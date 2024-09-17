# Instructions for HW01

In this exercise, you will get to know how to build a Docker image with [Dockerfile](https://docs.docker.com/reference/dockerfile/), how to push it to the registry, and run it. You will also learn how to interact with the running container.

**Prerequisities:**

- Git
- Docker
- mosquitto_sub (cli tool)
- [Rahti](https://rahtiapp.fi/) project

**Assignment**
Your goal is to dockerize our Toyota data feeder application which playbacks
actual car data in real-time and then sends it to an MQTT server. You need to
create Dockerfile which runs the feeder.py file when the container is started
with correct environment variables. The application uses MQTT_URL, MQTT_PORT
and CLIENT_ID environment variables. This image is then pushed to a registry (CSC Rahti
Container registry or Dockerhub). You also need to test that you receive the
messages by subscribing to the MQTT server with mosquitto_sub tool.

Things to be done:

1. Check the [toyota-data-feeder repository](https://github.com/smaddis/toyota-data-feeder) repository.
2. Fill in the [Dockerfile](./Dockerfile) that executes feeder.py on container
   startup. Only include files that are actually needed for the application to run
   For example, be sure to not include /assets folder in your image.
3. Build the image and push it to the registry. You can use either DockerHub or
   CSC Rahti registry. If you are using CSC Rahti registry, be sure to assign
   TAs to your project and to change image pull policy to Anonymous. Tag the
   image with 1.0 version.
4. Run the image with correct MQTT_URL, MQTT_PORT and CLIENT_ID values. Don't hardcode these values!
5. Use mosquitto_sub to confirm you are receiving messages from your Docker container
   Use flags --verbose --insecure and --cafile ca.crt. ca.crt is available at HW02/certs of this repo.

**Other information**
For environment variables use these values:

- mqtt server url: mqtt-test.2.rahtiapp.fi
- mqtt port: 443
- client id: Use your CSC Rahti account name (eg. student067)

You can subscribe to every topic value under toyota topic with <client-id>/# when using mosquitto_sub command.

_Hint_: Run the image for testing the connection before tagging and pushing it to the registry.

## Deliverables

The following is the list of requirements for this homework assignment to be delivered by the deadline:

1. The [Dockerfile](./Dockerfile)
2. Provide a link ([video-demonstration file](video-demonstration.url)) to a recorded short video (about 2 minutes) with the following conditions:

   - Have your mic and camera on while screen recording your desktop
   - Introduce yourself by stating your full name
   - Explain each line of the code in the Dockerfile, and the reason that you have included such a line in the Dockerfile
   - Run the commands step by step, and show that the whole implementation of the assignment is working as illustrated in this exercise
   - You could use your office365 (or any other online place like YouTube etc.) for storing the recorded video and share its link in here

3. Run the following in the HW01 directory to deliver the assignment:

```shell
   git commit -am "HW01"
   git push
```

### Helpful section

The following is some instructions you may find helpful for this assignment.

#### Dockerfile Basic Commands

- FROM – Defines the base image to use and start the build process.
- RUN – It takes the command and its arguments to run it from the image (runs within
  the container at build time).
- VOLUME – Specifying it in the Dockerfile allows it to be externally mounted via the
  host itself or a Docker data container.
- CMD – Similar function as a RUN command, but it gets executed only after the
  container is instantiated.
- ENTRYPOINT – It targets your default application in the image when the container
  is created.
- ADD – It copies the files from source to destination (inside the container).
- ENV – Sets environment variables.
- COPY – Copy a file

#### Dockerfile example

```text
# Hey I’m a comment!

#Takes alpine:3.14 as base image
FROM alpine:3.14

#Copies from <src-path> <destination-path>
COPY . .

# echoes Hello at build time
RUN echo “Hello!”

CMD ["/usr/bin/echo", “Hello!”]
```

#### Building an image

- Once our Dockerfile is done we have to build it
- This is done by using docker cli-tool, with `docker build` command
- Let's build our cowsay application
  - `docker build -f .\Dockerfile -t cowsay-app:1.0 .`
  - `-f` specifies which Dockerfile to use. `-t` flag is used for tagging image with tag cowsay-app:1.0
  - Note the dot at the end command. This marks path where files are copied from to image
- After we have used above command lets see what we’ve got with docker images command
- `docker images` lists all the images your system has built or pulled from registry
