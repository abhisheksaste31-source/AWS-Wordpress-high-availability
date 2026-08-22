# WordPress Deployment

## 📌 Overview

WordPress is deployed as the web application on Amazon EC2 instances using the LAMP stack.

The application layer is integrated with an Application Load Balancer, Auto Scaling Group, Route 53, AWS Certificate Manager, and Amazon RDS for MySQL.

---

## 🏗️ WordPress Architecture

```text id="5c6q8a"
Internet User
      ↓
Route 53
      ↓
ACM / HTTPS
      ↓
Application Load Balancer
      ↓
Target Group
      ↓
Auto Scaling Group
      ↓
EC2
      ↓
Apache + PHP
      ↓
WordPress
      ↓
Amazon RDS MySQL
```

---

## ⚙️ WordPress Environment

The WordPress application runs on the following environment:

* Linux
* Apache
* PHP
* WordPress
* Amazon RDS for MySQL

The EC2 instances act as the application servers while RDS provides the database layer.

---

## 🖥️ Application Server

WordPress is hosted on Amazon EC2.

The EC2 instance contains:

```text id="h3a7zp"
Linux
  ↓
Apache
  ↓
PHP
  ↓
WordPress
```

---

## 🗄️ Database Configuration

WordPress uses Amazon RDS for MySQL as its database backend.

```text id="2w6m9j"
WordPress
    ↓
RDS Endpoint
    ↓
MySQL
    ↓
WordPress Database
```

Database credentials are not stored in this repository.

---

## ⚖️ Load Balancing

The WordPress application is accessed through an Application Load Balancer.

The ALB distributes incoming requests across healthy EC2 instances registered in the Target Group.

```text id="q8k2mz"
ALB
 ↓
Target Group
 ├── EC2-1
 ├── EC2-2
 └── EC2-3
```

---

## 📈 Auto Scaling

The EC2 application layer is managed by an Auto Scaling Group.

The ASG can launch or terminate EC2 instances according to the configured scaling policy.

This allows the WordPress application to handle changes in traffic.

---

## 🌐 Domain and HTTPS

The website is accessed using a custom domain managed through Amazon Route 53.

AWS Certificate Manager provides the SSL/TLS certificate used by the ALB.

```text id="9b8r2m"
Custom Domain
      ↓
Route 53
      ↓
HTTPS
      ↓
ALB
      ↓
WordPress
```

---

## 🔄 RDS Blue/Green Deployment

RDS Blue/Green Deployment was implemented for safer database deployment.

```text id="k3x7pf"
Blue RDS
   ↓
Green RDS
   ↓
Testing
   ↓
Validation
   ↓
Switchover
```

Detailed documentation:

[RDS Blue/Green Deployment](../rds/rds-blue-green-deployment.md)

---

## 🧪 Testing

The WordPress deployment was validated using:

* WordPress website access
* Custom domain
* HTTPS
* ALB
* Target Group health checks
* EC2 instances
* RDS MySQL connectivity
* Auto Scaling
* RDS Blue/Green Deployment

---

## 📸 Screenshot

The WordPress website screenshot can be added to:

```text id="0z0d4v"
screenshots/wordpress.png
```

---

## 🎯 Result

The WordPress application was successfully deployed on AWS using a scalable and highly available architecture.

The application layer uses EC2, Apache, PHP, WordPress, ALB, Target Group, and Auto Scaling, while Amazon RDS provides the managed MySQL database.

Route 53 and ACM provide custom-domain DNS resolution and secure HTTPS access.

