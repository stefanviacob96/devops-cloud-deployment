Cloud Deployment with AWS, Terraform & GitHub Actions

Overview

End-to-end CI/CD pipeline that automatically deploys a Dockerized application to AWS EC2 using GitHub Actions and Terraform.

Flow:
git push → GitHub Actions → SSH → EC2 → Docker Compose → Application live

---

Tech Stack

- AWS EC2
- Terraform
- Docker & Docker Compose
- GitHub Actions
- GitHub Container Registry (GHCR)
- Linux (Ubuntu)

---

Key Features

- Automated deployment via GitHub Actions
- Remote execution over SSH with secure key handling
- Infrastructure provisioned with Terraform
- Container-based deployment using Docker Compose
- Health checks to verify successful deployment
- No manual steps required after initial setup

---

Architecture

1. Application image is built and pushed to GHCR
2. GitHub Actions pipeline triggers on push to `main`
3. Runner connects to EC2 via SSH
4. EC2 pulls the latest image
5. Docker Compose recreates the container
6. Health check validates deployment

---

Project Structure


.github/workflows/deploy.yml
CI/CD pipeline
terraform/main.tf
Infrastructure as code
README.md

---

How to Run

1. Provision infrastructure:
   ```bash
   terraform init
   terraform apply
   ```

2. Configure GitHub Secrets:
   - `EC2_HOST`
   - `EC2_USER`
   - `EC2_SSH_KEY_B64`

3. Push to main:
   ```bash
   git push origin main
   ```

Deployment runs automatically.

---

Lessons Learned

- Managing SSH authentication in CI/CD pipelines
- Debugging network issues between GitHub runners and EC2
- Handling dynamic EC2 public IPs (Elastic IP recommended)
- Building reliable deployment health checks
- Structuring reproducible infrastructure with Terraform

---

Status

Production-like deployment pipeline fully functional.
