# devops-eks-microservices-platform
Production-grade DevOps platform on AWS EKS with Terraform, CI/CD (GitHub Actions), Helm deployments, auto-scaling, monitoring (Prometheus/Grafana), logging (Loki), and security scanning (Trivy)

<img width="1536" height="1024" alt="ee" src="https://github.com/user-attachments/assets/7f962f43-9514-4667-849f-20bd3858a5a5" />
# DevOps EKS Microservices Platform

[![CI](https://github.com/ragavitdevops/devops-eks-microservices-platform/actions/workflows/ci.yml/badge.svg)](https://github.com/ragavitdevops/devops-eks-microservices-platform/actions/workflows/ci.yml)
[![CD](https://github.com/ragavitdevops/devops-eks-microservices-platform/actions/workflows/cd.yml/badge.svg)](https://github.com/ragavitdevops/devops-eks-microservices-platform/actions/workflows/cd.yml)
[![Trivy Scan](https://img.shields.io/badge/Security-Trivy-brightgreen)](https://github.com/aquasecurity/trivy)
[![Terraform fmt](https://img.shields.io/badge/Terraform-fmt-blue)](https://github.com/hashicorp/terraform)
[![Terraform validate](https://img.shields.io/badge/Terraform-validate-green)](https://github.com/hashicorp/terraform)
[![K8s Deployment](https://img.shields.io/badge/Kubernetes-Deployment-orange)](https://kubernetes.io/)

---

## Project Overview

This is a **production-grade DevOps platform** deploying microservices on **AWS EKS** using **Terraform**, **Helm**, and **CI/CD pipelines** via **GitHub Actions**.  

Key features:

- **Infrastructure as Code (IaC)** with Terraform
- **Kubernetes EKS cluster** with Auto-scaling
- **Microservices deployment** via Helm charts
- **CI/CD pipelines** for build, scan, and deploy
- **Security scanning** with Trivy
- **Monitoring and logging** with Prometheus, Grafana, and Loki

This project is **fully automated** and ideal for showcasing a **DevOps portfolio for overseas jobs**.

---

## Architecture Diagram

![Architecture](./docs/architecture.png)

> Diagram includes EKS cluster, Terraform provisioning, CI/CD flow, microservices deployment via Helm, and monitoring/logging stack.

---

## Project Structure


devops-eks-platform/
├── terraform/ # Terraform configs for EKS, VPC, IAM, and security
│ ├── eks/
│ └── vpc/
├── helm-charts/ # Helm charts for microservices
│ └── backend/
├── microservices/ # Application code
│ └── backend/
├── .github/
│ └── workflows/ # CI/CD GitHub Actions workflows
├── docs/ # Architecture diagrams and documentation
└── README.md


---

## Features

### 1. Infrastructure as Code (Terraform)

- Creates **VPC, subnets, EKS cluster, IAM roles**
- Supports **auto-scaling** and **high availability**
- Secure with **KMS keys, encrypted S3 buckets, and policies**

### 2. Microservices Deployment (Helm)

- Backend microservice containerized with **Docker**
- Helm charts for **templated Kubernetes deployment**
- Easy to extend for additional services

### 3. CI/CD Pipelines

**CI Pipeline:**

- Builds Docker image
- Runs **Trivy vulnerability scan**
- Pushes image to **AWS ECR**

**CD Pipeline:**

- Configures `kubectl` and connects to EKS
- Deploys services using **Helm**
- Monitors deployment logs

### 4. Security & Compliance

- Trivy scans for **Docker images and Terraform code**
- Detects **vulnerabilities and misconfigurations**
<img width="908" height="499" alt="Trivy_scan" src="https://github.com/user-attachments/assets/76398d5f-71d5-4275-b573-0aaf778f39f7" />

<img width="521" height="68" alt="app_test" src="https://github.com/user-attachments/assets/89ae371d-463a-4df5-9583-ddf2c8099779" />

### 5. Monitoring & Logging

- **Prometheus**: Metrics collection
- **Grafana**: Dashboards for cluster and service metrics
- **Loki**: Centralized logging for all pods

---

## Getting Started

### Prerequisites

- **AWS Account** with EKS permissions
- **Terraform ≥ 1.5**
- **Kubectl ≥ 1.29**
- **Helm ≥ 3**
- **Docker** installed
- **GitHub Actions** configured for CI/CD

### Deployment Steps

1. **Clone the repository**

```bash
git clone https://github.com/ragavitdevops/devops-eks-microservices-platform.git
cd devops-eks-platform

**Deploy infrastructure with Terraform **
cd terraform
terraform init
terraform apply

**Build and push Docker images**
docker build -t backend ./microservices/backend
docker tag backend:latest <ECR_URL>/backend:latest
docker push <ECR_URL>/backend:latest

**Deploy Helm charts to EKS**
helm upgrade --install backend helm-charts/backend

**Access backend service**
kubectl get svc backend
# Use EXTERNAL-IP in browser or curl

**Check monitoring stack**
kubectl get pods -n monitoring
kubectl port-forward -n monitoring svc/grafana 3000:3000
# Access Grafana at http://localhost:3000
Security Scans

# Scan Docker image
trivy image <ECR_URL>/backend:latest

# Scan Terraform code
cd terraform
trivy config .
Contact / Author

Raghunatha M

GitHub: ragavitdevops
Email: ragav.it.devops@gmail.com
