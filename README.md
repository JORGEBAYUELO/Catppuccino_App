# React App on AWS EKS with ArgoCD (GitOps + CI/CD)

## Project Overview

This project demonstrates how to **deploy a React web application on AWS EKS (Elastic Kubernetes Service)** using **ArgoCD for GitOps-based deployment** and **GitHub Actions for CI/CD**.

Key highlights:

- **Frontend:** React app containerized with Docker and served via **NGINX.**
- **Infrastructure:** AWS EKS cluster with managed node groups.
- **GitOps Workflow:** ArgoCD continuously syncs Kubernetes manifest from GitHub.
- **CI/CD Pipeline:** GitHub Actions builds & pushes the Docker image to Docker Hub, and ArgoCD deploys the latest version automatically.

How the pipeline works:

1. Builds and pushes a Docker image of the React app to **Docker Hub** via **GitHub Actions**.
2. Deploys the application to **EKS** through **ArgoCD**.
3. Exposes the app using **NGINX Ingress** for external access.

This project highlights my DevOps skills across **AWS, Kubernetes, Docker, CI/CD automation, and GitOps**.

---

## Infrastructure Setup

### 1. EKS Cluster Creation

- Created an **EKS cluster** with `eksctl`:
- Two managed nodegroups:
  - **t3.micro** for general workloads.
  - **t3.medium** dedicated for ArgoCD.

```bash
eksctl create cluster --name portfolio-eks --region us-east-1 --nodegroup-name demo-nodes --node-type t3.micro --nodes 1 --nodes-min 1 --nodes-max 1 --managed
```

```bash
eksctl create nodegroup --cluster portfolio-eks --region us-east-1 --name argocd-nodes --node-type t3.medium --nodes 1 --nodes-min 1 --nodes-max 1 --managed
```
```
```

### 2. NGINX Ingress Controller

Installed to handle external traffic and expose the React app:

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/aws/deploy.yaml
```

### 3. ArgoCD Installation

Installed ArgoCD in the `argocd` namespace:

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

Expose ArgoCD UI using port-forward:

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

Then open http://localhost:8080 in your browser.

#### Default Login Credentials

- **Username:** `admin`
- **Password:** auto-generated, stored in a Kubernetes secret:

```bash
kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d
```

## Deployment

### 1. React App Dockerization

```
```
```
```
```
```
```
```
