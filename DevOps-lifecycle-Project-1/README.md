# 🚀 DevOps Lifecycle Implementation – Abode Software

## 📌 Project Overview

As a Sr. DevOps Engineer at Abode Software, I was tasked with implementing a complete DevOps lifecycle for the company’s product hosted on GitHub.

Product Repository:
https://github.com/hshar/website.git

The goal was to automate:

- Infrastructure configuration
- Software provisioning
- Git branching workflow
- CI/CD automation
- Docker containerization
- Environment-based deployment (Test & Production)

---

# 🏗 Infrastructure Architecture

Three EC2 instances were launched:

- **Master Server** – Jenkins + Ansible
- **Test Server**
- **Production Server**

![EC2 Overview](screenshots/01-ec2-instances-overview.png)

---

# ⚙ Configuration Management – Ansible

Ansible was used to automatically configure Test and Production servers.

## 🔹 Tasks Automated

- Installed Java
- Installed Docker
- Ensured consistent configuration across nodes

## 🔹 Files Included

- `inventory` – Contains Test & Prod server IPs
- `playbook.yml` – Installs required software
- `script.sh` (if applicable)

## 🔹 Execution Command

```bash
ansible-playbook -i inventory playbook.yml
```

## 🔹 Inventory File
![Inventory](screenshots/07-ansible-inventory-file.png)

## 🔹 Playbook Execution
![Playbook](screenshots/08-ansible-playbook-execution.png)

---

# 🧩 Jenkins Master–Agent Setup

- Jenkins installed on Master server
- Test & Prod machines configured as Jenkins nodes
- SSH-based agent communication configured

![Jenkins Dashboard](screenshots/11-jenkins-dashboard.png)
![Jenkins Nodes](screenshots/14-jenkins-all-nodes.png)

---

# 🌿 Git Workflow Strategy

Branch-based deployment logic implemented:

- `develop` branch → Deploy to **Test**
- `master` branch → Deploy to **Production**

Webhook configured to trigger Jenkins automatically on push.

![Fork](screenshots/15-github-forked-repository.png)
![Develop Branch](screenshots/16-github-develop-branch.png)
![Webhook](screenshots/17-github-webhook-configuration.png)

---

# 🐳 Docker Containerization

Application was containerized using a Dockerfile.

Base Image:
```
hshar/webapp
```

Application directory:
```
/var/www/html
```

## 🔹 Docker Commands Used in Pipeline

```bash
sudo docker build . -t img1
sudo docker run -itd --name cont1 -p 81:80 img1
```

---

# 🔁 CI/CD Pipeline Implementation

The DevOps lifecycle was implemented using three Jenkins jobs:

---

## 🔹 Job1 – Build

- Triggered on every commit
- Builds Docker image
- Prepares artifact for deployment

![Job1 Build](screenshots/18-jenkins-job1-build.png)

---

## 🔹 Job2 – Test Deployment

- Triggered when commit is pushed to `develop`
- Deploys container on Test server only

![Job2 Test](screenshots/19-jenkins-job2-test.png)

---

## 🔹 Job3 – Production Deployment

- Triggered when commit is pushed to `master`
- Deploys container on Production server

![Job3 Prod](screenshots/20-jenkins-job3-prod.png)

---

# 📊 Build & Deployment Execution

## 🔹 Console Output
![Build Console](screenshots/22-build-console-output.png)

---

# 🌍 Final Deployment Result

Application successfully deployed and accessible via browser from slave server.

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

# 🧠 Key Concepts Implemented

- Infrastructure Provisioning (EC2)
- Configuration Management (Ansible)
- Jenkins Master-Agent Architecture
- Git Branching Strategy
- Webhook Integration
- CI/CD Automation
- Docker Containerization
- Environment-Based Deployment Logic
- Automated Build & Deployment

---

# 🎯 Outcome

A fully automated DevOps lifecycle was implemented with:

✔ Zero manual deployments  
✔ Branch-based environment control  
✔ Automated testing workflow  
✔ Containerized application delivery  
✔ Infrastructure configuration automation  

---

# 📁 Project Structure

```
abode-devops-lifecycle-project/
├── ansible/
│   ├── inventory
│   ├── playbook.yml
│   └── script.sh
├── Dockerfile
├── screenshots/
└── README.md
```

---
