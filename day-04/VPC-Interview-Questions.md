# Amazon VPC Interview Questions and Answers

## Q1. What is Amazon VPC?

**Answer:**

Amazon VPC is a logically isolated virtual network within AWS where resources can be launched securely.

---

## Q2. Why Do We Need a VPC?

**Answer:**

VPC provides isolation, security, IP management, and complete network control for AWS resources.

---

## Q3. What is a CIDR Block?

**Answer:**

CIDR defines the IP address range available in a VPC or subnet.

Example:

```text
10.0.0.0/16
```

---

## Q4. What is a Subnet?

**Answer:**

A subnet is a smaller network inside a VPC.

---

## Q5. What is the Difference Between Public and Private Subnet?

| Public Subnet       | Private Subnet            |
| ------------------- | ------------------------- |
| Has IGW Route       | No IGW Route              |
| Internet Accessible | No Direct Internet Access |
| Hosts Web Servers   | Hosts Databases           |

---

## Q6. What Makes a Subnet Public?

**Answer:**

A subnet becomes public when its Route Table contains a route to an Internet Gateway.

---

## Q7. What is an Internet Gateway?

**Answer:**

An Internet Gateway enables communication between a VPC and the Internet.

---

## Q8. What is a NAT Gateway?

**Answer:**

A NAT Gateway allows private subnet resources to access the Internet while preventing inbound Internet access.

---

## Q9. What is a Route Table?

**Answer:**

A Route Table contains rules that determine where network traffic is directed.

---

## Q10. What is the Difference Between Security Group and NACL?

| Security Group | NACL           |
| -------------- | -------------- |
| Stateful       | Stateless      |
| Instance Level | Subnet Level   |
| Allow Only     | Allow and Deny |

---

## Q11. What is VPC Peering?

**Answer:**

VPC Peering allows private communication between two VPCs using AWS internal networking.

---

## Q12. What is a VPC Endpoint?

**Answer:**

A VPC Endpoint allows private access to AWS services without using the Internet.

---

## Q13. What is a Bastion Host?

**Answer:**

A Bastion Host is a public EC2 instance used to securely access resources in private subnets.

---

## Q14. What is an Elastic IP?

**Answer:**

An Elastic IP is a static public IPv4 address in AWS.

---

## Q15. What is AWS Direct Connect?

**Answer:**

AWS Direct Connect provides a dedicated private network connection between AWS and an on-premises data center.

---

## Q16. What is AWS VPN?

**Answer:**

AWS VPN securely connects an on-premises network to AWS through the Internet.

---

## Q17. What are VPC Flow Logs?

**Answer:**

VPC Flow Logs capture information about network traffic entering and leaving network interfaces.

---

## Q18. Can a Subnet Exist Across Multiple Availability Zones?

**Answer:**

No. A subnet can exist in only one Availability Zone.

---

## Q19. Can One VPC Have Multiple Subnets?

**Answer:**

Yes. A VPC can have multiple public and private subnets.

---

## Q20. What are the Main Components of a VPC?

**Answer:**

* VPC
* Subnets
* Route Tables
* Internet Gateway
* NAT Gateway
* Security Groups
* NACLs
* VPC Endpoints
* VPC Peering
* Flow Logs
