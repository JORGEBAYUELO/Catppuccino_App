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
eksctl create cluster --name portfolio-eks --region us-east-1 --nodegroup-name demo-nodes --node-type t3.micro --nodes 1
```
