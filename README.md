# Scalable AWS VPC Infrastructure with Auto Scaling & ALB

## 🚀 Why This Architecture?

Modern applications need to be **secure, highly available, and scalable**. This architecture provides a robust solution that separates public-facing components from internal compute resources, enables auto-healing and auto-scaling, and aligns with AWS best practices.

By placing EC2 instances in private subnets and exposing only the Load Balancer and Bastion Host publicly, we **minimize the attack surface** and ensure **controlled access** to internal resources. Load balancing and auto scaling provide elasticity, while NAT and routing configurations ensure secure internet access for backend instances.

This architecture is commonly used for:

- Web applications with multiple tiers (frontend/backend)
- Microservices deployed in isolated environments
- Secure infrastructure deployments in production environments

---

## 📘 Project Overview

This project demonstrates how to design and deploy a secure, scalable, and production-grade AWS infrastructure using:

- Custom VPC with public and private subnets across **two Availability Zones**
- **Auto Scaling Group** behind an **Application Load Balancer**
- Secure **Bastion Host** setup in public subnet for SSH access
- **NAT Gateway** for secure outbound internet access from private subnets
- **Security Groups** for strict traffic control

The design closely follows AWS best practices for secure and scalable VPC networking.

---

## 📏 Architecture Diagram


![Architecture](./architecture.png)
---

## 🛠️ Components Used

| Component                     | Description                                  |
| ----------------------------- | -------------------------------------------- |
| **VPC**                       | Custom VPC with isolated subnets             |
| **Public Subnet**             | Contains NAT Gateway and Bastion Host        |
| **Private Subnet**            | Hosts Auto Scaling Group EC2 instances       |
| **NAT Gateway**               | Enables internet access from private subnet  |
| **Application Load Balancer** | Manages and distributes incoming traffic across EC2 instances in different AZs |
| **Auto Scaling Group**        | Ensures high availability & dynamic scaling  |
| **Security Groups**           | Controls access between subnets and services |
| **Bastion Host**              | Acts as a secure jump server to access private instances via SSH |

---

## 📊 Key Features

- Multi-AZ **high availability**
- **Application Load Balancer** manages incoming traffic and routes it to healthy instances
- **Auto Scaling Group** maintains availability and scales based on demand
- **Private subnets** ensure backend instances are not publicly exposed
- **Bastion Host** allows controlled, auditable SSH access to private instances
- **NAT Gateway** allows private instances to access the internet securely
- **Security Groups** enforce least-privilege access control

---

## 🧠 What I Learned

- How to manually configure **VPC, subnets, IGW, route tables, and NAT**
- Why a **Bastion Host** is essential: It provides a secure entry point to access private EC2 instances without exposing them directly to the internet
- How **Application Load Balancer** works for distributing incoming traffic across AZs
- Debugging **SSH access and connectivity issues** through routing and firewall checks
- The role of **Security Groups** and **route tables** in controlling internal and external traffic

---

## 📅 Deployment Summary

- OS Used: **Ubuntu 22.04 LTS** (in EC2)
- Region: **ap-south-1** (Mumbai)
- VPC: 2 public + 2 private subnets across 2 AZs
- SSH via Bastion Host only
- Load balancer type: **Application Load Balancer (ALB)**
