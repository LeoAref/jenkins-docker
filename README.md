# Jenkins-Docker [![Packagist](https://img.shields.io/packagist/l/doctrine/orm.svg?maxAge=2592000?style=flat-square)](https://github.com/LeoAref/jenkins-docker/blob/master/LICENSE.txt)

An image for running Docker command in Jenkins, it's not *docker-in-docker*, but instead it enables exposing Docker socket to the Jenkins container

### First steps

```bash
docker pull leoaref/jenkins-docker
docker run -d -v /var/run/docker.sock:/var/run/docker.sock -p 8080:8080 --name jenkins-docker leoaref/jenkins-docker
```

This will pull the image locally, and run a container with mounted docker socket

### Working example

ssh into the running container *jenkins-docker*
```bash
docker run -d -v /var/run/docker.sock:/var/run/docker.sock -p 8080:8080 --name jenkins-docker leoaref/jenkins-docker
docker exec -it jenkins-docker bash
```

Run test command inside the container
```bash
sudo docker ps
```

It should output something similar to:
```bash
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                               NAMES
f344dc9c58dd        f79b24adaa64        "/bin/tini -- /usr..."   4 hours ago         Up 4 hours          0.0.0.0:8080->8080/tcp, 50000/tcp   jenkins-docker
```