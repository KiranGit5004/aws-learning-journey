# Amazon EC2 (Elastic Compute Cloud)

## What is Amazon EC2?

Amazon Elastic Compute Cloud (EC2) is a web service that provides secure, scalable, and resizable compute capacity in the cloud.

EC2 allows users to launch virtual servers within minutes and pay only for the resources they use.

### Benefits of EC2

* On-demand compute resources
* Highly scalable
* Pay-as-you-go pricing
* High availability
* Secure infrastructure
* Global deployment capability

---

# Why EC2 is Important

Before cloud computing, organizations had to:

* Purchase physical servers
* Maintain hardware
* Handle upgrades
* Manage data centers

With EC2:

* Servers can be created in minutes
* Infrastructure scales automatically
* No upfront hardware cost
* Resources are available globally

---

# EC2 Instance Basics

An EC2 Instance is a virtual server running in AWS.

## Components of an EC2 Instance

### 1. Amazon Machine Image (AMI)

AMI is a template used to launch EC2 instances.

Contains:

* Operating System
* Application Server
* Software Packages
* Configuration Settings

Examples:

* Amazon Linux
* Ubuntu
* Red Hat Enterprise Linux
* Windows Server

---

### 2. Instance Type

Defines:

* CPU
* Memory
* Storage
* Networking Capacity

Example:

* t2.micro
* t3.micro
* m5.large
* c5.large

---

### 3. Instance State

Possible EC2 States:

| State      | Description                  |
| ---------- | ---------------------------- |
| Pending    | Instance is launching        |
| Running    | Instance is active           |
| Stopping   | Instance is shutting down    |
| Stopped    | Instance is powered off      |
| Rebooting  | Instance is restarting       |
| Terminated | Instance permanently deleted |

---

# EC2 Instance Types

AWS provides multiple instance categories.

## 1. General Purpose

General Purpose instances are designed to deliver a balance of compute, memory, and network resources. They are suitable for a wide range of applications, including web servers, small databases, development and test environments, and more.

Examples:

* T Series
* M Series

Use Cases:

* Web Servers
* Small Databases
* Development Environments

---

## 2. Compute Optimized

Compute Optimized instances provide a higher ratio of compute power to memory. They excel in workloads that require high-performance processing such as batch processing, scientific modeling, gaming servers, and high-performance web servers.

Examples:

* C Series

Use Cases:

* Gaming Servers
* Scientific Modeling
* Batch Processing

---

## 3. Memory Optimized

Memory Optimized instances are designed to handle memory-intensive workloads. They are suitable for applications that require large amounts of memory, such as in-memory databases, real-time big data analytics, and high-performance computing.

Examples:

* R Series
* X Series

Use Cases:

* In-Memory Databases
* Analytics Platforms

---

## 4. Storage Optimized

Storage Optimized instances are optimized for applications that require high, sequential read and write access to large datasets. 
They are ideal for tasks like data warehousing, log processing, and distributed file systems.

Examples:

* I Series
* D Series

Use Cases:

* Data Warehousing
* Log Processing

---

## 5. Accelerated Computing

Accelerated Computing Instances typically come with one or more types of accelerators, such as Graphics Processing Units (GPUs),
Field Programmable Gate Arrays (FPGAs), or custom Application Specific Integrated Circuits (ASICs). 
These accelerators offload computationally intensive tasks from the main CPU, enabling faster and more efficient processing for specific workloads.

Examples:

* P Series
* G Series
* F Series

Use Cases:

* AI/ML
* Video Processing
* Scientific Computing

---

# EC2 Instance Families

| Family | Purpose                    |
| ------ | -------------------------- |
| C      | Compute Optimized          |
| D      | Dense Storage              |
| F      | FPGA                       |
| G      | GPU                        |
| Hpc    | High Performance Computing |
| I      | High I/O                   |
| Inf    | AWS Inferentia             |
| M      | General Purpose            |
| P      | GPU                        |
| R      | Memory Optimized           |
| T      | Burstable Performance      |
| Trn    | AWS Trainium               |
| U      | Ultra High Memory          |
| VT     | Video Transcoding          |
| X      | Extra Large Memory         |

---

# Additional Instance Capabilities

| Letter | Meaning           |
| ------ | ----------------- |
| a      | AMD Processor     |
| g      | AWS Graviton      |
| i      | Intel Processor   |
| d      | Instance Store    |
| n      | Network Optimized |
| e      | Extra Memory      |
| z      | High Performance  |

---

# Security Groups

Security Groups act as a virtual firewall.

Control:

* Inbound Traffic
* Outbound Traffic

Example:

Allow:

* SSH (22)
* HTTP (80)
* HTTPS (443)

---

# Key Pairs

Used for secure login into EC2 instances.

Consists of:

* Public Key
* Private Key

Linux Access:

```bash
ssh -i mykey.pem ec2-user@public-ip
```

Never share your private key.

---

# Launching an EC2 Instance

1. Open AWS Console
2. Navigate to EC2
3. Click Launch Instance
4. Select AMI
5. Select Instance Type
6. Configure Network Settings
7. Create Security Group
8. Create or Select Key Pair
9. Launch Instance

---

# Managing EC2 Instances

## Start Instance

Powers on a stopped instance.

## Stop Instance

Shuts down instance without deleting it.

## Reboot Instance

Restarts instance.

## Terminate Instance

Deletes instance permanently.

---

# Summary

* EC2 provides virtual servers in AWS.
* EC2 instances are launched using AMIs.
* Security Groups act as firewalls.
* Key Pairs provide secure access.
* Multiple pricing models are available.
* CloudWatch is used for monitoring.
* EC2 supports various workloads through different instance types.

---

