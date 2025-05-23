
# Sample Node.js App with MongoDB on Minikube

This project demonstrates how to deploy a sample Node.js application connected to a MongoDB backend using **Minikube** and **Docker** within a **Kubernetes** environment.

---

## 🚀 Project Objectives

- Containerize a Node.js web application.
- Deploy MongoDB with persistent storage.
- Configure secrets and services in Kubernetes.
- Expose the application using `NodePort` for browser access.
- Run everything locally using Minikube.

---

## 📁 Prerequisites

Make sure you have the following installed:

- [Docker](https://docs.docker.com/)
- [Minikube](https://minikube.sigs.k8s.io/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- A [Docker Hub](https://hub.docker.com/) account


## 🐳 Docker Image Build & Push

1. Build the Docker image:

   ```bash
   docker build -t muhammad532/sample-app:latest . 
2. Push to Docker Hub:

   ```bash
   docker push muhammad532/sample-app:latest
   ```
   
   
  ## ☸️ Kubernetes Deployment

Apply the following YAML files **in order**:

```bash
kubectl apply -f mongodb-secret.yaml
kubectl apply -f mongodb-pv.yaml
kubectl apply -f mongodb-pvc.yaml
kubectl apply -f mongodb-deployment.yaml
kubectl apply -f mongodb-service.yaml

kubectl apply -f app-deployment.yaml
kubectl apply -f app-service.yaml
```

---

## 🌐 Access the Web App

Use Minikube to open the service in your browser:

```bash
minikube service sample-app-service
```

Minikube will launch a browser tab at a local URL (e.g., `http://127.0.0.1:32001`) to access the app.

---

## 🧪 Verify Deployments

Check if pods and services are running correctly:

```bash
kubectl get pods
kubectl get services
```

You should see:

* MongoDB pod in a `Running` state
* App pod in a `Running` state
* NodePort services for both

---

## 🗂️ Project Structure

```bash
.
├── Dockerfile
├── app-deployment.yaml
├── app-service.yaml
├── mongodb-secret.yaml
├── mongodb-pv.yaml
├── mongodb-pvc.yaml
├── mongodb-deployment.yaml
├── mongodb-service.yaml
└── README.md
```

---

## 👤 Author

**Muhammad Nouman Qaiser**
SIT737 – Software Deployment and Operation
Deakin University
