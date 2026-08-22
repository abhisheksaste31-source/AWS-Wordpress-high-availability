# Application Load Balancer & Target Group

## 📌 Overview

An **Application Load Balancer (ALB)** is used to distribute incoming WordPress traffic across multiple EC2 instances.

The ALB works together with a **Target Group** and **Auto Scaling Group** to provide load distribution and application availability.

---

## 🏗️ Architecture

```text
Internet Users
      ↓
Route 53
      ↓
HTTPS
      ↓
Application Load Balancer
      ↓
Target Group
      ↓
┌──────────────┬──────────────┐
↓              ↓
EC2-1          EC2-2
WordPress      WordPress
```

---

## ⚖️ Application Load Balancer

The ALB is configured as the public entry point for the WordPress application.

It receives incoming HTTP/HTTPS requests and forwards them to healthy targets in the Target Group.

### Responsibilities

* Receive application traffic
* Distribute requests across EC2 instances
* Perform routing
* Integrate with HTTPS
* Forward traffic to healthy targets

---

## 🎯 Target Group

The Target Group contains the EC2 instances running the WordPress application.

The ALB forwards requests to registered healthy targets.

### Health Checks

Health checks are used to determine whether an EC2 instance is available to receive traffic.

```text
ALB
 ↓
Target Group
 ↓
Health Check
 ↓
Healthy EC2 → Receive Traffic
Unhealthy EC2 → Traffic Not Sent
```

---

## 🔐 HTTPS

HTTPS traffic is terminated at the Application Load Balancer using an SSL/TLS certificate from **AWS Certificate Manager (ACM)**.

```text
User
 ↓
HTTPS :443
 ↓
ALB
 ↓
Target Group
 ↓
EC2
```

---

## 📈 Integration with Auto Scaling

The Target Group works with the Auto Scaling Group.

When Auto Scaling launches a new EC2 instance, the instance can be registered with the Target Group.

When an instance is removed, it is removed from the active target pool.

```text
Auto Scaling Group
        ↓
EC2 Instances
        ↓
Target Group
        ↓
Application Load Balancer
```

---

## 🧪 Testing

The ALB configuration was validated using:

* ALB DNS endpoint
* HTTPS access
* Target Group health status
* EC2 target registration
* WordPress website access
* Traffic distribution across instances

---

## 📸 Screenshot

ALB screenshots can be added to:

```text
screenshots/alb.png
```

Target Group screenshots can be added to:

```text
screenshots/target-group.png
```

---

## 🎯 Result

The Application Load Balancer successfully provides a single entry point for the WordPress application and distributes traffic across healthy EC2 instances.

Combined with the Auto Scaling Group and Target Group, the architecture provides a scalable and highly available application layer.
