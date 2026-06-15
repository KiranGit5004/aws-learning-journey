# Amazon Route 53 Interview Questions

## Q1. What is Amazon Route 53?

**Answer:**

Amazon Route 53 is AWS's scalable DNS service used for domain registration, DNS routing, and health checks.

---

## Q2. Why is it Called Route 53?

**Answer:**

Because DNS uses Port 53.

---

## Q3. What is DNS?

**Answer:**

DNS converts domain names into IP addresses.

---

## Q4. What is a Hosted Zone?

**Answer:**

A Hosted Zone contains DNS records for a domain.

---

## Q5. What is an A Record?

**Answer:**

Maps a domain name to an IPv4 address.

---

## Q6. What is an AAAA Record?

**Answer:**

Maps a domain name to an IPv6 address.

---

## Q7. What is a CNAME Record?

**Answer:**

Maps one domain name to another domain name.

---

## Q8. What is an MX Record?

**Answer:**

Used for email routing.

---

## Q9. What is a TXT Record?

**Answer:**

Stores text information used for verification and email security.

---

## Q10. What is an Alias Record?

**Answer:**

AWS-specific record that points directly to AWS resources like ELB, CloudFront, and S3.

---

## Q11. What is the Difference Between Alias and CNAME?

| Alias                | CNAME           |
| -------------------- | --------------- |
| AWS Specific         | Standard DNS    |
| Free Queries         | Charged Queries |
| Supports Root Domain | Does Not        |

---

## Q12. What is Simple Routing?

**Answer:**

Routes traffic to a single resource.

---

## Q13. What is Weighted Routing?

**Answer:**

Routes traffic based on assigned percentages.

---

## Q14. What is Latency-Based Routing?

**Answer:**

Routes users to the region with lowest latency.

---

## Q15. What is Failover Routing?

**Answer:**

Redirects traffic to a backup resource if the primary resource fails.

---

## Q16. What is Geolocation Routing?

**Answer:**

Routes traffic based on user location.

---

## Q17. What is Multi-Value Routing?

**Answer:**

Returns multiple healthy IP addresses.

---

## Q18. What are Route 53 Health Checks?

**Answer:**

Health checks monitor the health of endpoints and help Route 53 route traffic only to healthy resources.

---

## Q19. Can Route 53 Register Domains?

**Answer:**

Yes.

---

## Q20. What AWS Resources Commonly Integrate with Route 53?

**Answer:**

* EC2
* Elastic Load Balancer
* CloudFront
* S3 Static Website
* API Gateway
