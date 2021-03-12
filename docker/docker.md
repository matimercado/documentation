# Docker documentation based on "Docker for the Absolute Beginer" course by Mumshad Mannambeth

**Why we need Docker?**

- With docker we can run each component (such as a Web Server, DataBase, etc) in a different container with its own dependencies and libraries.interfaces. And all on the same machine. 

**Container**

 - A container is separate environment with its own processes, services and network 

**Docker Image**

- Is a package or a template. Containers run instances of an image which are isolated and have their own environment and processes

## Basic Docker Commands

```
# Run instance of the app
docker run application
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
# Stop a container; can use ID too
docker stop name
```

```
# Delete a container; can user ID too
docker rm name
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
# Delete an image
docker rmi name
```