# PRODYNA DevOps Challenge

This repository contains my solution for the PRODYNA DevOps / Automation Engineer task.

## 1. Task Understanding

The goal is to design a cloud environment including CI/CD for a Single Page Application consisting of:

- Vue.js frontend
- Node.js backend
- MongoDB-compatible NoSQL database

The target hyperscaler is Microsoft Azure.

The solution should fulfill the following requirements:

- preferred usage of Platform as a Service components
- full description of the infrastructure as code
- full automation of infrastructure deployment and application build/deploy jobs
- support for fast development cycles through cloud-native technologies

---

## 2. Solution Design

## Preferred solution

I would choose the following Azure-based PaaS architecture:

- **Frontend:** Azure Static Web Apps
- **Backend:** Azure App Service
- **Database:** Azure Cosmos DB with MongoDB API
- **Secrets / configuration:** Azure Key Vault
- **Monitoring / observability:** Azure Monitor + Application Insights

### Why this solution?

This architecture minimizes operational overhead by using managed Azure services.  
It supports fast deployments, easy scaling and reduced maintenance effort.  
It is especially suitable for teams that want to focus on development speed and reliability instead of managing infrastructure manually.

### Alternative solution

As an alternative, the application could also be deployed container-based on Azure Kubernetes Service (AKS).  
This would provide more flexibility and portability, but it would also increase operational complexity significantly.  
Since the task explicitly prefers PaaS components, I would not choose AKS as the preferred solution.

---

## 3. PaaS / SaaS Components

The following Azure services would be used:

- Azure Static Web Apps
- Azure App Service
- Azure Cosmos DB (MongoDB API)
- Azure Key Vault
- Azure Monitor / Application Insights
- GitHub Actions or Azure DevOps Pipelines

Optional supporting services:

- Azure Container Registry (if containerization is later required)
- Azure Storage Account (for Terraform state)

---

## 4. Infrastructure as Code

Terraform is used as the Infrastructure as Code tool.

### Why Terraform?

- cloud-independent and widely adopted
- good modularization
- suitable for CI/CD integration
- versionable in Git

### Terraform environments

The infrastructure is separated into three stages:

- dev
- staging
- prod

Each stage has its own Terraform entry point.

Terraform is used to provision:

- resource groups
- app services
- static web app resources
- cosmos DB
- key vault
- monitoring components

---

## 5. Git / Repository Structure

The repository is structured as follows:

```text
prodyna-devops-challenge
│
├── README.md
├── architecture/
├── terraform/
│   ├── dev/
│   ├── staging/
│   └── prod/
├── pipelines/
│   ├── ci.yml
│   └── cd.yml
└── presentation/
