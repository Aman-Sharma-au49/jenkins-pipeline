Deploying Minikube Using Jenkins

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXcyF6y6eSwJdAA3I8YCyE1XvGljPvbyIjVKhtp479VTbV8A9brL8awJhyoIYxyUh_9-v14gK5NH9G6l4eBpXSdcN6GkeHHRTtZ0a5bBVh7G8HWf7iPoydrmYIHduhF7GYWQQESlFA?key=hXxL76BvOSp_AT-WR8fwLgn1)

  
  
  
  
  
  
  
  
  
  

Made by [Aman Sharma](mailto:aman.x.sharma@fosteringlinux.com)

# Table of Content

  

[Table of Content 2](https://docs.google.com/document/d/1fiF9rObz0JoDqcLrRxVqElMHHXae62d7oSJHAAGZBtU/edit?tab=t.0#heading=h.o0wuxa6wblg)

[1\. ABOUT DOCUMENT 2](https://docs.google.com/document/d/1fiF9rObz0JoDqcLrRxVqElMHHXae62d7oSJHAAGZBtU/edit?tab=t.0#heading=h.9n4m3gegls89)

[1.1 Reviewer 2](https://docs.google.com/document/d/1fiF9rObz0JoDqcLrRxVqElMHHXae62d7oSJHAAGZBtU/edit?tab=t.0#heading=h.3odoyjz3qe4v)

[1.2 Audience 2](https://docs.google.com/document/d/1fiF9rObz0JoDqcLrRxVqElMHHXae62d7oSJHAAGZBtU/edit?tab=t.0#heading=h.kilqx1g8libb)

[3\. PREREQUISITES 3](https://docs.google.com/document/d/1fiF9rObz0JoDqcLrRxVqElMHHXae62d7oSJHAAGZBtU/edit?tab=t.0#heading=h.rafncxjmyewi)

[4\. Installation 4](https://docs.google.com/document/d/1fiF9rObz0JoDqcLrRxVqElMHHXae62d7oSJHAAGZBtU/edit?tab=t.0#heading=h.y2prnwvdc4rg)

[1\. Install Node.js and NPM 4](https://docs.google.com/document/d/1fiF9rObz0JoDqcLrRxVqElMHHXae62d7oSJHAAGZBtU/edit?tab=t.0#heading=h.abpqhhvv7wm0)

[2\. Docker Installation 4](https://docs.google.com/document/d/1fiF9rObz0JoDqcLrRxVqElMHHXae62d7oSJHAAGZBtU/edit?tab=t.0#heading=h.2ny7ickzk3w)

[3\. Kubectl Installation 6](https://docs.google.com/document/d/1fiF9rObz0JoDqcLrRxVqElMHHXae62d7oSJHAAGZBtU/edit?tab=t.0#heading=h.141bxj5an4yq)

[4\. Minikube Installation 6](https://docs.google.com/document/d/1fiF9rObz0JoDqcLrRxVqElMHHXae62d7oSJHAAGZBtU/edit?tab=t.0#heading=h.9g69jit0udbx)

[6\. Jenkins installation 7](https://docs.google.com/document/d/1fiF9rObz0JoDqcLrRxVqElMHHXae62d7oSJHAAGZBtU/edit?tab=t.0#heading=h.di0np9qwe8xe)

[5\. APPLICATION FILES 8](https://docs.google.com/document/d/1fiF9rObz0JoDqcLrRxVqElMHHXae62d7oSJHAAGZBtU/edit?tab=t.0#heading=h.dvlhluwjmqao)

[6\. JENKINS PIPELINE 10](https://docs.google.com/document/d/1fiF9rObz0JoDqcLrRxVqElMHHXae62d7oSJHAAGZBtU/edit?tab=t.0#heading=h.uxpmmsnp2g2s)

[7\. Workflow Summary 16](https://docs.google.com/document/d/1fiF9rObz0JoDqcLrRxVqElMHHXae62d7oSJHAAGZBtU/edit?tab=t.0#heading=h.aqxpy1khyqce)

[8\. Conclusion 17](https://docs.google.com/document/d/1fiF9rObz0JoDqcLrRxVqElMHHXae62d7oSJHAAGZBtU/edit?tab=t.0#heading=h.6m5j0stsbo13)

  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  

# 1\. About Document

This guide explains how to set up a Jenkins pipeline to deploy a Node.js application to a Kubernetes cluster using Minikube. The pipeline includes stages to initialize the Node.js project, build a Docker image, and deploy it to Kubernetes.

  

## 1.1 Reviewer

  

| Sr No | Name |
| --- | --- |
| 1 | Kunal Saini |

  
  
  

## 1.2 Audience

Before proceeding with the setup, ensure you have basic knowledge about following.

● Basic knowledge of Linux operating system administration.

● Access to a Linux environment where you can install and configure software.

● Knowledge of Docker and Minikube.

  

I am Using the Operating system is given below:-

  

| NAME="Ubuntu"VERSION="20.04.6 LTS (Focal Fossa)"ID=ubuntuID_LIKE=debianPRETTY_NAME="Ubuntu 20.04.6 LTS"VERSION_ID="20.04"HOME_URL="https://www.ubuntu.com/"SUPPORT_URL="https://help.ubuntu.com/"BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"VERSION_CODENAME=focalUBUNTU_CODENAME=focal |
| --- |

  

# 3\. Prerequisites

To set up the pipeline, you will need a few essential tools:

*   NPM: Manages JavaScript libraries and tools for Node.js.
    
*   Docker: Used to package applications into containers.
    
*   kubectl: A command-line tool for managing Kubernetes clusters.
    
*   Minikube: Provides a local Kubernetes environment for testing.
    
*   Jenkins Server: Automates building, testing, and deploying projects in CI/CD pipelines.
    
*   Kubeconfig File: Required for kubectl to connect and interact with the Kubernetes cluster.
    

  
  
  

# 4\. Installation

## 1\. Install Node.js and NPM

Update the Packages and Installation of nodejs and npm

| `$ sudo apt update$ sudo apt install nodejs npm` |
| --- |

Verify Node.js and NPM Installation

| $ node -v$ npm -v |
| --- |

  
  
  
  
  
  

## 2\. Docker Installation

Update Package List:

| $ sudo apt-get update |
| --- |

  

Install necessary packages for Docker installation

| $ sudo apt install -y apt-transport-https ca-certificates curl software-properties-common |
| --- |
  
Download and add Docker's official GPG key

| $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg  sudo gpg --dearmor -o/usr/share/keyrings/docker-archive-keyring.gpg |
| --- |

Install Docker engine

| $ sudo apt install -y docker-ce docker-ce-cli containerd.io |
| --- |

  

Start the Docker service and enable it to run at boot

| $ sudo systemctl start docker$ sudo systemctl enable docker |
| --- |

  
  

Verify Installation: After installation, verify that Docker has been installed correctly by checking its version:

| $ docker --version |
| --- |

  

These above steps should guide you through the process of installing Docker on Ubuntu.

  
  
  
  
  
  

## 3\. Kubectl Installation

Install Kubectl:

| $ sudo apt install kubectl --classic |
| --- |

  

Check version of kubectl:

| $ kubectl version --client |
| --- |

  
  
  
  

## 4\. Minikube Installation

Download Minikube:

| $ curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 |
| --- |

  
  

Install Minikube:

| $ sudo install minikube-linux-amd64 /usr/local/bin/minikube |
| --- |

  
  

Version of Minikube:

| $ minikube version |
| --- |

  

Add User

| $ sudo usermod -aG docker $USER |
| --- |

  

Add New Group

| $ newgrp docker |
| --- |

  

Start the minikube with Docker

| $ minikube start --driver=docker |
| --- |

  

Check the status of minikube

| $ minikube status |
| --- |

  
  
  
  
  
  
  
  
  
  
  
  
  

## 6\. Jenkins installation

Install Java (Jenkins requires Java):

| $ sudo apt install openjdk-17-jdk |
| --- |

  

Import the Jenkins key:

| sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key |
| --- |

  

Add Jenkins repository to your system:

| echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \  https://pkg.jenkins.io/debian-stable binary/  sudo tee \  /etc/apt/sources.list.d/jenkins.list > /dev/null |
| --- |

  

Update System Packages:

| $ sudo apt-get update |
| --- |

  

Install Jenkins:

| sudo apt-get install jenkins |
| --- |

  

Enable the Jenkins service

| $ sudo systemctl enable jenkins |
| --- |

  

Start the Jenkins service:

| $ sudo systemctl start jenkins |
| --- |

  
  

Status the Jenkins service:

| $ sudo systemctl status jenkins |
| --- |

  
  
  
  
  
  
  

Install the Plugin in Jenkins:

Navigate to Dashboard -> Manage Jenkins -> Plugin 

*   Github 
    
*   Docker
    
*   Kubernetes
    
*   Kubernetes CI
    

  
  

# 5\. Application Files

Directory Structure of the Application

| .├── app.js├── Dockerfile├── nodejs-pod.yaml├── package.json└── package-lock.json |
| --- |

  
  

5.1 app.js

| const express = require('express'); const app = express(); const port = 3000; // Define a route for the home pageapp.get('/', (req, res) => {  res.send('<h1>Welcome to my Node.js page!</h1>');});app.listen(port, () => {  console.log(`Server is running at http://localhost:${port}`);}); |
| --- |

  
  

5.2 Dockerfile

| # Use Node.js as the base imageFROM node:18-alpine# Set working directoryWORKDIR /usr/src/app# Copy package.json and install dependenciesCOPY package*.json ./RUN npm install# Copy application filesCOPY . .# Expose the port the app runs onEXPOSE 3000 |
| --- |

  

5.3 nodejs-pod.yaml

| apiVersion: v1kind: Podmetadata:  name: nodejs-pod  labels:app: nodejs-appspec:  containers:  - name: nodejs-appimage: nodejs-appimagePullPolicy: Neverports:- containerPort: 3000 |
| --- |

  
  

Create a Repository on github and upload the file is given below:-

*   Dockerfile
    
*   Nodejs-pod.yaml
    
*   app.js
    

  

Exports the Minikube cluster:

| $ minikube kubectl -- config view --flatten > kubeconfig.yaml |
| --- |

  

Then: 

| $ sudo cp kubeconfig.yaml /var/lib/jenkins/ |
| --- |

  
  
  
  
  
  
  
  
  
  
  
  
  
  
  

# 6\. Jenkins Pipeline

  

Pipeline Script

| pipeline {agent anyenvironment {     IMAGE_NAME = "nodejs-app"     POD_YAML = "nodejs-pod.yaml"     KUBECONFIG = "/var/lib/jenkins/workspace/jenkins-pipeline/kubeconfig"}stages {     stage('Setup Node.js Project') {         steps {             echo 'Initializing Node.js project...'             sh '''             # Ensure we are in the correct directory for npm initialization             if [ ! -f package.json ]; then                 echo "Initializing npm project..."                 npm init -y  # Create package.json                 npm install express  # Install Express.js             else                 echo "package.json already exists. Skipping initialization."             fi             '''         }     }     stage('Checkout Code') {         steps {             echo 'Checking out code...'             sh '''             # Initialize Git repository and pull the code             if [ ! -d .git ]; then                 echo "Initializing Git repository..."                 git init                 git remote add origin https://github.com/Aman-Sharma-au49/jenkins.git             fi             echo "Fetching and checking out code..."             git fetch origin             git checkout main             ls -l             '''         }     }     stage('Build Docker Image') {         steps {             echo 'Building Docker Image...'             sh '''             # Ensure package.json exists before building             if [ ! -f package.json ]; then                 echo "Error: package.json not found. Aborting Docker build."                 exit 1             fi             echo "Building Docker image..."             docker build -t ${IMAGE_NAME} .             '''         }     }     stage('Deploy to Kubernetes') {         steps {             echo 'Deploying to Kubernetes...'             withEnv(['KUBECONFIG=/var/lib/jenkins/workspace/jenkins-pipeline/kubeconfig']) {                 sh '''                 # Ensure kubectl authentication                 echo "Checking kubectl authentication..."                 kubectl auth can-i get pods --namespace default                 if [ $? -ne 0 ]; then                     echo "Error: kubectl authentication failed!"                     exit 1                 fi                 echo "Applying Kubernetes deployment..."                 kubectl apply -f "${POD_YAML}" --validate=false                 '''             }         }     }     stage('Verify Deployment') {         steps {             echo 'Verifying Deployment...'             withEnv(['KUBECONFIG=/var/lib/jenkins/workspace/jenkins-pipeline/kubeconfig']) {                 sh 'kubectl get pods -l app=nodejs-app'             }         }     }}post {     success {         echo 'Pipeline executed successfully!'     }     failure {         echo 'Pipeline failed. Check the logs for details.'     }}} |
| --- |

  
  
  

Output Sample:

  

| Started by user aman[Pipeline] Start of Pipeline[Pipeline] nodeRunning on Jenkins in /var/lib/jenkins/workspace/node-pipeline[Pipeline] {[Pipeline] withEnv[Pipeline] {[Pipeline] stage[Pipeline] { (Setup Node.js Project)[Pipeline] echoInitializing Node.js project...[Pipeline] sh+ [ ! -f package.json ]+ echo package.json already exists. Skipping initialization.package.json already exists. Skipping initialization.[Pipeline] }[Pipeline] // stage[Pipeline] stage[Pipeline] { (Checkout Code)[Pipeline] echoChecking out code...[Pipeline] sh+ [ ! -d .git ]+ echo Fetching and checking out code...Fetching and checking out code...+ git fetch origin+ git checkout mainAlready on 'main'Your branch is up to date with 'origin/main'.+ ls -ltotal 44-rw-r--r--  1 jenkins jenkins   381 Nov 25 12:50 app.js-rw-r--r--  1 jenkins jenkins   314 Nov 25 12:50 Dockerfile-rw-r--r--  1 jenkins jenkins   212 Nov 25 12:50 nodejs-pod.yamldrwxr-xr-x 66 jenkins jenkins  4096 Nov 25 12:50 node_modules-rw-r--r--  1 jenkins jenkins   277 Nov 25 12:50 package.json-rw-r--r--  1 jenkins jenkins 20830 Nov 25 12:50 package-lock.json[Pipeline] }[Pipeline] // stage[Pipeline] stage[Pipeline] { (Build Docker Image)[Pipeline] echoBuilding Docker Image...[Pipeline] sh+ [ ! -f package.json ]+ echo Building Docker image...Building Docker image...+ docker build -t nodejs-app .#0 building with "default" instance using docker driver#1 [internal] load build definition from Dockerfile#1 transferring dockerfile: 353B 0.0s done#1 DONE 0.0s#2 [internal] load metadata for docker.io/library/node:18-alpine#2 DONE 1.9s#3 [internal] load .dockerignore#3 transferring context: 2B done#3 DONE 0.0s#4 [1/5] FROM docker.io/library/node:18-alpine@sha256:7e43a2d633d91e8655a6c0f45d2ed987aa4930f0792f6d9dd3bffc7496e44882#4 DONE 0.0s#5 [internal] load build context#5 transferring context: 37.18kB 0.2s done#5 DONE 0.3s#6 [2/5] WORKDIR /usr/src/app#6 CACHED#7 [3/5] COPY package*.json ./#7 CACHED#8 [4/5] RUN npm install#8 CACHED#9 [5/5] COPY . .#9 DONE 0.7s#10 exporting to image#10 exporting layers#10 exporting layers 0.4s done#10 writing image sha256:28b92108c17b9c999f417887833bcbc9940f2a05439991de850b5d09fd3f0c7b done#10 naming to docker.io/library/nodejs-app done#10 DONE 0.5s[Pipeline] }[Pipeline] // stage[Pipeline] stage[Pipeline] { (Deploy to Kubernetes)[Pipeline] echoDeploying to Kubernetes...[Pipeline] withEnv[Pipeline] {[Pipeline] sh+ echo Checking kubectl authentication...Checking kubectl authentication...+ kubectl auth can-i get pods --namespace defaultyes+ [ 0 -ne 0 ]+ echo Applying Kubernetes deployment...Applying Kubernetes deployment...+ kubectl apply -f nodejs-pod.yaml --validate=falsepod/nodejs-pod created[Pipeline] }[Pipeline] // withEnv[Pipeline] }[Pipeline] // stage[Pipeline] stage[Pipeline] { (Verify Deployment)[Pipeline] echoVerifying Deployment...[Pipeline] withEnv[Pipeline] {[Pipeline] sh+ kubectl get pods -l app=nodejs-appNAME     READY   STATUS          RESTARTS   AGEnodejs-pod   0/1 ContainerCreating   0      2s[Pipeline] }[Pipeline] // withEnv[Pipeline] }[Pipeline] // stage[Pipeline] stage[Pipeline] { (Declarative: Post Actions)[Pipeline] echoPipeline executed successfully![Pipeline] }[Pipeline] // stage[Pipeline] }[Pipeline] // withEnv[Pipeline] }[Pipeline] // node[Pipeline] End of PipelineFinished: SUCCESS |
| --- |

  
  
  
  
  
  
  
  
  
  
  
  

# 7\. Workflow Summary

Node.js Setup:

     Ensure the project is initialized and dependencies are installed.

Code Checkout:

     Clone or fetch the latest application code from the Git repository.

Docker Image Build:

     Use the Dockerfile to create a container image of the Node.js application.

Kubernetes Deployment:

     Apply the deployment YAML to the Minikube cluster.

Deployment Verification:

     Check if the application pods are running successfully.

  

# 8\. Conclusion

  

This pipeline demonstrates a simple yet powerful workflow to automate the deployment of a Node.js application to Minikube using Jenkins. By following this documentation, you can adapt the pipeline for other applications and clusters as needed.
