# Assignment 3

# Build the images for Microservices (remember to edit code for frontend) and push images to Dockerhub and write commands to run backedn & frontend and they should run fine
  - `https://hub.docker.com/repository/docker/sannan1357/backend`
  - `https://hub.docker.com/repository/docker/sannan1357/frontend`
# How to leverage cache using Dockerfiles
  - Layers that change more frequently (like copying code) should be placed at last

# What are multi-stage builds
  In multi-stage builds we use nested images in which the final image only consists of build artifacts\exe of application which is enough to run application. Multi-stage build are use to reduce image sizes.
  With multi-stage builds, you use multiple FROM statements in your Dockerfile. Each FROM instruction can use a different base, and each of them begins a new stage of the build. You can selectively copy artifacts from one stage to another, leaving behind everything you don't want in the final image reducing image size.


# Explain containers vs Image
  Image is made from dockerfile which consists of layers whereas, containers are running instance of an image

# Explain RUN vs CMD vs Entrypoint

  - RUN: is used to install additional packages and creates a new layer on top of an image. 
  - CMD: Is the default command which is passed to entrypoint as a parameter.
  - Entrypoint: The ENTRYPOINT specifies a command that will always be executed when the container starts.

# Improve the Dockerfile for python Application given in slides using the Dockerfile & then improve it and share image size & estimated build time for it
    FROM python:3.6-alpine
    COPY . /
    RUN pip3 install --upgrade pip 
    CMD ["python3" ,"app.py"]


   Bad-Practise image took: 172.5 s
   Good-practise image took: 5.4 s

# Run mysql container using the official image, by persisting data and passing environment variables to set username & passwordâ€¦ You can see the information of how to persist and information here
  `docker run --name mysql-container -v /Users/sannan/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=my-seceret -d mysql`

https://hub.docker.com/_/mysql
