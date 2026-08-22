# AWS Certificate Manager (ACM)

## 📌 Overview

AWS Certificate Manager (ACM) is used to provide an SSL/TLS certificate for the WordPress website.

The certificate enables secure HTTPS communication between users and the Application Load Balancer.

---

## 🔐 HTTPS Architecture

```text id="7d6s2p"
User
 ↓
HTTPS :443
 ↓
Application Load Balancer
 ↓
Target Group
 ↓
EC2
 ↓
WordPress
```

The SSL/TLS certificate is associated with the Application Load Balancer.

---

## ⚙️ ACM Configuration

The ACM certificate is used for the custom domain.

The certificate must be issued and validated before it can be associated with the HTTPS listener on the Application Load Balancer.

```text id="3i7f1r"
Custom Domain
      ↓
AWS Certificate Manager
      ↓
SSL/TLS Certificate
      ↓
ALB HTTPS Listener
      ↓
Target Group
      ↓
EC2
```

---

## 🌐 Route 53 Integration

Route 53 provides DNS resolution for the custom domain while ACM provides the SSL/TLS certificate.

```text id="f6r2z8"
Route 53
   ↓
Custom Domain
   ↓
ALB
   ↑
ACM Certificate
```

---

## 🔄 HTTP to HTTPS

The Application Load Balancer can be configured to redirect HTTP traffic to HTTPS.

```text id="2yq6sx"
HTTP :80
   ↓
Redirect
   ↓
HTTPS :443
   ↓
ALB
   ↓
WordPress
```

This ensures users access the website securely using HTTPS.

---

## 🛡️ Security Benefits

HTTPS provides:

* Encrypted communication
* Protection against traffic interception
* Secure website access
* Browser trust through a valid certificate
* Secure communication between users and the load balancer

---

## 🧪 Testing

The ACM and HTTPS configuration was validated by:

* Opening the website using HTTPS
* Checking the SSL certificate
* Verifying the ALB HTTPS listener
* Testing HTTP to HTTPS redirection
* Confirming the WordPress website loads securely

---

## 📸 Screenshot

ACM screenshots can be added to:

```text id="7m0s3e"
screenshots/acm.png
```

---

## 🎯 Result

AWS Certificate Manager provides the SSL/TLS certificate required for secure HTTPS access to the WordPress application.

Combined with Route 53 and the Application Load Balancer, it provides a secure custom-domain based entry point for the application.

