# DevOps CI/CD Pipeline with Google Cloud

## Overview

This project demonstrates the implementation of a simple DevOps CI/CD workflow using Google Cloud services, Docker, GitHub, and Cloud Build. The lab focused on creating a Python web application, containerizing it with Docker, storing images in Artifact Registry, and automating builds using Cloud Build triggers.

---

## Objectives

* Create a GitHub repository
* Build a simple Python web application
* Test the application in Google Cloud Shell
* Create a Dockerfile for containerization
* Build and manage Docker images using Cloud Build and Artifact Registry
* Automate builds using Cloud Build triggers
* Test automated build changes

---

## Technologies Used

* Python
* Flask
* Docker
* Google Cloud Shell
* Google Cloud Build
* Artifact Registry
* GitHub
* Compute Engine VM

---

## Project Structure

```bash
devops-repo/
│
├── main.py
├── requirements.txt
├── Dockerfile
├── templates/
│   └── layout.html
└── README.md
```

---

## Application Description

A simple Flask web application was created and tested locally in Cloud Shell. The application was then containerized using Docker and deployed using Google Cloud services.

---

## Steps Performed

### 1. Created GitHub Repository

* Created a repository named `devops-repo`
* Connected GitHub with Google Cloud Build

### 2. Built Python Flask Application

* Developed a simple Flask web application
* Added dependencies in `requirements.txt`

### 3. Tested Application in Cloud Shell

* Executed the Flask application locally
* Verified browser output

### 4. Created Dockerfile

* Defined Docker image configuration
* Used Gunicorn for production server

### 5. Built Docker Image

Used Cloud Build to build the Docker image:

```bash
gcloud builds submit --tag us-east4-docker.pkg.dev/PROJECT_ID/devops-repo/devops-image:v0.1 .
```

---

### 6. Stored Image in Artifact Registry

* Created Artifact Registry repository
* Uploaded Docker image successfully

---

### 7. Automated Builds with Triggers

* Connected GitHub repository to Cloud Build
* Created automatic build trigger on code push
* Verified successful builds in Cloud Build history

---

### 8. Tested Build Changes

* Modified application files
* Pushed changes to GitHub
* Confirmed automatic rebuild execution

---

## Key Concepts Learned

* Continuous Integration (CI)
* Docker containerization
* Artifact management
* Automated build pipelines
* GitHub integration with Google Cloud
* Cloud Build triggers
* DevOps workflow automation

---

## Commands Used

### Run Flask App

```bash
python3 main.py
```

### Build Docker Image

```bash
gcloud builds submit --tag IMAGE_NAME
```

### Run Docker Container

```bash
docker run -d -p 80:80 IMAGE_NAME
```

### View Running Containers

```bash
docker ps
```

---

## Outcome

Successfully implemented a basic CI/CD pipeline using Google Cloud services. The project demonstrated how automated cloud-based builds and container management simplify modern DevOps workflows.

---

## Author

Sunidhi Pandey
