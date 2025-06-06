# CI/CD Pipeline for Django Todoapp with Helm on Azure Kubernetes Service using GitHub Actions

# Project Overview:

This project demonstrates a complete CI/CD pipeline for a Django Todolist application
using GitHub Actions, Docker, Helm, and Kubernetes (Azure Kubernetes Service).
The application is packaged using a Helm chart and deployed to different environments
(development and staging) via reusable workflows.

# Tech Stack:

- Python (Django)
- Docker & DockerHub
- Helm
- Kubernetes (Azure Kubernetes Service)
- GitHub Actions (CI/CD)
- GitHub Actions Environments & Secrets

# What was done:

- Created a Docker image of the Django application using semantic versioning.
The image is built and tagged automatically via GitHub Actions.

- Stored DockerHub credentials, Azure credentials, and other sensitive data as GitHub Actions repository/environment secrets.
- Developed a main and reusable GitHub Actions workflow to deploy Helm charts to an Azure Kubernetes Service (AKS) cluster.

- Continuous Integration included:
  - Python-ci
  - Docker-ci
  - Helm-ci

- Continuous Deployment  included:

  - Handled via a reusable workflow (deployment-workflow.yml) and triggered automatically on push to main.
  - Authenticates into Azure and sets AKS context.
  - Performs Helm dry-run to catch release issues early.
  - Executes atomic helm upgrade --install to ensure safe deployment
  - Supports multiple environments:
    - development
    - staging (with custom values/stg.yaml)
    
- Helm Charts included:
  - todoapp/: Helm chart for the Django application
  - mysql/: Reused chart from a previous task for MySQL backend

# Triggering the Pipeline:
  - On push to main branch
  - On pull request targeting main
  - Manually via workflow_dispatch

# Link to the successful GitHub Actions run:
https://github.com/konstantinou77/devops_todolist_cicd_task_5_deploy_to_k8s/actions/runs/14795749052

