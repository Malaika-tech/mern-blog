# MERN Blog Deployment using Docker & Kubernetes

## Project Overview

This project demonstrates containerization and deployment of a MERN stack application using Docker, Docker Compose, and Kubernetes.

The application consists of three main services:

- Frontend (React)
- Backend (Node.js / Express)
- Database (MongoDB)

The project shows how a multi-service application can be containerized and deployed with persistent storage and scaling capabilities.

# Tools and Technologies

- Docker
- Docker Compose
- Kubernetes
- Minikube
- Node.js
- React
- MongoDB

# Docker Containerization

Each service is containerized using Docker.

Frontend Dockerfile builds the React app and serves it using Nginx.
Backend Dockerfile builds the Node.js API.
MongoDB runs using the official MongoDB Docker image.

To build and run containers:
docker compose up --build

Check running containers:
docker ps

# Docker Compose Setup

Docker Compose is used to run multiple containers together.
Services defined:

- frontend
- backend
- mongo

This allows all services to communicate in the same network.

# Kubernetes Deployment

The application is deployed on Kubernetes using YAML manifests.

Deployment files include:
- frontend-deployment.yaml
- backend-deployment.yaml
- mongo-deployment.yaml
- hpa.yaml
- pv.yaml
- pvc.yaml

Each deployment runs **3 replicas** for high availability.

To deploy:
kubectl apply -f k8s/

Verify:
kubectl get pods

# Persistent Storage

MongoDB uses persistent storage to retain data.

Resources created:

- PersistentVolume (PV)
- PersistentVolumeClaim (PVC)

Verify storage:
kubectl get pv
kubectl get pvc

# Horizontal Pod Autoscaling

Horizontal Pod Autoscaler (HPA) is configured for the backend service.

Configuration:
Minimum Pods: 2
Maximum Pods: 5

CPU Utilization Target: 70%

Check autoscaler:
kubectl get hpa