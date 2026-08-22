# Amazon RDS MySQL

## 📌 Overview

Amazon RDS for MySQL is used as the managed database service for the WordPress application.

Instead of hosting MySQL directly on the EC2 application servers, the WordPress database is separated into Amazon RDS.

---

## 🏗️ Architecture

```text id="z8k6qm"
Application Load Balancer
          ↓
    Target Group
          ↓
   Auto Scaling Group
          ↓
      EC2 Instances
          ↓
       WordPress
          ↓
     Amazon RDS
          ↓
       MySQL
          ↓
   WordPress Database
```

---

## 🗄️ RDS Configuration

The RDS database provides the persistent database layer for WordPress.

The configuration includes:

* Amazon RDS for MySQL
* Database instance
* Database name
* Database user
* Database connectivity
* Security Group
* Backup configuration
* Database storage

> Database passwords and credentials are intentionally not stored in this repository.

---

## 🔐 Network & Security

The RDS instance should not be directly accessible from the public internet.

Database access is controlled using Security Groups.

```text id="2yhy3d"
Internet
    X
    |
    X
   RDS

EC2
 |
 └────→ RDS MySQL
```

The application EC2 instances are allowed to communicate with the RDS database on the required MySQL port.

---

## 🔗 WordPress Database Connection

WordPress is configured to use the RDS MySQL endpoint as its database server.

```text id="qqj5gn"
WordPress
    ↓
EC2
    ↓
RDS Endpoint
    ↓
MySQL
    ↓
WordPress Database
```

This keeps the application and database layers separated.

---

## 💾 Database Persistence

Amazon RDS provides managed database storage and database persistence independently from the EC2 application instances.

This means that application EC2 instances can be replaced or scaled without storing the primary WordPress database on the local EC2 filesystem.

---

## 🔄 RDS Blue/Green Deployment

RDS Blue/Green Deployment was also implemented in this project.

The detailed documentation is available here:

[RDS Blue/Green Deployment](rds-blue-green-deployment.md)

Deployment flow:

```text id="f6e5x4"
Blue RDS
   ↓
Replication
   ↓
Green RDS
   ↓
Testing
   ↓
Validation
   ↓
Switchover
```

---

## 🧪 Testing

The RDS configuration was validated by:

* Connecting the WordPress application to RDS
* Verifying database connectivity
* Accessing WordPress successfully
* Checking database operations
* Validating RDS Blue/Green deployment

---

## 📸 Screenshot

RDS screenshots can be added to:

```text id="e3d8d6"
screenshots/rds.png
```

Blue/Green deployment screenshot:

```text id="f1s6s0"
screenshots/rds-blue-green.png
```

---

## 🎯 Result

Amazon RDS for MySQL provides a managed and persistent database layer for the WordPress application.

The separation of the application and database layers improves scalability, maintainability, and reliability of the AWS architecture.

