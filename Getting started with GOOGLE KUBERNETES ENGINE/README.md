# Getting Started with Google Kubernetes Engine (GKE)

## Overview

This course provided a hands-on introduction to **Containers, Kubernetes, and Google Kubernetes Engine (GKE)**. It covered the fundamentals of containerized applications, Kubernetes architecture, cluster management, and deploying workloads on Google Cloud using GKE.

Through videos, quizzes, and practical labs, I learned how modern cloud-native applications are packaged, deployed, managed, and scaled using Kubernetes.

---

## Objectives

* Understand containerization and container images.
* Learn how Docker and container runtimes work.
* Explore Kubernetes architecture and core concepts.
* Deploy and manage workloads using Google Kubernetes Engine (GKE).
* Understand GKE Autopilot and Standard modes.
* Use Cloud Build to build container images.
* Manage Kubernetes resources using kubectl.
* Troubleshoot and inspect Kubernetes workloads.

---

## Technologies & Services Used

* Google Kubernetes Engine (GKE)
* Kubernetes
* Docker
* Cloud Build
* Artifact Registry
* kubectl
* Google Cloud Console
* Cloud Shell
* IAM
* Virtual Private Cloud (VPC)

---

## Key Concepts Learned

### Containers

* Lightweight application runtime environments.
* Package applications with all required dependencies.
* Share the host operating system kernel.
* Faster startup and better resource utilization than Virtual Machines.

### Container Images

* Application + dependencies packaged together.
* Built using Dockerfiles.
* Organized into layered, reusable images.
* Stored in Artifact Registry.

### Docker

* Used to build and run container images.
* Provides containerization but not orchestration.

### Kubernetes

* Open-source container orchestration platform.
* Manages deployment, scaling, networking, and recovery of containers.
* Uses declarative configuration to maintain desired state.

### Google Kubernetes Engine (GKE)

* Managed Kubernetes service on Google Cloud.
* Simplifies cluster management and operations.
* Supports automatic upgrades, repairs, and scaling.

---

## Course Modules

### Module 1: Containers and Container Images

* Traditional deployment vs virtualization vs containers
* Container architecture
* Linux namespaces and cgroups
* Docker and container images
* Dockerfile fundamentals
* Multi-stage builds
* Artifact Registry

### Module 2: Kubernetes Fundamentals

* Kubernetes architecture
* Control Plane and Nodes
* Clusters
* Declarative vs Imperative configuration
* Workload management
* Scaling and resource management

### Module 3: Google Kubernetes Engine

* GKE overview
* Cluster creation
* Node management
* Auto-upgrade
* Auto-repair
* Cluster autoscaling

### Module 4: GKE Autopilot vs Standard

* Autopilot mode
* Standard mode
* Use cases and trade-offs
* Infrastructure management responsibilities

### Module 5: Kubernetes Resource Management

* Pods
* Deployments
* ReplicaSets
* Services
* Labels and Selectors
* Namespaces

### Module 6: kubectl and Cluster Introspection

* Configuring kubectl
* Managing workloads
* Viewing logs
* Describing resources
* Troubleshooting Pods
* Debugging deployment issues

---

## Hands-On Labs Completed

### Lab 1: Working with Cloud Build

* Built container images using Cloud Build.
* Automated container build processes.
* Stored images in Artifact Registry.

### Lab 2: Deploying GKE Autopilot Clusters

* Created and configured GKE Autopilot clusters.
* Deployed workloads to Kubernetes.
* Explored cluster management features.

### Lab 3: Deploying GKE Autopilot Clusters from Cloud Shell

* Managed clusters using Cloud Shell.
* Used kubectl commands.
* Inspected and troubleshot Kubernetes resources.

---

## Common kubectl Commands Learned

```bash
kubectl get pods
kubectl get deployments
kubectl describe pod <pod-name>
kubectl logs <pod-name>
kubectl exec -it <pod-name> -- sh
kubectl apply -f deployment.yaml
kubectl delete pod <pod-name>
```

---

## Skills Gained

* Containerization Fundamentals
* Docker Basics
* Kubernetes Architecture
* Kubernetes Deployments
* Cluster Management
* GKE Administration
* Cloud Build
* Artifact Registry
* kubectl Usage
* Application Deployment & Scaling
* Troubleshooting Kubernetes Workloads

---

## Key Takeaways

* Containers provide lightweight and portable application environments.
* Kubernetes automates deployment, scaling, and management of containerized applications.
* GKE simplifies Kubernetes operations by providing a managed control plane.
* Autopilot mode reduces operational overhead while Standard mode offers greater control.
* Cloud Build and Artifact Registry streamline container image management and deployment.
* kubectl is the primary tool for interacting with Kubernetes clusters.

---

## Outcome

By completing this course, I gained practical experience with containerized applications, Kubernetes orchestration, and Google Kubernetes Engine. I learned how to deploy, manage, scale, and troubleshoot workloads in a cloud-native environment using industry-standard tools and practices.
