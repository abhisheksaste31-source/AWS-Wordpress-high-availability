
# Amazon Route 53

## 📌 Overview

Amazon Route 53 is used as the DNS service for the WordPress website.

It maps the custom domain name to the Application Load Balancer, allowing users to access the WordPress application using a domain name instead of the ALB DNS name.

---

## 🌐 DNS Architecture

```text id="y5r3u7"
User
 ↓
Custom Domain
 ↓
Amazon Route 53
 ↓
Application Load Balancer
 ↓
Target Group
 ↓
EC2
 ↓
WordPress
```

---

## ⚙️ Route 53 Configuration

A hosted zone is used to manage DNS records for the domain.

The DNS configuration points the website domain to the Application Load Balancer.

```text id="v2q8xj"
Domain
   ↓
Route 53 Hosted Zone
   ↓
DNS Record
   ↓
Application Load Balancer
```

---

## 🔗 ALB Integration

The Route 53 DNS record directs users to the Application Load Balancer.

The ALB then forwards the request to the appropriate healthy EC2 instance through the Target Group.

```text id="8y3nqv"
Route 53
   ↓
ALB
   ↓
Target Group
   ↓
Healthy EC2
   ↓
WordPress
```

---

## 🔐 HTTPS Integration

Route 53 works together with AWS Certificate Manager and the Application Load Balancer to provide HTTPS access.

```text id="8tqjxr"
User
 ↓
Domain
 ↓
Route 53
 ↓
HTTPS
 ↓
ALB
 ↓
EC2
```

---

## 🧪 Testing

The Route 53 configuration was validated by:

* Accessing the website using the custom domain
* DNS resolution
* HTTPS access
* Application Load Balancer connectivity
* WordPress website availability

---

## 📸 Screenshot

Route 53 screenshots can be added to:

```text id="m6q8zp"
screenshots/route53.png
```

---

## 🎯 Result

Route 53 provides DNS resolution for the WordPress website and directs users to the Application Load Balancer.

This creates a clean architecture where users access the application through a custom domain.
