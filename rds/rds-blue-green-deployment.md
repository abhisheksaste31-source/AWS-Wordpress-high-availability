# Amazon RDS Blue/Green Deployment

## 📌 Overview

Amazon RDS Blue/Green Deployment was used in this project to provide a safer approach for making database changes with minimal downtime.

The Blue environment represents the current production database, while the Green environment is used to prepare and validate the updated database environment before switching production traffic.


## 🏗️ Deployment Flow
-
                Production Application
                         |
                         v
                 Amazon RDS MySQL
                         |
                    BLUE Environment
                         |
                    Replication
                         |
                         v
                    GREEN Environment
                         |
                  Testing & Validation
                         |
                         v
                     Switchover
                         |
                         v
                 New Production DB
``
## 🔵 Blue Environment

The Blue environment represents the current production RDS database.

The WordPress application uses the Blue database during normal production operation.


WordPress EC2
      |
      v
Blue RDS MySQL
      |
      v
WordPress Database
`

## 🟢 Green Environment

The Green environment is the separate environment created from the Blue production environment.

It can be used to test database changes before making the Green environment the new production environment.

`
Blue RDS
    |
    | Replication
    v
Green RDS
    |
    v
Testing
``
## 🧪 Testing and Validation

Before the switchover, the Green environment can be validated to ensure that:

* Database connectivity is working
* Required database objects are available
* Application compatibility is verified
* Data is synchronized
* The WordPress application can work with the new database environment

---

## 🔄 Switchover

After successful validation, the Blue and Green environments can be switched.

``
Before Switchover

WordPress
    |
    v
BLUE RDS
Production


After Switchover

WordPress
    |
    v
GREEN RDS
Production

The Green environment becomes the production environment after the switchover.


## 🎯 Benefits

RDS Blue/Green Deployment provides:

* Safer database changes
* Pre-production testing
* Reduced deployment risk
* Faster rollback capability
* Minimal production disruption
* Better database deployment management

---

## 🛡️ Security Considerations

Database credentials and sensitive information were not stored in the GitHub repository.

Never commit:

* RDS passwords
* AWS access keys
* Secret keys
* Private keys
* Database connection secrets

---

## 📸 Project Evidence

Screenshots of the RDS Blue/Green Deployment configuration and switchover process can be added to:

```text
screenshots/rds-blue-green.png
```

---

## 📝 Conclusion

RDS Blue/Green Deployment was implemented as part of the AWS WordPress hosting project to demonstrate a safer database deployment strategy.

Combined with EC2, Auto Scaling, Application Load Balancer, Route 53, ACM, and Amazon RDS, this project demonstrates a scalable and highly available AWS-based WordPress architecture.
