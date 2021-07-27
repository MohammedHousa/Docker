# ---Docker Setup---
#Install Docker: 	
yum install docker -y
#Enable Docker:		
systemctl enable docker
#Start Docker:		
systemctl start docker
# Check Docker service:		
systemctl status docker
# Add user to group
sudo usermod -a -G docker ec2-user
# Check Docker Version: 	
docker version
# Check Docker Info:			
docker info
# Login to DockerHub:	
docker login
# Logout of DockerHub:	
docker logout


# ---Docker Images---
# List images:		
docker images
# Pull an image from DockerHub: 			
docker pull <img>
# Rename an image:			
docker image tag <img> <new-name>
# Push an images to DockerHub:			
docker push <img name>
# Remove an image:			
docker rmi <img>
# Remove unused images:		
docker image prune -a
# Remove all images
docker rmi $(docker images -q)


# ---Dockre Container---
# List continers:	
docker ps -a
# Create a container form an image
docker run -it -d --name <container> <img>
# Rename cont:		
docker rename <container> <new name>
# Stop cont:			
docker stop <container>
# Start cont:			
docker start <continer>
# Restart cont:		
docker restart <container>
# Execute cont:		
docker exec -it <container> bash
# Create an image from a container
docker commit <container> <new-img-name>
# Remove cont:		
docker rm <container>
# Removes all stopped cont:	
docker container prune
# kill all running containers
docker kill $(docker ps -q)


# ---Dockre File---
# Build an image:			
docker build -t <img-name:v1> .




















