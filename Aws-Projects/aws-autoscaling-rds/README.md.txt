# 🚀 AWS Capstone Project 1  
## AWS Auto Scaling Web Application with RDS Integration

---

## 📌 Project Overview

This project demonstrates the deployment of a highly available and scalable PHP-based web application on Amazon Web Services (AWS).

The architecture includes:
- Application Load Balancer
- Auto Scaling Group with EC2 instances
- Amazon RDS (MySQL) database
- Public and Private Subnet separation
- Secure communication using Security Groups

The infrastructure ensures scalability, high availability, and secure database connectivity.

---

## 🏗️ Architecture Diagram

![Architecture Diagram](screenshots/00-architecture-diagram.png)

---

## 🎯 Objective

To build a scalable, highly available, and cost-efficient cloud architecture for a PHP web application using AWS EC2, Auto Scaling, and RDS.

---

## 🛠️ AWS Services Used

- Amazon EC2
- Amazon RDS (MySQL)
- Auto Scaling Group
- Application Load Balancer
- VPC
- Security Groups
- Internet Gateway

---

# ⚙️ Implementation Steps

---

## 1️⃣ Launched an EC2 Instance

- Amazon Linux instance launched
- Apache & PHP configured

![EC2 Launch](screenshots/01-ec2-launch.png)

---

## 2️⃣ Created an RDS Instance

- Engine: MySQL
- Database Name: `intel`
- Secure connectivity configured

![RDS Creation](screenshots/02-rds-creation.png)

---

## 3️⃣ Website Folder Setup

- Created folder in `/home/ubuntu`
- Removed default `index.html`
- Created `index.php`

![Website Folder Setup](screenshots/03-website-folder-setup.png)

---

## 4️⃣ Created Database & Table

- Database: `intel`
- Table: `data`

![Database Creation](screenshots/04-database-table-creation.png)

---

## 5️⃣ Added Database Connection in index.php

- Configured RDS endpoint
- Updated DB credentials in PHP file

![DB Configuration](screenshots/05-db-connection-config.png)

---

## 6️⃣ Website Output

- Successfully connected EC2 to RDS
- Dynamic content displayed

![Website Output](screenshots/06-website-output.png)

---

## 7️⃣ Created Auto Scaling Group from Existing EC2

- Created AMI from configured EC2
- Launch template created
- Auto Scaling Group configured (Min: 2 instances)

![Auto Scaling Group Creation](screenshots/07-auto-scaling-group-creation.png)

---

## 8️⃣ Auto Scaling Result

- Multiple EC2 instances running
- High availability achieved

![Auto Scaling Result](screenshots/08-auto-scaling-result.png)

---

# 🔐 Security Implementation

- Security Groups configured with least privilege
- HTTP (80) allowed to Load Balancer
- HTTP allowed from Load Balancer to EC2
- MySQL (3306) allowed from EC2 to RDS only
- RDS placed in private subnets

---

# 📈 Key Features

✔ High Availability across Availability Zones  
✔ Automatic Scaling  
✔ Secure Database Integration  
✔ Fault Tolerant Architecture  
✔ Cost-efficient cloud deployment  

---

## ⚠️ Project Status

This infrastructure was successfully deployed and tested in AWS.  
All resources were later terminated to prevent unnecessary AWS charges.

---

## 👨‍💻 Author

Nishant Mishra  
Cloud & DevOps Enthusiast