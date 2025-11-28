# Scalable & Secure E-Commerce Web Application on AWS

## Overview

A production-ready, highly available, and cost‑optimized e-commerce application deployed on AWS using core cloud services and best practices.

## Architecture Summary

* **VPC** with public subnets (ALB) and private subnets (EC2, RDS)
* **Application Load Balancer** for traffic distribution
* **EC2 Auto Scaling Group** for high availability
* **RDS (MySQL/PostgreSQL)** for secure backend database
* **S3** for static files and product images
* **IAM** with least‑privilege roles (EC2, S3, CloudWatch, SSM)
* **Secrets Manager** for DB credentials
* **SQS** for asynchronous order processing
* **SNS** for application/health notifications
* **CloudWatch** for logs, metrics, alarms
* **CloudTrail** for full API auditing and compliance
* **Systems Manager (Session Manager)** for passwordless EC2 access
* **AWS Budgets** for cost alerts

## Responsibilities

* Built VPC networking (subnets, IGW, NAT, route tables)
* Configured EC2 instances and attached IAM roles
* Deployed Auto Scaling with CPU‑based policies
* Launched ALB & target groups for load distribution
* Set up RDS in private subnets and secured access via Secrets Manager
* Configured S3 bucket (versioning, bucket policy, encryption)
* Built CloudWatch alarms integrated with SNS
* Enabled CloudTrail logging into secured S3
* Implemented SQS queue for order processing workflows
* Used SSM for secure EC2 access without SSH keys
* Applied cost optimization (Auto Scaling + Budgets)

## Outcome

Delivered a secure, scalable, and fully monitored e-commerce cloud architecture suitable for production workloads.


<img width="953" height="776" alt="image" src="https://github.com/user-attachments/assets/26a9d0e5-1f9e-4e79-9e33-af5127c36aba" />

