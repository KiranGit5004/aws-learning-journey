# AWS Security Groups and NACL Interview Questions

## Q1. What is a Security Group?

**Answer:**

A Security Group is a virtual firewall that controls inbound and outbound traffic for AWS resources such as EC2 instances.

---

## Q2. What is a NACL?

**Answer:**

A Network Access Control List (NACL) is a subnet-level firewall that controls inbound and outbound traffic entering or leaving a subnet.

---

## Q3. What is the Difference Between Security Group and NACL?

| Security Group   | NACL           |
| ---------------- | -------------- |
| Instance Level   | Subnet Level   |
| Stateful         | Stateless      |
| Allow Only       | Allow and Deny |
| Multiple per EC2 | One per Subnet |

---

## Q4. What Does Stateful Mean?

**Answer:**

If inbound traffic is allowed, the return outbound traffic is automatically allowed.

---

## Q5. What Does Stateless Mean?

**Answer:**

Inbound and outbound traffic must be explicitly allowed separately.

---

## Q6. Can Security Groups Have Deny Rules?

**Answer:**

No. Security Groups only support Allow rules.

---

## Q7. Can NACLs Have Deny Rules?

**Answer:**

Yes. NACLs support both Allow and Deny rules.

---

## Q8. Which Layer Provides Better Granular Control?

**Answer:**

Security Groups provide more granular instance-level control.

---

## Q9. Can Multiple Security Groups Be Attached to an EC2 Instance?

**Answer:**

Yes.

---

## Q10. Can a Subnet Have Multiple NACLs?

**Answer:**

No. A subnet can have only one NACL associated with it.

---

## Q11. What Happens If No Security Group Rule Matches?

**Answer:**

Traffic is denied.

---

## Q12. How Are NACL Rules Evaluated?

**Answer:**

Rules are processed from the lowest rule number to the highest rule number.

---

## Q13. What is the Default Security Group Behavior?

**Answer:**

* Allows all outbound traffic
* Allows inbound traffic from resources in the same Security Group

---

## Q14. What is the Default NACL Behavior?

**Answer:**

Default NACL allows all inbound and outbound traffic.

---

## Q15. Which AWS Services Commonly Use Security Groups?

**Answer:**

* EC2
* RDS
* Elastic Load Balancer
* Lambda (inside VPC)

---

## Q16. Why Are Security Groups Called Virtual Firewalls?

**Answer:**

Because they filter network traffic entering and leaving AWS resources.

---

## Q17. What Port is Used for SSH?

**Answer:**

```text
22
```

---

## Q18. What Port is Used for HTTP?

**Answer:**

```text
80
```

---

## Q19. What Port is Used for HTTPS?

**Answer:**

```text
443
```

---

## Q20. Which Should Be Preferred First: Security Group or NACL?

**Answer:**

Security Groups should be the primary security mechanism. NACLs should be used as an additional security layer.
