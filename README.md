# CICDCLOUDS Java Web Application CI/CD Pipeline

## Overview

This project demonstrates an end-to-end CI/CD pipeline for a Java web application using:

- Jenkins
- Maven
- Docker
- Docker Hub
- Kubernetes (Minikube)

The pipeline automates:

1. Source Code Checkout
2. Maven Build
3. Docker Image Build
4. Docker Image Push to Docker Hub
5. Kubernetes Deployment Update

---

# Architecture

```text
Developer
   ↓
GitHub Repository
   ↓
Jenkins Pipeline
   ↓
Maven Build
   ↓
Docker Image Build
   ↓
Docker Hub Push
   ↓
Minikube Kubernetes Deployment
```

---

# Technologies Used

- Java
- Maven
- Jenkins
- Docker
- Docker Hub
- Kubernetes
- Minikube
- GitHub

---

# Jenkins Pipeline Stages

## 1. Checkout

Clones source code from GitHub.

```groovy
git branch: 'main', url: 'https://github.com/cicdclouds/cicdclouds_javawebappi.git'
```

---

## 2. Maven Build

Builds the Java application.

```bash
mvn clean package
```

---

## 3. Docker Build

Creates Docker image and tags it.

```bash
docker build -t hariprasad15/cicdclouds-java-app:${BUILD_NUMBER} .
docker tag hariprasad15/cicdclouds-java-app:${BUILD_NUMBER} hariprasad15/cicdclouds-java-app:latest
```

---

## 4. Push to Docker Hub

Authenticates and pushes Docker images.

```bash
docker push hariprasad15/cicdclouds-java-app:${BUILD_NUMBER}
docker push hariprasad15/cicdclouds-java-app:latest
```

---

## 5. Deploy to Kubernetes

Updates deployment image in Minikube.

```bash
kubectl set image deployment/java-web-deployment \
java-container=hariprasad15/cicdclouds-java-app:${BUILD_NUMBER}
```

---

# Environment Variables

| Variable | Description |
|----------|-------------|
| DOCKER_HUB_USER | Docker Hub Username |
| DOCKER_IMAGE | Docker Image Name |
| IMAGE_TAG | Jenkins Build Number |

---

# Jenkins Credentials

Create Jenkins credentials:

| Credential ID | Type |
|---------------|------|
| dockerhub-creds | Username with Password |

---

# Kubernetes Deployment

Example deployment update:

```bash
kubectl get deployments
kubectl get pods
kubectl get svc
```

---

# Docker Hub Repository

```text
hariprasad15/cicdclouds-java-app
```

---

# Future Improvements

- GitHub Actions integration
- Helm charts
- ArgoCD deployment
- SonarQube integration
- Trivy image scanning
- AWS EKS deployment

---

# Author

Hari Prasad  
DevOps & Cloud Engineer

- GitHub: https://github.com/cicdclouds
- Website: https://cicdclouds.com
