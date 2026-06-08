# DevOps CI/CD Pipeline using Google Cloud

## Project Overview

This project demonstrates the implementation of a complete Continuous Integration (CI) workflow using GitHub, Docker, Google Cloud Build, Artifact Registry, and Compute Engine.

A simple Python Flask web application was developed, containerized using Docker, stored in Artifact Registry, and automatically rebuilt whenever code changes were pushed to GitHub.

---

## Architecture

GitHub Repository
↓
Cloud Build Trigger
↓
Cloud Build
↓
Docker Image
↓
Artifact Registry
↓
Compute Engine VM

---

## Technologies Used

* Python
* Flask
* Docker
* Git & GitHub
* Google Cloud Shell
* Cloud Build
* Artifact Registry
* Compute Engine
* Gunicorn

---

## Project Structure

```text
devops-repo/
│
├── main.py
├── requirements.txt
├── Dockerfile
│
└── templates/
    ├── layout.html
    └── index.html
```

---

## Features Implemented

### Source Code Management

* Created GitHub repository
* Cloned repository into Cloud Shell
* Managed code using Git

### Flask Application Development

* Created a simple web application
* Rendered HTML templates
* Displayed dynamic page content

### Containerization

* Created Dockerfile
* Packaged application into Docker image
* Configured Gunicorn as production web server

### Cloud Build Integration

* Built Docker images using Cloud Build
* Automated image creation from source code

### Artifact Registry

* Created Docker repository
* Stored and managed container images

### Continuous Integration

* Connected GitHub repository to Cloud Build
* Configured automatic build trigger
* Automatically rebuilt images after code changes

### Deployment Testing

* Deployed Docker image on Compute Engine
* Verified application functionality using VM external IP

---

## Docker Build Process

1. Pull Python 3.13 base image
2. Create application working directory
3. Copy application source code
4. Install Gunicorn
5. Install Flask dependencies
6. Configure application port
7. Launch application using Gunicorn

---

## Continuous Integration Workflow

1. Developer updates source code
2. Changes are committed and pushed to GitHub
3. Cloud Build Trigger detects the change
4. Cloud Build starts automatically
5. Docker image is built
6. Image is stored in Artifact Registry
7. Updated image becomes available for deployment

---

## Commands Used

### Git Commands

```bash
git add --all
git commit -m "message"
git push origin main
```

### Create Docker Image

```bash
gcloud builds submit --tag IMAGE_NAME .
```

### View Project ID

```bash
echo $DEVSHELL_PROJECT_ID
```

### Configure Docker Authentication

```bash
gcloud auth configure-docker us-east4-docker.pkg.dev
```

---

## Learning Outcomes

Through this project I learned:

* Git and GitHub workflows
* Docker containerization
* Cloud Build automation
* Artifact Registry image management
* Continuous Integration concepts
* Build triggers
* Compute Engine deployment
* DevOps pipeline fundamentals

---

## Final Result

Successfully built and tested an automated CI/CD workflow where code changes pushed to GitHub automatically triggered Docker image builds and stored them in Artifact Registry for deployment on Google Cloud.

---

## Author

Sunidhi Pandey
