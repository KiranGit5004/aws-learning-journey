# Amazon EC2 Interview Questions and Answers

## Q1. What is Amazon EC2?

**Answer:**

Amazon EC2 (Elastic Compute Cloud) is a service that provides scalable virtual servers in the AWS cloud.

---

## Q2. What is an EC2 Instance?

**Answer:**

An EC2 Instance is a virtual machine running in AWS.

---

## Q3. What is an AMI?

**Answer:**

AMI (Amazon Machine Image) is a template used to launch EC2 instances. It contains the operating system, software, and configuration settings.

---

## Q4. What is the Difference Between AMI and EC2?

**Answer:**

| AMI                      | EC2                     |
| ------------------------ | ----------------------- |
| Template                 | Running Virtual Machine |
| Used to Launch Instances | Actual Compute Resource |

---

## Q5. What are Security Groups?

**Answer:**

Security Groups act as virtual firewalls that control inbound and outbound traffic to EC2 instances.

---

## Q6. What is a Key Pair?

**Answer:**

A Key Pair consists of a Public Key and a Private Key used for secure authentication to EC2 instances.

---

## Q7. What are EC2 Instance Types?

**Answer:**

Instance Types define CPU, memory, storage, and networking capacity.

Examples:

* t3.micro
* m5.large
* c5.large

---

## Q8. Name the Main EC2 Instance Categories.

**Answer:**

* General Purpose
* Compute Optimized
* Memory Optimized
* Storage Optimized
* Accelerated Computing

---

## Q9. What is the Difference Between Stop and Terminate?

**Answer:**

### Stop

* Instance can be restarted.
* Data on EBS remains.

### Terminate

* Instance is permanently deleted.

---

## Q10. What are On-Demand Instances?

**Answer:**

Instances billed per second or hour with no long-term commitment.

---

## Q11. What are Reserved Instances?

**Answer:**

Instances purchased with a 1-year or 3-year commitment for discounted pricing.

---

## Q12. What are Spot Instances?

**Answer:**

Unused AWS capacity available at significantly reduced prices.

---

## Q13. What is an Elastic IP?

**Answer:**

A static public IPv4 address that can be attached to an EC2 instance.

---

## Q14. How Do You Connect to a Linux EC2 Instance?

**Answer:**

Using SSH:

```bash
ssh -i key.pem ec2-user@public-ip
```

---

## Q15. What is CloudWatch?

**Answer:**

Amazon CloudWatch is a monitoring service used to monitor EC2 performance and AWS resources.

---

## Q16. What Happens When an Instance is Rebooted?

**Answer:**

The operating system restarts, but data remains intact.

---

## Q17. Can You Change an Instance Type After Launch?

**Answer:**

Yes. Stop the instance, change the instance type, and start it again.

---

## Q18. What is the Default SSH Port for Linux EC2?

**Answer:**

Port 22.

---

## Q19. What is the Default RDP Port for Windows EC2?

**Answer:**

Port 3389.
