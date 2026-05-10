# AWS Secure & Scalable Auto-Scaling Architecture

![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white)
![Security](https://img.shields.io/badge/Security-Cyber-blue?style=for-the-badge)
![Automation](https://img.shields.io/badge/Automation-CLI-green?style=for-the-badge)

## 📌 Project Overview

This project implements a highly available, secure, and elastically scalable web architecture on AWS. By leveraging an **EC2 Auto Scaling Group** within a custom **VPC**, the system is designed to handle fluctuating traffic patterns automatically while maintaining a robust security posture through **Defense-in-Depth** principles.

The core focus of this implementation is to demonstrate production-ready cloud engineering practices, including automated scaling, least-privilege access control, and secure remote management without the need for traditional SSH exposure.

---

## 🏗️ Architecture

The infrastructure is built upon several key AWS services, ensuring a resilient and secure environment:

- **Networking:** Custom VPC with Private Subnets for backend instances to minimize attack surface.
- **Traffic Management:** Route 53 (DNS) → AWS Certificate Manager (ACM) → Application Load Balancer (ALB).
- **Compute & Scaling:** EC2 Auto Scaling Group (ASG) across multiple Availability Zones.
- **Security:** IAM Roles (Least Privilege), Security Groups, NACLs, and Systems Manager (SSM) Session Manager.
- **Monitoring:** CloudWatch Metrics and Alarms for automated scaling triggers.

### Architecture Diagram
*(See `/Infastructure/AutoScaling Diagram.png`)*

---

## 🚀 Key Features

### 🛡️ Hardened Security Posture
- **Zero-Trust Management:** Utilizes **AWS Systems Manager (Session Manager)** instead of SSH (Port 22), eliminating public exposure of compute resources.
- **Least Privilege IAM:** Custom JSON policies crafted to provide the absolute minimum permissions required for each service role.
- **Encryption in Transit:** Enforced HTTPS using SSL/TLS certificates managed via ACM.
- **Network Isolation:** All application servers reside in private subnets, accessible only through the ALB.

### 📈 Dynamic Scalability & Elasticity
- **Self-Healing:** ASG automatically replaces unhealthy instances based on ALB health checks.
- **Load-Based Scaling:** CloudWatch alarms trigger scale-out/scale-in events based on CPU utilization and traffic patterns.

### ⚙️ Automation & CLI
- **Infrastructure Management:** Leveraged the **AWS CLI** for advanced configuration of IAM policies, ASG parameters, and resource management, moving beyond manual console interactions.

---

## 📂 Repository Structure

```text
.
├── Infastructure/              # Architecture diagrams and design documents
├── Screenshots/               # Visual verification of AWS resource configuration
│   ├── VPC.png                # Custom VPC configuration
│   ├── ALB.png                # Load Balancer setup
│   └── ...                    # Network and Subnet configurations
├── Video Demo/                # Demonstrations of the system in action
│   ├── Auto-Scaling.mp4       # Real-time scaling event demonstration
│   └── Load_Balancer.mp4      # Traffic distribution demo
├── IAM Policy.txt             # Custom JSON policy for Least Privilege access
├── outline.md                 # Project technical brief and objectives
└── README.md                  # Project documentation
```

---

## 🛠️ Tech Stack
- **Provider:** Amazon Web Services (AWS)
- **Services:** EC2, ASG, ALB, Route 53, ACM, S3, CloudFront, CloudWatch, SSM, IAM, VPC.
- **Tools:** AWS CLI, Markdown.

---

## 🧠 Lessons Learned
- Implementing **Least Privilege** is critical for mitigating lateral movement risks.
- **Auto Scaling** is as much about resilience and high availability as it is about performance.
- Moving from Console to **CLI/Automation** significantly improves deployment consistency and auditing.

---
