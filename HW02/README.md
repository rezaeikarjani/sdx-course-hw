# Instructions for HW02

In this assignment you will get to create a docker compose file which starts your previously built toyota-data-feeder Docker image and Eclipse Mosquitto MQTT broker. Consider this exercise as a "testing phase" for building your MQTT broker, because in exercise 3 you will deploy this same mosquitto server to the cloud.

**Assignment**

- Create a Docker compose file which defines two services - toyota-data-feeder application and mosquitto broker
  - For toyota-data-feeder use the image you created in HW01
  - Use the [official eclipse-mosquitto image](https://hub.docker.com/_/eclipse-mosquitto/)
  - USE ONLY CHARACTERS a-z AND minus sign ( - ) IN SERVICE NAMES
- Configure mosquitto broker with correct configuration - encrypted unauthenticated access
  - Broker should allow for anonymous access
  - Use ports 1883 and 8883. Note that these are two different ports. Map both!
  - Use ca.crt, server.crt and server.key for enabling encrypted access ([certs/ directory](./certs/))
- Connect toyota-data-feeder to use mosquitto broker in the docker compose file. Don't use mqtt-test.2.rahtiapp.fi
- Run docker compose to start up the services
- Confirm you are receiving messages to your localhost with mosquitto_sub

## Deliverables

The following files are needed for this assignment:

- [docker-compose.yml](./docker-compose.yml)
- [mosquitto.conf](./mosquitto.conf)

- Run the following in the HW02 directory to deliver the assignment:

```shell
   git commit -am "HW02"
   git push
```

### Other information

- You don't need to modify previous toyota-data-feeder image in anyway
- You are creating your own local MQTT broker/server in this exercise, so no need to connect to the MQTT broker we set up.
- Use MQTT certificates files in the [certs/](./certs/) directory
- See below links how to configure mosquitto Docker image with mosquitto configuration options:
  - [Mosquitto configuration documentation](http://mosquitto.org/man/mosquitto-conf-5.html)
  - [Mosquitto docker image documentation](https://github.com/eclipse/mosquitto/blob/master/docker/2.0/README.md)
  - [Docker compose documentation](https://docs.docker.com/compose/)
