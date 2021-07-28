# Docker
Docker is a set of platform as a service products that use OS-level virtualization to deliver software in packages called containers. Containers are isolated from one another and bundle their own software, libraries and configuration files; they can communicate with each other through well-defined channels.

GitHub Repo: 

Tutorials:
1. How to Install Docker on Linux
2. How to work with Docker Images
3. How to work with Docker Containers
4. How to work with Docker Storage
5. How to work with Docker Network
6. How to work with Docker File
7. How to work with Docker Compose
8. How to work wiht Docker Swarm


## ---Install Docker---

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



## ---Docker Images---
| Purpose | Command |
| --- | --- |
| List images | ```docker images``` |
| Pull image from DockerHub | ```docker pull <img>``` |
| Rename image | ```docker image tag <img> <new-name>``` |
| Push images to DockerHub | ```docker push <img name>``` |
| Remove image | ```docker rmi <img>``` |
| Remove unused images | ```docker image prune -a``` |
| Remove all images | ```docker rmi $(docker images -q)```|


## ---Dockre Container---
| Purpose | Command |
| --- | --- |
| List continers | ```docker ps -a``` |
| Create a container form an image | ```docker run -it -d --name <container> <img>``` |
| Rename container | ```docker rename <container> <new name>``` |
| Stop container | ```docker stop <container>``` |
| Start container | ```docker start <continer>``` |
| Restart container | ```docker restart <container>``` |
| Execute container | ```docker exec -it <container> bash``` |
| Create a container with a link | ```docker run -it -d --name <container> --link <name or id> <img>``` |
| Create an image from a container | ```docker commit <container> <new-img-name>``` |
| Remove container | ```docker rm <container>``` |
| Removes all stopped containers | ```docker container prune``` |
| kill all running containers | ```docker kill $(docker ps -q)``` |


## ---Dockre Volumes---
| Purpose | Command |
| --- | --- |
| Create a volume | docker volume create <vol name> |
| List volumes | docker volume ls |
| Inspect a volume | docker volume inspect <vol name> |
| Remove a volume | docker volume rm <vol name> |
| Start a container with a new volume | docker run -d --name devtest --mount source=myvol2,target=/app nginx:latest |
| Start a container with an existing volume | docker run -d --name devtest -v /home/ec2-user/storage:/mount ubuntu |
| Remove unused volumes| docker volume prune|

## ---Dockre File---
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
| Create a container form the image | docker run -d -p 8080:80 demodockerfile |

#### To access the container ```http://publicIP:8080```




















