# Deployed-a-Reddit-Copy-on-Kubernetes-with-Ingress-Enabled
projects

For this project 1st u have to create two ec2 instances. Let's assume the first instance name is CI server and the senond one is Deployment server. And remember one thing while creating the second server here you should use t2.medium instance type bcz on that server we have to install minikube. 

On that 1st server we need to install DOCKER by using this commands
[ sudo apt-get update
sudo apt-get install docker.io -y
sudo usermod -aG docker $USER && newgrp docker]

1st step (clone the git repo)
git clone https://github.com/LondheShubham153/reddit-clone-k8s-ingress.git

create a Dockerfile 

FROM node:19-alpine3.15
WORKDIR /reddit-clone
COPY . /reddit-clone
RUN npm install 
EXPOSE 3000
CMD ["npm","run","dev"]

Building Docker-Image

apiVersion: apps/v1
kind: Deployment
