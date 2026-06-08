Deploying Applications to Google Cloud
Overview

This lab demonstrated how to deploy the same Python web application on multiple Google Cloud compute platforms. The application was containerized using Docker and then deployed to App Engine, Google Kubernetes Engine (GKE), and Cloud Run to understand the differences between Platform as a Service (PaaS), Kubernetes-based deployments, and serverless container deployments.

Objectives
Download a sample application from GitHub
Deploy the application to App Engine
Deploy the application to Google Kubernetes Engine (GKE)
Deploy the application to Cloud Run
Technologies Used
Python
Flask
Docker
Google Cloud Build
Artifact Registry
App Engine
Google Kubernetes Engine (GKE)
Cloud Run
Kubernetes
GitHub
Lab Workflow
1. Downloaded Sample Application

Cloned the sample Python web application from GitHub into Cloud Shell.

Purpose:

Obtain the source code.
Prepare the application for deployment.

Key Files

main.py – Flask application
requirements.txt – Python dependencies
templates/index.html – Web page template
2. Created Dockerfile

Created a Dockerfile to containerize the application.

FROM python:3.13

WORKDIR /app

COPY . .

RUN pip install gunicorn
RUN pip install -r requirements.txt

ENV PORT=8080

CMD exec gunicorn --bind :$PORT --workers 1 --threads 8 main:app
What each instruction does
Instruction	Purpose
FROM	Uses Python 3.13 base image
WORKDIR	Sets working directory
COPY	Copies application files
RUN	Installs dependencies
ENV	Sets application port
CMD	Starts Flask application using Gunicorn
3. Built Docker Image

Built the application container image.

docker build -t test-python .
Purpose
Package application and dependencies.
Create a portable deployment artifact.
4. Tested Application Locally

Ran the container locally in Cloud Shell.

docker run --rm -p 8080:8080 test-python

Opened Web Preview and verified the application was working.

Deployment 1: App Engine
What is App Engine?

App Engine is Google's Platform as a Service (PaaS) offering.

It automatically manages:

Infrastructure
Servers
Scaling
Load balancing
Steps Performed

Created an app.yaml file.

Example:

runtime: python313

Deployed the application:

gcloud app deploy

Opened the application:

gcloud app browse
Result

Successfully deployed the Flask application to App Engine.

Learning
Simplest deployment option.
No server management required.
Automatic scaling.
Deployment 2: Google Kubernetes Engine (GKE)
What is GKE?

Google Kubernetes Engine is a managed Kubernetes service.

Provides:

Container orchestration
High availability
Autoscaling
Load balancing
Created GKE Cluster

Created a Kubernetes cluster in:

europe-west1-c

Connected to cluster:

gcloud container clusters get-credentials CLUSTER_NAME

Verified connection:

kubectl get nodes
Created Kubernetes Configuration

Created:

kubernetes-config.yaml

This file contained:

Deployment configuration
Service configuration
Deployment Section

Configured:

replicas: 3

Meaning:

Three container instances run simultaneously.
Improves availability and scalability.
Service Section

Configured:

type: LoadBalancer

Purpose:

Creates a public IP.
Routes traffic to application pods.
Built New Docker Image

Created an Artifact Registry repository.

gcloud artifacts repositories create devops-demo \
--repository-format=docker \
--location=europe-west1

Built image using Cloud Build:

gcloud builds submit \
--tag europe-west1-docker.pkg.dev/PROJECT_ID/devops-demo/devops-image:v0.2 .
Deployed to GKE
kubectl apply -f kubernetes-config.yaml

Verified deployment:

kubectl get pods

Verified service:

kubectl get services

Opened Load Balancer external IP.

Result

Application successfully ran on Kubernetes with 3 replicas.

Learning
Kubernetes manages containers.
Supports scaling and high availability.
Suitable for complex production workloads.
Deployment 3: Cloud Run
What is Cloud Run?

Cloud Run is a serverless container platform.

Features:

Deploy containers directly.
Automatic scaling.
Pay only when requests are received.
No cluster management.
Built Cloud Run Image

Used Cloud Build:

gcloud builds submit \
--tag europe-west1-docker.pkg.dev/PROJECT_ID/devops-demo/cloud-run-image:v0.1 .
Deployed Application
gcloud run deploy hello-cloud-run \
--image europe-west1-docker.pkg.dev/PROJECT_ID/devops-demo/cloud-run-image:v0.1 \
--region europe-west1

Selected:

Allow unauthenticated invocations
Result

Cloud Run generated a public URL: https://hello-cloud-run-356447962226.europe-west1.run.app/

Opening the URL displayed the web application successfully.

Learning
Simplest container deployment option.
No infrastructure management.
Automatic scaling to zero.
Cost-efficient for low traffic workloads.
Comparison of Deployment Platforms
Feature	App Engine	GKE	Cloud Run
Server Management	No	Partial	No
Container Support	Optional	Yes	Yes
Scaling	Automatic	Configurable	Automatic
Complexity	Low	High	Low
Cost	Medium	Higher	Pay-per-use
Best For	Web Apps	Large Systems	Microservices
Key Concepts Learned
Docker

Used to package applications and dependencies into portable containers.

Cloud Build

Automated container image creation.

Artifact Registry

Stores Docker container images securely.

App Engine

Fully managed application hosting platform.

Kubernetes

Container orchestration platform.

GKE

Managed Kubernetes service by Google Cloud.

Cloud Run

Serverless platform for containerized applications.

Load Balancer

Distributes traffic across multiple application instances.

Replicas

Multiple copies of an application running simultaneously for reliability and scalability.

Skills Gained
Docker containerization
Container image management
App Engine deployment
Kubernetes deployment
GKE cluster management
Cloud Run deployment
Artifact Registry usage
Cloud Build automation
Load balancing concepts
Scalable application deployment
Conclusion

In this lab, I successfully containerized a Python Flask application and deployed it across three Google Cloud platforms: App Engine, Google Kubernetes Engine (GKE), and Cloud Run. This provided practical experience with different cloud deployment models ranging from fully managed platforms to Kubernetes-based container orchestration and serverless container execution. The lab highlighted the trade-offs between simplicity, flexibility, scalability, and operational management across Google Cloud deployment services.
