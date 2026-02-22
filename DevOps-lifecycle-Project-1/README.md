# 🚀 DevOps Lifecycle Implementation Project

## 📌 Project Overview

This project demonstrates the implementation of a complete DevOps lifecycle for a web application hosted on GitHub.

Repository Used:
https://github.com/hshar/website.git

The objective was to design and automate:

- Infrastructure provisioning
- Configuration management
- Git branching workflow
- CI/CD automation
- Docker containerization
- Environment-based deployment (Test & Production)

This project simulates a real-world DevOps implementation scenario.

---

# 🏗 Infrastructure Setup

Three EC2 instances were created:

- Master Server – Jenkins + Ansible
- Test Server
- Production Server

![EC2 Overview](screenshots/01-ec2-instances-overview.png)

---

# ⚙ Configuration Management – Ansible

Ansible was used to configure the Test and Production servers automatically.

## 🔹 Tasks Automated

- Installed Java
- Installed Docker
- Ensured consistent configuration across nodes

## 🔹 Files Included

- `inventory` – Contains Test & Prod server IPs
- `playbook.yml` – Installs required software
- `script.sh` (if used)

## 🔹 Execution Command

```bash
ansible-playbook -i inventory playbook.yml
```

![Inventory](screenshots/07-ansible-inventory-file.png)
![Playbook Execution](screenshots/08-ansible-playbook-execution.png)

---

# 🧩 Jenkins Master–Agent Architecture

- Jenkins installed on Master server
- Test & Prod machines added as Jenkins nodes
- SSH-based agent configuration

![Jenkins Dashboard](screenshots/11-jenkins-dashboard.png)
![Jenkins Nodes](screenshots/14-jenkins-all-nodes.png)

---

# 🌿 Git Workflow Strategy

Branch-based deployment logic:

- `develop` branch → Deploy to Test environment
- `master` branch → Deploy to Production environment

Webhook configured to trigger Jenkins automatically on every push.

![Fork](screenshots/15-github-forked-repository.png)
![Develop Branch](screenshots/16-github-develop-branch.png)
![Webhook](screenshots/17-github-webhook-configuration.png)

---

# 🐳 Docker Containerization

The application was containerized using a Dockerfile.

Base Image:
```
hshar/webapp
```

Application directory:
```
/var/www/html
```

## Docker Commands Used in Pipeline

```bash
sudo docker build . -t img1
sudo docker run -itd --name cont1 -p 81:80 img1
```

---

# 🔁 CI/CD Pipeline Implementation

Three Jenkins jobs were created:

---

## 🔹 Job1 – Build

- Triggered on every commit
- Builds Docker image

![Job1](screenshots/18-jenkins-job1-build.png)

---

## 🔹 Job2 – Test Deployment

- Triggered when commit is pushed to `develop`
- Deploys container on Test server only

![Job2](screenshots/19-jenkins-job2-test.png)

---

## 🔹 Job3 – Production Deployment

- Triggered when commit is pushed to `master`
- Deploys container on Production server

![Job3](screenshots/20-jenkins-job3-prod.png)

---

# 📊 Build & Deployment Execution

![Build Console](screenshots/22-build-console-output.png)

---

# 🌍 Final Result

Application successfully deployed and accessible via browser from the respective environment.

![Final Deployment](screenshots/23-final-website-deployment.png)

---

# 🔄 DevOps Lifecycle Flow

GitHub Push  
↓  
Webhook  
↓  
Jenkins Pipeline  
↓  
Docker Build  
↓  
Branch-Based Deployment  
↓  
Test or Production Server  

---

# 🧠 Key Concepts Demonstrated

- Infrastructure Provisioning (EC2)
- Configuration Management (Ansible)
- Jenkins Master-Agent Setup
- Git Branching Strategy
- Webhook Integration
- CI/CD Pipeline Design
- Docker Containerization
- Automated Environment-Based Deployment

---

## 👨‍💻 Author

Nishant Mishra  
DevOps & Cloud Enthusiast
