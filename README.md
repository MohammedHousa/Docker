# Docker
Docker is a set of platform as a service products that use OS-level virtualization to deliver software in packages called containers. Containers are isolated from one another and bundle their own software, libraries and configuration files; they can communicate with each other through well-defined channels.

GitHub Repo: https://github.com/MohammedHousa/Docker

YouTube Playlist: https://www.youtube.com/playlist?list=PLUy8DvyX4nDHS1GyzRwN8OhbC0JoJwqPA

Topics:
1. [How to Install Docker on Linux](https://github.com/MohammedHousa/Docker/blob/main/README.md#install-docker) 
2. [How to work with Docker Images](https://github.com/MohammedHousa/Docker/blob/main/README.md#docker-images) 
3. [How to work with Docker Containers](https://github.com/MohammedHousa/Docker/blob/main/README.md#docker-containers) 
4. [How to work with Docker Storage](https://github.com/MohammedHousa/Docker/blob/main/README.md#docker-storage) 
6. [How to work with Docker File](https://github.com/MohammedHousa/Docker/blob/main/README.md#docker-file) 
7. [How to work with Docker Swarm](https://github.com/MohammedHousa/Docker/blob/main/README.md#docker-swarm) 



# Install Docker
| Purpose | Command |
| --- | --- |
| Install Docker | ```yum install docker -y``` |
| Enable Docker Service | ```systemctl enable docker``` |
| Start Docker Service | ```systemctl start docker``` |
| Check Docker service | ```systemctl status docker``` |
| Add user to group | ```usermod -a -G docker ec2-user``` |
| Check Docker Version | ```docker version``` |
| Check Docker Info | ```docker info``` |
| Login to DockerHub | ```docker login```|
| Logout of DockerHub| ```docker logout```|



# Docker Images
| Purpose | Command |
| --- | --- |
| List images | ```docker images``` |
| Pull image from DockerHub | ```docker pull <img>``` |
| Rename image | ```docker image tag <img> <new-name>``` |
| Push images to DockerHub | ```docker push <img name>``` |
| Remove image | ```docker rmi <img>``` |
| Remove unused images | ```docker image prune -a``` |
| Remove all images | ```docker rmi $(docker images -q)```|



# Docker Containers
Containers are isolated execution environments.
| Purpose | Command |
| --- | --- |
| List continers | ```docker ps -a``` |
| Create a container form an image | ```docker run -it -d -p 8080:80 --name service1 httpd``` |
| Rename container | ```docker rename <container> <new name>``` |
| Stop container | ```docker stop <container>``` |
| Start container | ```docker start <continer>``` |
| Restart container | ```docker restart <container>``` |
| Create a container with a link | ```docker run -it -d --name service2 --link service1 ubuntu``` |
| Execute container | ```docker exec -it <container> bash``` |
| Create an image from a container | ```docker commit <container> <new-img-name>``` |
| Remove container | ```docker rm <container>``` |
| Removes all stopped containers | ```docker container prune``` |
| kill all running containers | ```docker kill $(docker ps -q)``` |



# Docker Storage
Docker has two options for containers to store files in the host machine, so that the files are persisted even after the container stops: volumes, and bind mounts.
| Purpose | Command |
| --- | --- |
| Create a volume | ```docker volume create <vol name>``` |
| List volumes | ```docker volume ls``` |
| Inspect a volume | ```docker volume inspect <vol name>``` |
| Remove a volume | ```docker volume rm <vol name>``` |
| Start a container with a new volume | ```docker run -d --name service1 --mount source=vol1,target=/app nginx``` |
| Start a container with an existing volume | ```docker run -it -d --name service2 -v /home/ec2-user/storage:/testfile ubuntu``` |
| Remove unused volumes| ```docker volume prune```|



# Docker File
#### Create a dockerfile ```vim dockerfile```
```
FROM ubuntu
ARG DEBIAN_FRONTEND=noninteractive
RUN apt update -y
RUN apt install -y apache2
ADD . /var/www/html
ENTRYPOINT apachectl -D FOREGROUND
ENV name DevOps 
```
  
#### Create an index.html file ```vim index.html```
```
<html>
<title> Hello from CodingDojo </title>
<body> Hello world! </body>
</html>
```

| Purpose | Command |
| --- | --- |
| Build an image from dockerfile| ```docker build -t dockerfile . ``` |
| Create a container form the image | ```docker run -d -p 8080:80 dockerfile``` |

#### To access the container ```http://publicIP:8080```



# Docker Swarm
Docker swarm is a container orchestration tool, meaning that it allows the user to manage multiple containers deployed across multiple host machines. One of the key benefits associated with the operation of a docker swarm is the high level of availability offered for applications.
| Purpose | Command |
| --- | --- |
| Initialize a swarm | ```docker swarm init``` |
| Join a node to a swarm | ```docker swarm join --token <token> HOST:PORT``` |
| Leaves the swarm | ```docker swarm leave --force``` |
| List nodes in the swarm | ```dokcer node ls``` |
| Promote node to manager | ```docker node promote <node>``` |
| Demote node from manager | ```docker node demote <node>``` |
| Creates a service | ```docker service create alpine ping 8.8.8.8``` |
| List services| ```docker service ls``` |
| Lists the tasks that are running | ```docker service ps <service name>``` |
| Updates a service | ```docker service update <service ID> --replicas 3``` |

