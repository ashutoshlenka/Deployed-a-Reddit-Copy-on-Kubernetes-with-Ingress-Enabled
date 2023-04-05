# Deployed-a-Reddit-Copy-on-Kubernetes-with-Ingress-Enabled

For this project 1st u have to create two ec2 instances. Let's assume the first instance name is CI server and the senond one is Deployment server. And remember one thing while creating the second server here you should use t2.medium instance type bcz on that server we have to install minikube. 

On that 1st server we need to install DOCKER by using this commands

sudo apt-get update

sudo apt-get install docker.io -y

sudo usermod -aG docker $USER && newgrp docker


Step 1: Clone the source code)

git clone https://github.com/LondheShubham153/reddit-clone-k8s-ingress.git

Step 2: Containerize the Application using Docker

FROM node:19-alpine3.15

WORKDIR /reddit-clone

COPY . /reddit-clone

RUN npm install 

EXPOSE 3000

CMD ["npm","run","dev"]

Step 3: Build the Docker-Image

docker build -t ashutosh1999/reddit-clone

Step 4: Push the Image To DockerHub
1st login to your DockerHub account using Command 

docker login and give your username & password

docker push ashutosh1999/reddit-clone

Then connect to the deployment server. Here we need to install docker by the previous docker commands and install minikube by this commands

curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

sudo install minikube-linux-amd64 /usr/local/bin/minikube 

sudo snap install kubectl --classic

minikube start --driver=docker

Write a Deployment.yml and a Service.yml file

then  Deploy both the manifect file into Kubernetes by the following command

kubectl apply -f Deployment.yml

kubectl apply -f Service.yml

