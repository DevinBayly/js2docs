# Containers on Jetstream2

Containers are isolated environments in which to run your applications. They created by objects called images. An image is defined as a read only template with instructions for creating a container. These instructions define everything a container needs; Software, dependencies, system libraries, environment variables, configuration files, etc.

Jetstream2 supports Docker and Singularity. Other container software may be included in the future.

[Jetstream Featured Images](featured.md) all include Docker as part of the build. Additionally, the NVIDIA Docker2 container environment is also built in so that all Featured images may be used for GPU usage or using NVIDIA containers for code development.

Singularity is installed as part of the [Jetstream Software Collection](software.md).

## Some basic Docker commands:

`docker -version`  - will give the version of Docker is installed.
`docker pull <image_name>` - will download the image from dockerhub.
`docker run  <image_name>` - will run the image pulled from dockerhub to create a container.
    If you don’t have a local copy of the image, the `run` command will pull and then run the image to create a container.
`docker ps` - Process status of containers. If no container is running, you get a blank line.
`docker ps -a` - process status of all containers.
`docker exec -it <container_id> bash` - allows you to run a command in the docker container.
    The `-it` flag provides an interactive tty (shell) within the container.
`docker stop <container_id>` - shuts down a computer.
`docker build <path_to_docker_file>` - Builds an image from the specified docker file.
`docker push <docker_hub_username/image_name>` - pushes an image to the docker hub repository.
