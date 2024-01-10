# Nginx Deployment on Kubernetes

This repository contains the Kubernetes configuration files for deploying a Nginx server on a Kubernetes cluster, specifically tailored for a Kubernetes environment managed by Docker Desktop. The deployment demonstrates setting up a basic web server that responds with "Hello, world!".

## Overview

The deployment is structured into three parts: the Nginx server deployment, a ConfigMap for Nginx configuration, and a NodePort service to expose Nginx externally.

### Files in This Repository

- `hello-world-deployment.yaml`: Defines the Nginx deployment.
- `nginx-configmap.yaml`: Contains the ConfigMap for the Nginx configuration.
- `nginx-service.yaml`: Defines the NodePort service to expose Nginx.

## Prerequisites

- Docker Desktop with Kubernetes enabled.
- `kubectl` command-line tool installed and configured to interact with your Kubernetes cluster.

## Steps to Deploy

1. **Applying the Nginx ConfigMap**
   - The `nginx-configmap.yaml` creates a ConfigMap with a custom Nginx configuration.
   ```bash
   kubectl apply -f nginx-configmap.yaml
   ```
![image](https://github.com/owootomo/nginx-kubernetes-deployment/assets/144632027/f4647589-6500-4cc7-9bd3-67d475ac48f1)

2. **Deploying Nginx**
The hello-world-deployment.yaml deploys Nginx using the latest stable Alpine image.
```bash
kubectl apply -f hello-world-deployment.yaml
```
![image](https://github.com/owootomo/nginx-kubernetes-deployment/assets/144632027/1fc35621-8fb7-4f61-8267-af5716f29e53)

3. **Deploying Nginx**
The nginx-service.yaml exposes the Nginx service on port 30080 externally and port 80 internally.
```bash
kubectl apply -f nginx-service.yaml
```
![image](https://github.com/owootomo/nginx-kubernetes-deployment/assets/144632027/3995baf7-c958-423f-825e-eb1e6212d9d9)

4. **Verifying the Deployment**
Ensuring the deployment is running smoothly:
```bash
kubectl get deployments
kubectl get pods
kubectl get services
```
![image](https://github.com/owootomo/nginx-kubernetes-deployment/assets/144632027/d563a4a9-6003-4192-bf0b-d38ed3ff103c)
![image](https://github.com/owootomo/nginx-kubernetes-deployment/assets/144632027/a1551b26-019c-4eb1-aa2f-bb43f236529e)
![image](https://github.com/owootomo/nginx-kubernetes-deployment/assets/144632027/2a02b214-8f38-4e0d-ad93-37eda939be4d)

5. **Accessing the Nginx Service**
The Nginx service is accessible from outside the Kubernetes cluster at http://localhost:30080.
