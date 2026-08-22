# 🚀 Highly Available WordPress Hosting on AWS

A highly available and scalable WordPress website hosted on AWS using a **LAMP stack**, **Amazon EC2**, **Amazon RDS for MySQL**, **Application Load Balancer**, **Target Group**, **Auto Scaling Group**, **Amazon Route 53**, and **AWS Certificate Manager (ACM)**.

---

## 📌 Project Overview

This project demonstrates the deployment of a production-style WordPress website on AWS with scalability, load balancing, database separation, DNS management, and HTTPS security.

The WordPress application runs on EC2 instances using the LAMP stack, while the WordPress database is hosted on Amazon RDS for MySQL.

Application traffic is distributed through an Application Load Balancer, and Auto Scaling automatically manages EC2 instances based on demand.

---

## 🏗️ AWS Architecture

```text
                         🌐 Internet
                              |
                              v
                       Amazon Route 53
                         DNS Resolution
                              |
                              v
                    AWS Certificate Manager
                         SSL / HTTPS
                              |
                              v
              Application Load Balancer (ALB)
                              |
                              v
                       Target Group
                         /       \
                        /         \
                       v           v
                  EC2 Instance  EC2 Instance
                     LAMP          LAMP
                  WordPress     WordPress
                       \           /
                        \         /
                         \       /
                          v     v
                       Amazon RDS
                       MySQL Database

                  Auto Scaling Group
                  ↕ Automatically manages
                    EC2 instances
```

---

## ☁️ AWS Services Used

| AWS Service               | Purpose                                            |
| ------------------------- | -------------------------------------------------- |
| Amazon EC2                | Hosts the WordPress application                    |
| Apache                    | Web server                                         |
| PHP                       | WordPress runtime                                  |
| MySQL                     | Database engine                                    |
| Amazon RDS                | Managed MySQL database                             |
| Application Load Balancer | Distributes incoming traffic                       |
| Target Group              | Registers EC2 instances and performs health checks |
| Auto Scaling Group        | Automatically scales EC2 instances                 |
| Amazon Route 53           | DNS management                                     |
| AWS Certificate Manager   | SSL/TLS certificate                                |
| Security Groups           | Network-level access control                       |

---

## 🔄 Request Flow

```text
User
  ↓
Route 53
  ↓
HTTPS
  ↓
Application Load Balancer
  ↓
Target Group
  ↓
Healthy EC2 Instance
  ↓
Apache + PHP + WordPress
  ↓
Amazon RDS MySQL
```

---

## ⚙️ LAMP Stack

The application uses the following LAMP components:

* **Linux** – Operating system for EC2
* **Apache** – Web server
* **MySQL** – Database
* **PHP** – WordPress application runtime

---

## 🚀 Key Features

* ✅ WordPress hosted on Amazon EC2
* ✅ LAMP stack configuration
* ✅ Amazon RDS MySQL database
* ✅ Application Load Balancer
* ✅ Target Group with health checks
* ✅ Auto Scaling Group
* ✅ Route 53 DNS configuration
* ✅ HTTPS using AWS Certificate Manager
* ✅ Scalable EC2 architecture
* ✅ Managed database using Amazon RDS
* ✅ High availability architecture

---

## 🔐 Security

Security Groups were configured to control traffic between the AWS resources.

The architecture separates the application and database layers:

```text
Internet
   ↓
ALB
   ↓
EC2
   ↓
RDS
```

The RDS database is accessed by the application layer rather than directly from the public internet.

> ⚠️ Never commit AWS credentials, private keys, database passwords, `.env` files, or other secrets to this repository.

---

## 📊 Scalability

The Auto Scaling Group allows the application layer to scale according to workload.

```text
Low Traffic
    ↓
Minimum EC2 Instances
    ↓
Traffic Increases
    ↓
Auto Scaling
    ↓
Additional EC2 Instances
    ↓
ALB distributes traffic
```

---

## 🧪 Testing

The deployment was tested using:

* WordPress website access
* HTTPS access
* Application Load Balancer
* Target Group health checks
* EC2 instances
* RDS MySQL connectivity
* Auto Scaling configuration
* Route 53 DNS resolution

---

## 📸 Project Screenshots

Screenshots of the AWS infrastructure and WordPress website will be added to the repository.

Planned screenshots:

* AWS Architecture
* EC2 Instances
* RDS MySQL
* Application Load Balancer
* Target Group
* Auto Scaling Group
* Route 53
* ACM Certificate
* WordPress Website

---

## 🎯 Learning Outcomes

Through this project, I gained practical experience with:

* AWS EC2
* AWS RDS
* LAMP stack
* Application Load Balancer
* Target Groups
* Auto Scaling
* Route 53
* AWS Certificate Manager
* HTTPS
* Security Groups
* High Availability
* Cloud infrastructure architecture

---

## 👨‍💻 Author

**Abhishek Saste**

Cloud & DevOps Enthusiast

GitHub: [abhisheksaste31-source](https://github.com/abhisheksaste31-source)

---

## ⭐ Project

If you find this project useful, consider giving the repository a ⭐ star.

