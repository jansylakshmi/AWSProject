# 🚀 AWS Scalable Web Application Architecture

A **production‑grade, secure, and cost‑optimized AWS architecture** built using core AWS services. This project demonstrates real‑world DevOps & Cloud best practices and is **GitHub + interview ready**.

---

## 🧭 Architecture Overview

✔ Highly available
✔ Secure (private networking + IAM)
✔ Scalable (Auto Scaling + ALB)
✔ Cost‑optimized
✔ Auditable & monitored

---

## 🏗️ Services Used

* **VPC** – Network isolation
* **EC2** – Application servers
* **ALB** – Traffic routing
* **Auto Scaling Group** – Dynamic scaling
* **RDS (MySQL / PostgreSQL)** – Database
* **S3** – Static assets & backups
* **IAM** – Secure access control
* **Secrets Manager** – Credential management
* **SQS** – Async message processing
* **CloudWatch** – Monitoring & alarms
* **CloudTrail** – Auditing
* **SNS** – Notifications

---

## 🌐 VPC Setup

* 1 VPC
* **2 Public Subnets** (ALB, NAT Gateway)
* **2 Private Subnets** (EC2, RDS)
* Internet Gateway for public access
* NAT Gateway for private subnet outbound traffic


## 🔐 IAM Roles

### EC2 Role Permissions

* AmazonS3FullAccess (or custom policy)
* CloudWatchAgentServerPolicy
* SecretsManagerReadWrite

```bash
aws iam create-role --role-name EC2-App-Role --assume-role-policy-document file://trust-policy.json
aws iam attach-role-policy --role-name EC2-App-Role --policy-arn arn:aws:iam::aws:policy/AmazonS3FullAccess
```

---

## 🖥️ EC2 + Auto Scaling

* EC2 instances launched in **private subnets**
* ALB in public subnets
* Auto Scaling based on CPU utilization



---

## ⚖️ Application Load Balancer

* Internet‑facing ALB
* Routes traffic to EC2 target group



---

## 🗄️ RDS Database

* MySQL / PostgreSQL
* Deployed in **private subnets**
* Security Group allows access **only from EC2 SG**



---

## 🔑 AWS Secrets Manager

* Stores DB credentials securely
* Retrieved at runtime by EC2


---

## 🪣 S3 Bucket

* Versioning enabled
* Used for static assets & backups

```bash
aws s3 mb s3://my-app-assets-bucket
aws s3api put-bucket-versioning \
--bucket my-app-assets-bucket \
--versioning-configuration Status=Enabled
```

---

## 📬 SQS Queue

* Handles asynchronous order processing



---

## 📊 CloudWatch Monitoring

* CPU > 80% alarms
* EC2 & ALB health checks
* Notifications via SNS

```bash
aws cloudwatch put-metric-alarm \
--alarm-name HighCPU \
--metric-name CPUUtilization \
--threshold 80
```

---

## 🧾 CloudTrail Auditing

* Tracks all AWS API calls
* Logs stored in secure S3 bucket



---

## 💰 Cost Optimization

* Auto Scaling to avoid idle instances
* S3 lifecycle → IA / Glacier
* Reserved Instances / Savings Plans
* Log retention policies
* Minimal NAT Gateway usage

---

## 🔁 Traffic Flow

1. User → ALB (Public Subnet)
2. ALB → EC2 (Private Subnet)
3. EC2 → RDS (Private Subnet)
4. EC2 → SQS (Async tasks)
5. Logs → CloudWatch
6. Events → SNS Alerts

---


