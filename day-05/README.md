# Security-Groups-and-NACL-Notes

# AWS Security Using Security Groups and NACL

## Introduction

AWS provides multiple layers of security to protect cloud resources and data.

Two important network security components are:

* Security Groups (SG)
* Network Access Control Lists (NACL)

Both help control network traffic but operate at different levels.

---

# Security Groups

A Security Group acts as a virtual firewall for AWS resources such as EC2 instances.

Security Groups control:

* Inbound Traffic
* Outbound Traffic

They operate at the instance level.

---

# How Security Groups Work

When traffic reaches an EC2 instance:

1. AWS checks Security Group rules.
2. If traffic matches an Allow Rule → Traffic is allowed.
3. Otherwise → Traffic is denied.

Security Groups only support:

```text
ALLOW Rules
```

There are no DENY rules.

---

# Security Group Characteristics

* Instance Level Security
* Stateful
* Supports Allow Rules Only
* Multiple Security Groups can be attached to one EC2 instance
* Changes take effect immediately

---

# Example Security Group

| Type  | Port | Source    |
| ----- | ---- | --------- |
| SSH   | 22   | My IP     |
| HTTP  | 80   | 0.0.0.0/0 |
| HTTPS | 443  | 0.0.0.0/0 |

---

# Stateful Nature of Security Groups

Example:

```text
Inbound:
Allow SSH (22)
```

If a user connects:

```text
Laptop → EC2
```

The return traffic is automatically allowed.

No outbound rule is required.

This behavior is called:

```text
Stateful
```

---

# Network Access Control Lists (NACL)

NACL acts as a firewall at the subnet level.

It controls:

* Inbound Traffic
* Outbound Traffic

for all resources inside a subnet.

---

# How NACL Works

Every packet entering or leaving a subnet is checked against NACL rules.

Rules are evaluated from lowest number to highest number.

Example:

| Rule Number | Action |
| ----------- | ------ |
| 100         | Allow  |
| 200         | Deny   |

AWS evaluates Rule 100 first.

---

# NACL Characteristics

* Subnet Level Security
* Stateless
* Supports Allow and Deny Rules
* One NACL per Subnet
* Multiple Subnets can share a NACL

---

# Stateless Nature of NACL

Example:

Inbound Rule:

```text
Allow SSH Port 22
```

You must also create:

Outbound Rule:

```text
Allow Ephemeral Ports
```

Otherwise traffic will fail.

This behavior is called:

```text
Stateless
```

---

# Security Group vs NACL

| Feature         | Security Group      | NACL                     |
| --------------- | ------------------- | ------------------------ |
| Level           | Instance            | Subnet                   |
| Stateful        | Yes                 | No                       |
| Allow Rules     | Yes                 | Yes                      |
| Deny Rules      | No                  | Yes                      |
| Rule Processing | All Rules Evaluated | Lowest Rule Number First |
| Association     | EC2 Instance        | Subnet                   |

---

# Inbound and Outbound Traffic

## Inbound Traffic

Traffic entering AWS resources.

Examples:

* SSH
* HTTP
* HTTPS

---

## Outbound Traffic

Traffic leaving AWS resources.

Examples:

* Software Updates
* API Calls
* Database Connections

---

# Real-World Example

Architecture:

```text
Internet
    │
    ▼
Public Subnet
    │
    ▼
Web Server (EC2)
    │
    ▼
Private Subnet
    │
    ▼
Database Server
```

Security Groups:

Web Server:

* SSH (22)
* HTTP (80)
* HTTPS (443)

Database:

* MySQL (3306) from Web Server only

NACL:

* Allow Required Traffic
* Deny Unwanted Traffic

---

# Security Best Practices

* Follow Least Privilege Principle
* Allow only required ports
* Restrict SSH access to your IP
* Avoid 0.0.0.0/0 for sensitive ports
* Use Security Groups whenever possible
* Use NACLs as an additional security layer
* Regularly audit security rules

---
