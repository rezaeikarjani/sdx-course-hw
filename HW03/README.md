# Instructions for HW03

In this assignment you will deploy mosquitto broker to Rahti cloud.

**Assignment**

1. Fill in the [mosquitto.yaml](./mosquitto.yaml) file with the following Object Definitions:

   - Object definition for mosquitto broker (use deployment or deploymentConfig, not pod!)
   - Service
   - ConfigMap for mosquitto.conf
   - ConfigMap or Secret for server.crt, ca.cart and server.key (MQTT certificates)
   - Route

- Use the official eclipse-mosquitto:latest image.
- Use only one replica.
- Configure mosquitto broker with correct configuration - encrypted unauthenticated access. Broker needs to allow anonymous access.
- Use ports 1883 and 8883! Use both!
- Use ca.crt, server.crt and server.key in [HW02/certs/](../HW02/certs/) directory for enabling encrypted access.
- In Route object specification use `tls.termination: passthrough`. You need to figure out how to choose a custom URL for your route via Rahti documentation.
- USE ONLY CHARACTERS a-z AND minus sign ( - ) IN SERVICE NAMES!

2. Use `oc create` command to create the objects defined in your [mosquitto.yaml](./mosquitto.yaml) file in Rahti cloud

   - Inspect your deployment with "oc get all".

3. Test connection to your MQTT broker in Rahti cloud

- Use image from exercise 1 to run an MQTT publisher on your own machine.
- Check that messages are received by subscribing to your rahti mqtt server (use mosquitto_sub)

Hint: Use MQTT_URL and MQTT_PORT in the docker run command

Hint: If you get the "do handshake" error: your certs are mounted wrong, they are not in the filepath they need to be or actual filepath and the ones in mosquitto.conf do not match

**Note:** You don't need to modify the previous toyota-data-feeder image in any way!

## Deliverables

1. [mosquitto.yaml](./mosquitto.yaml) file

## Provide RAHTI_TOKEN {#rahti-token}

In order for the tests to check your assignment, a variable named `RAHTI_TOKEN` should be configured by you. Follow the below instructions:

1. Go to [rahti.csc.fi/](https://rahti.csc.fi/) and log in
2. Once logged in, click on your name on the top right corner, click on `copy login command`
3. Log in again in this new window
4. Once logged in, click `display token`
5. Copy the whole token that starts with sha256~ under `Your API token is`
6. Go to [gitlab.com/](https://gitlab.com/) and find your project for this course
7. Once you found the correct project, click on the top left icon to see the menu
8. In the menu, click on `settings -> CI/CD`
9. Click on the `expand` button on the `variables` section
10. Click on `add variable` button
11. Choose the `Masked` visibility
12. Unmark `Protect variable` and `Expand variable reference`
13. In the `Key` section, enter `RAHTI_TOKEN`
14. In the `value` section, paste the token you copied from Rahti
15. Click on `Add variable` button

**NOTE:** This token is only valid for 1 day. Next time you want to deliver your assignment, you need to update this `RAHTI_TOKEN` variable with new token information.

Run the following in the HW03 directory to deliver the assignment:

```shell
   git commit -am "HW03"
   git push
```

### Helpful Section

You might find this section helpful.

```shell
oc –help

oc create -f <your>.yaml

oc status

oc replace –force -f <your>.yaml

oc delete –all service (OR route OR configmap OR deployment OR etc..)

oc get pods (OR routes OR deployments OR etc..)

docker run --rm -it --name toyota-data-feeder -e MQTT_URL=??? -e MQTT_PORT=???? -e CLIENT_ID=<student_id> toyota-data-feeder:0.1


mosquitto_sub -t '<student_id>/#' --cafile ca.crt --insecure --host ??? --port ??? -v
```

Some useful links:

- [Pods and services](https://docs.openshift.com/dedicated/3/architecture/core_concepts/pods_and_services.html)
- [Deployments](https://docs.openshift.com/container-platform/4.16/applications/deployments/what-deployments-are.html)
- [Volumes](https://docs.openshift.com/container-platform/3.11/dev_guide/volumes.html)
- [ConfigMaps](https://docs.openshift.com/container-platform/3.11/dev_guide/configmaps.html)
- [Routes](https://docs.csc.fi/cloud/rahti2/networking/#routes)
