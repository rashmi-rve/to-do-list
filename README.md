# To-Do List — Node.js CI/CD Reference Project

A simple Node.js to-do list application used as a hands-on reference for a full DevOps pipeline: containerization with Docker, CI with Jenkins, code quality with SonarQube, infrastructure provisioning with Terraform, and deployment to Kubernetes (with Kustomize overlays).

## Features

- Add, view, and manage to-do items through a lightweight Express + EJS web UI
- Dockerized app with a ready-to-use `docker-compose.yaml` for local development
- Jenkins pipeline (`Jenkinsfile`) for automated build, test, and deployment
- Infrastructure-as-Code with Terraform for provisioning cloud resources
- Kubernetes manifests and Kustomize overlays for deploying to a cluster


## Tech Stack

| Layer            | Technology                          |
|-------------------|--------------------------------------|
| Application       | Node.js, Express, EJS, body-parser  |
| Testing           | Mocha, Chai, Supertest, NYC         |
| Containerization  | Docker, Docker Compose              |
| CI/CD             | Jenkins                             |
| Infrastructure    | Terraform                           |
| Orchestration     | Kubernetes, Kustomize               |

## Project Structure

```
to-do-list/
├── DevSecOps/               # Security scanning & DevSecOps pipeline config
├── k8s/                     # Raw Kubernetes manifests
├── kustomize/               # Kustomize overlays for different environments
├── terraform/               # Terraform configs for infrastructure provisioning
├── views/                   # EJS templates for the web UI
├── app.js                   # Application entry point
├── test.js                  # Test suite
├── Dockerfile               # Container image definition
├── docker-compose.yaml      # Local multi-container setup
├── Jenkinsfile              # CI/CD pipeline definition
├── package.json             # Node.js dependencies & scripts
└── README.md
```

## Prerequisites

- [Node.js](https://nodejs.org/) and npm
- [Docker](https://www.docker.com/) and Docker Compose (optional, for containerized runs)
- [Terraform](https://www.terraform.io/) (optional, for provisioning infrastructure)
- Access to a [Kubernetes](https://kubernetes.io/) cluster and `kubectl` (optional, for deployment)
- [Jenkins](https://www.jenkins.io/) (optional, for running the CI/CD pipeline)

## Getting Started

### Run Locally

```bash
sudo apt install nodejs
sudo apt install npm
npm install
node app.js
```

The app will be available at `http://localhost:8080` (or whichever port is configured in `app.js`).

### Run with Docker Compose

```bash
docker compose up --build
```

### Run Tests

```bash
npm test
```

## CI/CD Pipeline

The included `Jenkinsfile` defines a pipeline that typically:

1. Checks out the source code
2. Installs dependencies and runs tests
3. Runs a SonarQube code quality scan
4. Builds and pushes a Docker image
5. Deploys the application (e.g., to Kubernetes)

Configure your Jenkins server with the required credentials (Docker registry, SonarQube token, kubeconfig, etc.) before running the pipeline.

## Infrastructure (Terraform)

The `terraform/` directory contains configuration to provision the underlying infrastructure (e.g., a Kubernetes cluster or supporting cloud resources).

```bash
cd terraform
terraform init
terraform plan
terraform apply
```

## Deploying to Kubernetes

Apply the raw manifests directly:

```bash
kubectl apply -f k8s/
```

Or deploy using Kustomize overlays:

```bash
kubectl apply -k kustomize/
```

## Author

Rashmi
