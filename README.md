Project 4 – Cloud Deployment with AWS, Terraform & GitHub Actions

Overview

This project demonstrates a complete CI/CD pipeline that deploys a Dockerized application to AWS EC2 using GitHub Actions and Terraform.

The deployment is fully automated:
- Code push → triggers GitHub Actions
- GitHub Actions → connects to EC2 via SSH
- EC2 → pulls latest Docker image from GHCR
- Application is redeployed using Docker Compose

---

Tech Stack

- AWS EC2
- Terraform
- Docker & Docker Compose
- GitHub Actions
- GHCR (GitHub Container Registry)
- Linux (Ubuntu)

---

Architecture

1. Application image is built and pushed to GHCR (Project 2)
2. GitHub Actions pipeline runs on push
3. SSH connection is established to EC2
4. Docker Compose pulls latest image
5. Container is recreated
6. Health check verifies deployment

---

Deployment Flow
git push → GitHub Actions → SSH → EC2 → docker compose → app live


---

Key Features

- Automated remote deployment via SSH
- Secure key handling using GitHub Secrets
- Infrastructure defined with Terraform
- Zero manual deployment steps
- Health check after deployment

---

Project Structure
.github/workflows/deploy.yml # CI/CD pipeline
terraform/main.tf # Infrastructure as code


---

Lessons Learned

- Handling SSH keys securely in CI/CD
- Debugging GitHub Actions runners
- Managing EC2 lifecycle (start/stop, IP changes)
- Dealing with container startup timing issues
- Building reliable deployment health checks

---

How to Run

1. Provision infrastructure with Terraform
2. Configure GitHub Secrets:
   - EC2_HOST
   - EC2_USER
   - EC2_SSH_KEY_B64
3. Push to main branch

Deployment runs automatically.

---

Status

Production-like deployment working with automated CI/CD pipeline.
