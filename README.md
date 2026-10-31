# AZ STORE – End-to-End DevOps Project

An end-to-end DevOps project demonstrating how to build, containerize, deploy, automate, and monitor a static e-commerce application using AWS, Docker, GitHub Actions, and Ansible.

## Project Overview

AZ STORE is a demo e-commerce website deployed on an AWS EC2 Ubuntu server. The project uses Docker for containerization and GitHub Actions for automated CI/CD deployment.

## Technologies Used

- **AWS EC2** – Cloud hosting
- **Ubuntu 24.04** – Server operating system
- **Git and GitHub** – Source code management
- **Docker** – Application containerization
- **Nginx** – Web server
- **GitHub Actions** – CI/CD automation
- **Self-hosted GitHub Actions Runner** – Executes deployment jobs on EC2
- **Ansible** – Configuration management and deployment verification
- **Cron** – Scheduled application health checks
- **Bash** – Health-check scripting

## Project Structure

```text
AZ-store/
├── .github/
│   └── workflows/
│       └── deploy.yml
├── app/
│   └── index.html
├── deploy/
│   └── nginx/
│       └── az-store.conf
├── Dockerfile
└── README.md
```

## CI/CD Pipeline

The GitHub Actions workflow automates deployment whenever code is pushed to the `main` branch.

Pipeline steps:

1. Checkout source code.
2. Build the Docker image.
3. Remove the previous application container.
4. Start a new container.
5. Verify the application using an HTTP health check.

## Docker Deployment

The application is containerized using Docker and served through Nginx.

- Docker image: `az-store:latest`
- Container: `az-store-container`
- Application port: `8080`
- Container port: `80`

## Ansible Automation

Ansible is used to:

- Verify connectivity using the Ansible ping module.
- Ensure the Docker service is running and enabled.
- Verify that the AZ STORE Docker container is running.
- Confirm successful execution using an Ansible playbook.

Note: The current learning demonstration uses localhost as both the Ansible control node and managed node.

## Application Monitoring

A Bash health-check script verifies:

- Application HTTP availability.
- Docker container running status.

Cron executes the health-check script every five minutes and records results in:

`/var/log/az-store-health.log`

## Deployment

The application was deployed on an AWS EC2 Ubuntu instance and accessed through:

`http://<EC2-PUBLIC-IP>:8080`

## Project Status

### Completed
- [x] GitHub repository setup
- [x] AWS EC2 Ubuntu server deployment
- [x] Docker installation and containerization
- [x] Nginx-based application hosting
- [x] GitHub Actions CI/CD pipeline
- [x] Self-hosted GitHub Actions runner
- [x] Automated Docker deployment
- [x] Ansible connectivity and playbook verification
- [x] Application health-check script
- [x] Five-minute scheduled monitoring using cron

### Future Enhancements
- [ ] Prometheus monitoring
- [ ] Grafana dashboards
- [ ] Ansible configuration management from a separate control node
- [ ] Improved deployment security and notifications

## Learning Outcomes

This project demonstrates practical experience with cloud infrastructure, Linux administration, containerization, CI/CD automation, configuration management, and basic application monitoring.