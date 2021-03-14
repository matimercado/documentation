# Docker documentation based on "Docker for the Absolute Beginer" course by Mumshad Mannambeth

**Why we need Docker?**

- With docker we can run each component (such as a Web Server, DataBase, etc) in a different container with its own dependencies and libraries.interfaces. And all on the same machine. 

**Container**

 - A container is separate environment with its own processes, services and network.

**Docker Image**

- Is a package or a template. Containers run instances of an image which are isolated and have their own environment and processes. We can search for Docker's images from https://hub.docker.com/search


## Basic Docker Commands

```
# Run instance of an app
docker run application

# Run instance of an app and give it a name
docker run --name myappname application
```

```
# Run instance of an app backround
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
When the container is deleted, its data is deleted too. To avoid this, we can make data persistent mapping it to a directory outside the container.\
For example, to run an instance of mysql with persisten data, we can do this:
```
docker run -v /home/matimercado/desktop/docker:/var/lib/mysql mysql
```
 where /var/lib/mysql is a folder inside the docker container


## Hands on with Jenkins
For more information check https://hub.docker.com/_/jenkins

Jenkins is a Continuous Integration and Delivery server. We can access it in two ways: 
- Using the internal IP of the container
- By mapping a port to the docker host and accessing it using the external IP

To run it with docker using container IP:
```
docker run jenkins/jenkins
```
This will pull and run the last image.\
Now we have to know the IPAdress of the container to run it localy. To do this, we can use this command line.
```
docker inspect containername | grep IP
```
![docker_grep_IP](/docker/images/docker_inspect_containername_grep_IP.png)

In this case, we have to insert **172.17.0.2:8080** in our web browser, and paste the pass give by the container.

To run it maaping a port to the docker host:
```
docker run -p 8081:8080 jenkins/jenkins
```

And insert in the web browser the IP and port of our docker host, for example **192.168.1.162:8081**, and paste the pass give by the container.

If we configure the jenkins server and then we stop the container, configuration will we lost. To avoid this, we can make a persistent volume to store our settings:
```
docker run -p 8081:8080 -v /home/matimercado/Desktop/docker/jenkins_data:/var/jenkins_home jenkins:jenkins
```
where /var/jenkins_home is where the container stores the data

## Docker images