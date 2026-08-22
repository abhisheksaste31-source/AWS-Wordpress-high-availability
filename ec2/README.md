# Amazon EC2 Configuration

## 📌 Overview

Amazon EC2 instances are used as the application servers for hosting the WordPress website.

The EC2 instances run the LAMP stack and are managed by an Auto Scaling Group.

---

## 🖥️ EC2 Architecture

```text
Application Load Balancer
          ↓
     Target Group
          ↓
   Auto Scaling Group
          ↓
 ┌────────┴────────┐
 ↓                 ↓
EC2 Instance     EC2 Instance
 ↓                 ↓
LAMP              LAMP
 ↓                 ↓
WordPress         WordPress
```

---

## ⚙️ EC2 Configuration

The EC2 instances are configured with:

* Linux
* Apache
* PHP
* WordPress
* Required PHP extensions
* MySQL client/connectivity
* Security Group configuration

---

## 🔧 LAMP Stack

```text
Linux
  ↓
Apache
  ↓
PHP
  ↓
WordPress
```

The WordPress application uses Amazon RDS MySQL as its database backend.

---

## 🔐 Security

The EC2 instances are not intended to be directly accessed by public users.

Application traffic is routed through the Application Load Balancer.

```text
Internet
   ↓
ALB
   ↓
EC2
   ↓
RDS
```

Security Groups control the allowed traffic between the application and database layers.

---

## 📈 Auto Scaling

The EC2 instances are managed by an Auto Scaling Group.

The Auto Scaling Group can:

* Launch new EC2 instances
* Terminate unnecessary instances
* Maintain the configured capacity
* Improve application availability
* Handle increased traffic

---

## 🗄️ Database Connection

WordPress uses Amazon RDS for MySQL instead of storing the production database locally on the EC2 instance.

```text
EC2
 ↓
WordPress
 ↓
RDS MySQL
 ↓
WordPress Database
```

---

## 🧪 Validation

The EC2 configuration was validated using:

* Apache service
* PHP functionality
* WordPress website
* RDS database connectivity
* Target Group health checks
* Application Load Balancer

---

## 📸 Screenshot

EC2 screenshots can be added to:

```text
screenshots/ec2.png
```

---

## 🎯 Result

The EC2 application layer successfully hosts WordPress and integrates with the Application Load Balancer, Auto Scaling Group, and Amazon RDS MySQL database.

