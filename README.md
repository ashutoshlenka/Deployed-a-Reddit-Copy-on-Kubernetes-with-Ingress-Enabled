# Deployed-a-Reddit-Copy-on-Kubernetes-with-Ingress-Enabled
projects

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
