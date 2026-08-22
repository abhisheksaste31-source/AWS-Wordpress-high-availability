# Auto Scaling Group

## 📌 Overview

The **Amazon EC2 Auto Scaling Group (ASG)** is used to maintain and automatically manage the required number of WordPress application servers.

It works together with the Application Load Balancer and Target Group to provide scalability and high availability.

---

## 🏗️ Architecture

```text id="x7j3nq"
                    Application Load Balancer
                              |
                              v
                        Target Group
                              |
                              v
                    Auto Scaling Group
                       /      |      \
                      ↓       ↓       ↓
                    EC2-1   EC2-2   EC2-3
                      |       |       |
                  WordPress WordPress WordPress
```

---

## ⚙️ Auto Scaling Configuration

The Auto Scaling Group manages the EC2 instances used by the WordPress application.

The ASG configuration can include:

* Minimum capacity
* Desired capacity
* Maximum capacity
* Scaling policies
* Launch Template
* Target Group integration
* Health checks

---

## 📈 Scaling

When application demand increases, the Auto Scaling Group can launch additional EC2 instances.

```text id="72sk7v"
Increased Traffic
       ↓
Scaling Policy
       ↓
Auto Scaling Group
       ↓
New EC2 Instance
       ↓
Target Group
       ↓
ALB
```

When demand decreases, unnecessary instances can be terminated according to the configured scaling policy.

---

## 🩺 Health Checks

The Auto Scaling Group uses health checks to identify unhealthy EC2 instances.

```text id="g3qax8"
EC2 Instance
      ↓
Health Check
      ↓
Healthy
   ↓
Remain in ASG

Unhealthy
   ↓
Replace Instance
```

---

## ⚖️ Load Balancer Integration

The Auto Scaling Group is associated with the Application Load Balancer's Target Group.

New instances launched by the ASG can be registered with the Target Group and begin receiving traffic after passing health checks.

```text id="d8e0nr"
Auto Scaling Group
        ↓
Launch EC2
        ↓
Target Group
        ↓
Health Check
        ↓
ALB
```

---

## 🚀 Benefits

Using Auto Scaling provides:

* Automatic EC2 scaling
* Improved application availability
* Fault tolerance
* Better handling of traffic spikes
* Automatic replacement of unhealthy instances
* Integration with Application Load Balancer

---

## 🧪 Testing

The Auto Scaling configuration was validated using:

* EC2 instance count
* Target Group health status
* Scaling policy
* Load testing / increased traffic
* Launch of additional instances
* ALB traffic distribution

---

## 📸 Screenshot

Auto Scaling screenshots can be added to:

```text id="6o7g4f"
screenshots/autoscaling.png
```

---

## 🎯 Result

The Auto Scaling Group provides a scalable application layer for the WordPress deployment.

Combined with the Application Load Balancer and Target Group, it allows the WordPress application to automatically manage EC2 capacity based on the configured scaling requirements.

