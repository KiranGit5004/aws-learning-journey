# VPC-Notes

# Amazon VPC (Virtual Private Cloud)

## What is VPC?

Amazon VPC (Virtual Private Cloud) is a logically isolated virtual network within AWS where you can launch AWS resources such as EC2 instances, databases, and load balancers.

A VPC provides complete control over:

* IP Addressing
* Subnets
* Route Tables
* Internet Access
* Security Settings

Think of a VPC as your own private data center inside AWS.

---

# Why Do We Need a VPC?

Without a VPC:

* Resources would not be isolated.
* Security would be difficult to manage.
* Network configuration would not be customizable.

With a VPC:

* Resources are isolated.
* Secure communication is possible.
* Custom networking can be implemented.

---

# AWS Region and Availability Zones

## Region

A Region is a geographical area where AWS has data centers.

Examples:

* ap-south-1 (Mumbai)
* us-east-1 (Virginia)
* eu-west-1 (Ireland)

---

## Availability Zone (AZ)

An Availability Zone is one or more data centers within a Region.

Example:

```text
ap-south-1
 ├── ap-south-1a
 ├── ap-south-1b
 └── ap-south-1c
```

High Availability is achieved by deploying resources across multiple AZs.

---

# VPC Components

## VPC

A logically isolated network inside AWS.

Example:

```text
10.0.0.0/16
```

---

## Subnets

A subnet is a smaller network inside a VPC.

Example:

```text
VPC
10.0.0.0/16

Public Subnet
10.0.1.0/24

Private Subnet
10.0.2.0/24
```

---

# Types of Subnets

## Public Subnet

A subnet that has a route to an Internet Gateway.

Resources can access the internet directly.

Examples:

* Web Servers
* Bastion Hosts
* Load Balancers

---

## Private Subnet

A subnet without direct internet access.

Examples:

* Databases
* Internal Applications

---

# CIDR Block

CIDR (Classless Inter-Domain Routing) defines the IP range.

Examples:

```text
10.0.0.0/16
```

Provides:

```text
65,536 IP Addresses
```

Example:

```text
10.0.1.0/24
```

Provides:

```text
256 IP Addresses
```

---

# Route Tables

Route Tables control network traffic.

Example:

| Destination | Target           |
| ----------- | ---------------- |
| 10.0.0.0/16 | Local            |
| 0.0.0.0/0   | Internet Gateway |

---

# Internet Gateway (IGW)

An Internet Gateway allows communication between a VPC and the Internet.

Without an IGW:

* No internet access
* Public IPs won't work

---

# NAT Gateway

A NAT Gateway allows private subnet resources to access the internet without exposing them to inbound internet traffic.

Use Cases:

* Software Updates
* Package Downloads
* OS Updates

---

# Security Groups

Security Groups act as instance-level firewalls.

Characteristics:

* Stateful
* Allow Rules Only
* Applied to Instances

Example:

Allow:

* SSH (22)
* HTTP (80)
* HTTPS (443)

---

# Network ACL (NACL)

A Network Access Control List is a stateless firewall that controls inbound and outbound traffic at the subnet level. 
It operates at the IP address level and can allow or deny traffic based on rules that you define. 
NACLs provide an additional layer of network security for your VPC.

Characteristics:

* Stateless
* Allow and Deny Rules
* Applied to Subnets

---

# Security Group vs NACL

| Security Group         | NACL           |
| ---------------------- | -------------- |
| Instance Level         | Subnet Level   |
| Stateful               | Stateless      |
| Allow Only             | Allow and Deny |
| Default Allow Outbound | Separate Rules |

---

# VPC Peering

VPC Peering enables communication between two VPCs.

Example:

```text
VPC-A
   │
   │ Peering
   │
VPC-B
```

Traffic remains within AWS network.

---

# VPC Endpoints

VPC endpoint use to connect AWS services privately, without the use of an internet gateway or NAT device.

Examples:

* S3
* DynamoDB

Benefits:

* More Secure
* Lower Latency

---

# Bastion Host

A Bastion Host is an EC2 instance in a Public Subnet used to access instances in Private Subnets.

Example:

```text
Internet
   │
Bastion Host
   │
Private EC2
```

---

# Elastic IP

Elastic IP is a static public IPv4 address.

Benefits:

* Persistent IP Address
* Easy Remapping

---

# AWS Direct Connect

AWS Direct Connect provides a dedicated private connection between On-Premises Infrastructure and AWS.

Benefits:

* Lower Latency
* Higher Bandwidth
* Secure Connectivity

---

# AWS VPN

AWS VPN securely connects On-Premises Networks to AWS over the Internet.

---

# VPC Flow Logs

VPC Flow Logs capture information about network traffic.

Use Cases:

* Monitoring
* Security Analysis
* Troubleshooting

---

# Real-World Architecture

```text
Internet
    │
Internet Gateway
    │
Public Subnet
    │
Load Balancer
    │
Private Subnet
    │
Application Servers
    │
Database Subnet
    │
RDS Database
```

---

### VPC with servers in private subnets and NAT

https://docs.aws.amazon.com/vpc/latest/userguide/vpc-example-private-subnets-nat.html

---
