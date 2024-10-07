# Cloud Native Resource Monitoring application (CNRM) using Kubernates

## Overview

This is a cloud-native resource monitoring application built with Python using Flask and psutil. It displays the resource usage of the machine it is running on locally, containerization with Docker helps with using it on any cloud resource. AWS Elastic Container Registry (ECR) is created using a python script and deployed on an Amazon Elastic Kubernetes Service (EKS) cluster.
### Features
-  Resource Monitoring: Real-time monitoring of CPU and memory utilization.
-  Dockerization: Containerize the application for easy deployment and scalability.
-  AWS Integration: Utilize AWS services such as ECR and EKS for hosting and managing the application.
-  Kubernetes Deployment: Create Kubernetes deployments and services using Python.
## Part 1:  Run Locally

You can run the project locally to check if it works.

- Clone the project

```bash
  git clone https://github.com/cliffsandroses/cloud-native-monitoring.git
```

- Go to the project directory

```bash
  cd cloud-native-monitoring
```

- Install dependencies

```bash
  pip3 install -r requirements.txt
```

- Start the application

```bash
  python3 app.py
```

### To run the project

#### On Linux

```bash
xdg-open "http://localhost:5000/"
```

#### On macOS

```bash
open  "http://localhost:5000/"
```

#### On Windows

```bash
start "http://localhost:5000/"
```
### OR

Access the application at http://localhost:5000/ in your web browser.


## Part 2: Dockerize the application

- Build the Docker image

```bash
docker build -t my-app .
```

- Run the newly built Docker container

```bash
docker run -p 5000:5000 my-app
```

- Access the application at http://localhost:5000/ in your web browser.

## Part 3:  Push your Docker image to ECR

- Create an ECR repo

```bash
python3 ecr.py
```

- Push the Docker image to ECR (you can find the ECR repo URI in your AWS  ECR dashboard)

```bash
docker push <ecr_repo_uri>:my-app
```

## Part 4: Creating an EKS cluster

- Follow the AWS documentation to create your EKS cluster and add node groups
- Make sure to edit the name of the image in eks.py with your image Uri.

## Part 5: Deploying the application

```bash
python3 eks.py
```

## Part 6:  Verify Deployment

```bash
kubectl get deployment -n default
kubectl get service -n default
kubectl get pods -n default
```

## Part 7: Expose the service on your local machine (you can get the service name during verfication)

```bash
kubectl port-forward service/<service_name> 5000:5000
```
## Demo

Insert gif or link to demo
