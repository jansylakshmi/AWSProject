# ⚙️ Implementation Overview

## ✅ VPC Setup

* Create **2 public** and **2 private** subnets.
* Attach **Internet Gateway (IGW)** for public subnet traffic.
* Configure **NAT Gateway** to allow private subnets outbound internet access.

---

## ✅ IAM Roles

* Attach **S3 access policies** to EC2 role for reading/writing objects.
* Assign **CloudWatch monitoring roles** for metrics and logs.

---

## ✅ EC2 & Auto Scaling

* Launch EC2 instances in **private subnets** for security.
* Place **ALB (Application Load Balancer)** in public subnets to route traffic.
* Configure **Auto Scaling Group** for dynamic scaling based on CPU/memory.

---

## ✅ RDS Database

* Deploy **MySQL/PostgreSQL** in private subnets.
* Restrict DB access to only the EC2 application's security group.

---

## ✅ Secrets Manager

* Store database credentials securely.
* Application retrieves secrets directly from **AWS Secrets Manager** at runtime.

---

## ✅ S3 Bucket

* Enable **versioning** for product images and static assets.
* Set appropriate **bucket policies** to limit access to IAM roles.

---

## ✅ CloudWatch Monitoring

* Create alarms for:

  * **CPU > 80%**
  * Status or health check failures
* Integrate alarms with **SNS** for email/SMS notifications.

---

## ✅ CloudTrail Auditing

* Enable CloudTrail across the AWS account.
* Store all API logs in a **secure S3 bucket**.

---

## ✅ SQS Queue

* Use SQS to handle **asynchronous order processing** between front-end and back-end services.

---

## ✅ Cost Optimization

* Configure **AWS Budgets** for monthly spending alerts.
* Use Auto Scaling properly and apply **Spot Instances** for dev/test workloads.

---

