# LAMP Stack Configuration

## 📌 Overview

The WordPress application is hosted using the LAMP stack on Amazon EC2.

LAMP stands for:

* **L** — Linux
* **A** — Apache
* **M** — MySQL
* **P** — PHP

In this project, the WordPress database is hosted separately on **Amazon RDS for MySQL**.

---

## 🏗️ Architecture

```text id="l8m1xy"
Amazon EC2
     |
     ├── Linux
     |
     ├── Apache
     |
     ├── PHP
     |
     └── WordPress
             |
             ↓
       Amazon RDS MySQL
```

---

## 🐧 Linux

Linux provides the operating system environment for the WordPress application server.

The EC2 instance runs the Linux operating system and provides the environment required by Apache, PHP, and WordPress.

---

## 🌐 Apache

Apache is used as the web server.

Its main responsibilities include:

* Receiving HTTP/HTTPS application requests
* Serving WordPress files
* Processing PHP requests through the configured PHP environment
* Handling web traffic from the Application Load Balancer

---

## 🐘 PHP

PHP provides the runtime environment required by WordPress.

WordPress PHP files are processed by the PHP environment on the EC2 instance.

---

## 🗄️ MySQL

MySQL is the database engine used by WordPress.

For this project, the production MySQL database is hosted on:

**Amazon RDS for MySQL**

This separates the application layer from the database layer.

```text id="52c1v4"
EC2
 ↓
WordPress
 ↓
Amazon RDS
 ↓
MySQL
```

---

## 🌐 WordPress

WordPress is deployed on the EC2 application servers.

The application is accessed through:

```text id="w5w4fw"
User
 ↓
Route 53
 ↓
ALB
 ↓
Target Group
 ↓
EC2
 ↓
Apache
 ↓
PHP
 ↓
WordPress
 ↓
RDS MySQL
```

---

## 🔐 Security

The application and database layers are separated.

The RDS database should not be publicly accessible.

Security Groups control communication between:

```text id="bypg1h"
ALB → EC2
EC2 → RDS
```

---

## 📈 Scalability

The LAMP-based WordPress application runs on EC2 instances managed by an Auto Scaling Group.

This allows additional EC2 instances to be launched when required.

```text id="shqpyh"
Traffic Increase
      ↓
Auto Scaling
      ↓
New EC2 Instance
      ↓
LAMP + WordPress
      ↓
Target Group
```

---

## 🎯 Result

The LAMP stack provides the application environment required to host WordPress on Amazon EC2 while Amazon RDS for MySQL provides the managed database layer.

This architecture separates the application and database layers and supports scalability through the Auto Scaling Group.

