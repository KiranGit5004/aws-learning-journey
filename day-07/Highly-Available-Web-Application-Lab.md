# Deploy a Highly Available Web Application on AWS Using VPC, ALB, and Auto Scaling

## Project Overview

This project demonstrates how to deploy a highly available web application on AWS using:

The architecture follows AWS best practices by placing application servers in private subnets and exposing only the Application Load Balancer to the internet.

---

# Architecture

![Architecture Diagram](screenshots/01-architecture.png)

```text
Users / Internet
        │
        ▼
Internet Gateway
        │
        ▼
Application Load Balancer
        │
   ┌────┴────┐
   ▼         ▼

AZ-A       AZ-B

Public     Public
Subnet     Subnet

│            │
├─ NAT GW    ├─ NAT GW
├─ Bastion   │
│            │
▼            ▼

Private     Private
Subnet      Subnet

│            │
└─ Auto Scaling Group
      │
      ▼
   EC2 Instances
```

---


# Step 1: Create VPC

Navigate to:

```text
VPC → Create VPC
```

Select:

```text
VPC and More
```

Configuration:

```text
Name: Production-VPC

IPv4 CIDR:
10.0.0.0/16

Availability Zones:
2

Public Subnets:
2

Private Subnets:
2

NAT Gateway:
1 per AZ (Recommended)
```

For lab purposes:

```text
Use Single NAT Gateway
```

Click:

```text
Create VPC
```

AWS automatically creates:

* VPC
* Internet Gateway
* Public Route Tables
* Private Route Tables
* Public Subnets
* Private Subnets
* NAT Gateway

---

# Step 2: Create Security Groups

## 2.1 ALB-SG

Inbound Rules:

| Type | Port | Source    |
| ---- | ---- | --------- |
| HTTP | 80   | 0.0.0.0/0 |

Outbound:

```text
All Traffic
```

---

## 2.2 Bastion-SG

Inbound Rules:

| Type | Port | Source |
| ---- | ---- | ------ |
| SSH  | 22   | My IP  |

Outbound:

```text
All Traffic
```

---

## 2.3 App-SG

Inbound Rules:

| Type | Port | Source     |
| ---- | ---- | ---------- |
| HTTP | 80   | ALB-SG     |
| SSH  | 22   | Bastion-SG |

Outbound:

```text
All Traffic
```

Important:

```text
Do NOT use 0.0.0.0/0 for App-SG HTTP access.
Only allow traffic from ALB-SG.
```

---

# Step 3: Launch Bastion Host

Configuration:

```text
Name:
Bastion-Host

AMI:
Amazon Linux 2023

Instance Type:
t2.micro

VPC:
Select Created VPC (eg:- Production-VPC)

Subnet:
Public Subnet A

Public IP:
Enabled

Security Group:
Bastion-SG
```

---

# Step 4: Create Launch Template

Navigate:

```text
EC2 → Launch Templates
```

Create:

```text
Name:
App-Template
```

Allow Auto Scaling guidance [checkbox]

Configuration:

```text
AMI:
Amazon Linux 2023

Instance Type:
t2.micro

Key-Pair:
in my case aws-key.pem

Security Group:
App-SG
```

User Data:

```bash
#!/bin/bash

dnf update -y
dnf install httpd -y

systemctl enable httpd
systemctl start httpd

echo "<h1>Application Server</h1>" > /var/www/html/index.html
```

---

# Step 5: Create Target Group

Navigate:

```text
EC2 → Target Groups
```

Configuration:

```text
Name:
Application-TG

Target Type:
Instances

Protocol:
HTTP

Port:
80
```

Health Check:

```text
Path: /
```

---

# Step 6: Create Application Load Balancer

Navigate:

```text
EC2 → Load Balancers → create ALB
```

Configuration:

```text
Name:
Application-ALB

Scheme:
Internet Facing

VPC:
Select Created VPC (eg:- Production-VPC)

Select:
Public Subnet A
Public Subnet B

Security Group:
ALB-SG
```

Listener:

```text
HTTP : 80
```

Forward to target groups
Select Target Group:

```text
Application-TG
```

---

# Step 7: Create Auto Scaling Group

Navigate:

```text
EC2 → Auto Scaling Groups
```

Configuration:

```text
Name:
Web-ASG

Launch Template:
App-Template
```

Select Your VPC:
eg:- Production-VPC

```text
Private Subnet A
Private Subnet B
```

Attach to an existing LB:

```text
Application-TG
```

Capacity:

```text
Desired: 2
Minimum: 2
Maximum: 4
```

Create ASG.

---

# Step 8: Register targets to target group after autoscalling group done.

Navigate:

```text
EC2 → Target Groupa
```

Select:

```text
Your Created Target Group
```

Go to:

```text
Targets → Register targets → Select Target Instances →  Include as pending below → Register pending targets.
```

# Step 9: Verify Deployment

Verify:

```text
2 EC2 Instances Running
```

Verify Target Group:

```text
Healthy Targets
```

Verify ALB:

```text
State: Active
```

---

# Step 10: Test Application

Copy ALB DNS Name.

Example:

```text
http://application-alb-xxxxxxxx.ap-south-1.elb.amazonaws.com
```

Expected Output:

```html
<h1>Application Server</h1>
```

---

# Step 11: Test Auto Scaling

Terminate one instance from the Auto Scaling Group.

Verify:

```text
ASG automatically launches a replacement instance.
```

Target Group should return to:

```text
Healthy
```

---

# Step 12: Verify High Availability

Even after terminating one instance:

```text
Application remains accessible through ALB.
```

This demonstrates:

* High Availability
* Multi-AZ Deployment
* Fault Tolerance

---

# Troubleshooting

## Target Group Unhealthy

Check:

```bash
curl localhost
sudo systemctl status httpd
sudo ss -tulpn | grep :80
```

Verify:

* HTTP running on port 80
* App-SG allows HTTP from ALB-SG
* Health Check Path = /

---

## SSH Permission Error

```bash
chmod 400 or 600 aws-key.pem
```

---

## Test Connectivity

From Bastion:

```bash
curl http://<PRIVATE-IP>
```

Expected:

```html
<h1>Application Server</h1>
```

---

From Internet (Chrome):

```bash
http://DNS-Name
```

Expected:

```html
<h1>Application Server</h1>
```
