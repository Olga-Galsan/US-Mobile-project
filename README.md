# DevOps Take-Home Assignment – EKS + GitOps


## Overview

This project demonstrates a GitOps-based deployment pipeline on AWS EKS using Terraform, ArgoCD, Helm, and Kubernetes. It provisions cloud infrastructure, sets up GitOps automation, and deploys a sample microservice to an EKS cluster.

---

## 🛠 Tech Stack

- **AWS EKS** – Kubernetes Cluster
- **Terraform** – Infrastructure as Code (IaC)
- **Helm** – Kubernetes Package Manager
- **ArgoCD** – GitOps Continuous Delivery
- **Kubernetes** – Container Orchestration
- **GitHub** – Source Code Management

---

## 📁 Project Structure


---

## 🚀 How It Works

### 1. Infrastructure Provisioning (Terraform)
- Provisions VPC, subnets, IAM roles, and an EKS cluster using public Terraform modules.
- After `terraform apply`, outputs EKS endpoint and cluster name.

### 2. GitOps Setup (ArgoCD)
- ArgoCD is installed via Helm and configured to sync with this GitHub repo.
- ArgoCD watches the `applications/` folder for Kubernetes app definitions.

### 3. Application Deployment (Helm)
- Sample `nginx-app` is packaged as a Helm chart.
- Chart includes:
  - `Deployment`, `Service`, `ServiceAccount`
  - Optional: `HPA`, `Ingress`
- ArgoCD syncs the Helm chart to the EKS cluster.

### 4. Rollbacks
- ArgoCD provides automatic rollback on sync failure.

---

## 🧪 Testing Rollback

To simulate a failure:
- Manually break something in the Helm chart (e.g., set `image.tag: invalid`)
- Commit the change
- ArgoCD will detect the failure and show it in the UI
- Fix the error and commit again to recover

---

## ✨ Extra Credit

> Implemented: ✅ ArgoCD + Helm  
> Optional: Argo Rollouts (blue/green) – *not implemented yet*

---

## 🔒 Security

- Sensitive values like `tfvars` and `.terraform` folders are excluded via `.gitignore`.
- No secrets are hardcoded.

---

## Author

Olga Galsan – https://github.com/Olga-Galsan/US-Mobile-project
