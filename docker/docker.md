# Docker documentation based on "Docker for the Absolute Beginer" course by Mumshad Mannambeth

**Why we need Docker?**

- With docker we can run each component (such as a Web Server, DataBase, etc) in a different container with its own dependencies and libraries.interfaces. And all on the same machine. 

**Container**

 - A container is separate environment with its own processes, services and network.

**Docker Image**

- Is a package or a template. Containers run instances of an image which are isolated and have their own environment and processes. We can search for Docker's images from https://hub.docker.com/search


## Basic Docker Commands

```
# Run instance of the app
docker run application
```

```
# Run instance of the app backround
docker run -d application
```

```
# List running containers
docker ps
```

```
# List all containers
docker ps -a
```

```
# Stop a container; can be CONTAINER ID too
docker stop name
```

```
# Delete a container; can be CONTAINER ID too
docker rm name
```

```
# Delete an image
docker rmi name
```

```
# List download images
docker images
```

```
# Only download an image
docker pull image
```

```
# Containder details in JSON format
docker inspect name
```

### Example

```
# Centos with CLI (i for interactive mode, t terminal/prompt)
docker run -it centos bash
```

## Volume mapping
When the container is deleted, its data is deleted too. To avoid this, we can make data persistent mapping it to a directory outside the container.
For example, to run an instance of mysql with persisten data, we can do this:
```
docker run -v /home/matimercado/desktop/docker:/var/lib/mysql mysql
```
 where /var/lib/mysql is a folder inside the docker container
