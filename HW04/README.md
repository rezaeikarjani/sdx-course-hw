# Instructions for HW04

In this HW, you will build docker images of two kuksa-feeders f1demo2val and val2mqtt. Moreover, you will fill in the [docker compose file](./docker-compose.yml) which has three services kuksa.val,f1demo2val and val2mqtt. Then, you will use the MQTT broker you set up earlier in HW03.

Kuksa.val is a server which translates incoming and outcoming car data as [COVESA VSS data](https://covesa.github.io/vehicle_signal_specification/).

In this exercise you should have the following connection flow happening in your [docker compose file](./docker-compose.yml):

- [f1demo2val](https://github.com/smaddis/f1demo2val) feeds data to kuksa.val server
- [kuksa.val](https://github.com/eclipse/kuksa.val) server receives data
- [val2mqtt](https://github.com/smaddis/val2mqtt) listens to the data kuksa.val server receives and publishes this data as MQTT message to the MQTT broker

**Assignment**

- Fill in required instructions for [f1demo2val](./f1demo2val.dockerfile) and [val2mqtt](./val2mqtt.dockerfile) applications in their respective Dockerfiles, then build and push the images to a registry of your own choice
- Fill in the [docker-compose.yml](./docker-compose.yml) file to have three services kuksa.val,f1demo2val and val2mqtt
  - For kuksa.val use this image `ghcr.io/smaddis/kuksa-val:0.2.0`
  - For f1demo2val and val2mqtt use the image you pushed to the registry
- Configure f1demo2val and val2mqtt to use kuksa.val server
  - Figure out which port to use for kuksa.val
  - Use the mosquitto broker you have already deployed in HW03
  - For TOPIC_PREFIX use your student account name
- Run `docker compose up`
- Check you are receiving messages from your MQTT broker in Rahti with mosquitto_sub

## Deliverables

- [docker-compose.yml](./docker-compose.yml) file
- [f1demo2val.dockerfile](./f1demo2val.dockerfile) and required files ([f1demo2val-files/](./f1demo2val-files/))
- [val2mqtt.dockerfile](./val2mqtt.dockerfile) and required files ([val2mqtt-files/](./val2mqtt-files/))

## Provide RAHTI_TOKEN

Check the [Provide RAHTI_TOKEN](../HW03/README.md#provide-rahti_token) section in HW03 before pushing the assignment files.

Run the following in the HW04 directory to deliver the assignment:

```shell
   git add f1demo2val-files/ val2mqtt-files/
   git commit -am "HW04"
   git push
```
