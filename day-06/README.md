# Amazon Route 53 Notes

# What is Amazon Route 53?

Amazon Route 53 is AWS's highly available and scalable Domain Name System (DNS) web service.

It is used to:

* Register domain names
* Route internet traffic
* Perform health checks
* Manage DNS records

Route 53 helps users access applications using domain names instead of IP addresses.

Example:

```text
www.example.com
```

instead of

```text
54.123.45.67
```

---

# Why is Route 53 Important?

Humans remember names easily:

```text
google.com
amazon.com
github.com
```

Computers communicate using IP addresses:

```text
142.250.183.206
```

DNS converts domain names into IP addresses.

Route 53 provides DNS functionality in AWS.

---

# What is DNS?

DNS (Domain Name System) is like the phonebook of the internet.

Example:

```text
google.com
      │
      ▼
142.250.183.206
```

DNS translates domain names into IP addresses.

---

# Why is it Called Route 53?

The name comes from:

```text
Port 53
```

DNS uses Port 53 for communication.

---

# Domain Name

A domain name is a human-readable address.

Example:

```text
example.com
```

---

# Hosted Zone

A Hosted Zone stores DNS records for a domain.

Example:

```text
example.com
```

Hosted Zone contains:

* A Record
* CNAME Record
* MX Record
* TXT Record

---

# DNS Records

## A Record

Maps a domain name to an IPv4 address.

Example:

```text
www.example.com → 54.12.34.56
```

---

## AAAA Record

Maps a domain name to an IPv6 address.

Example:

```text
www.example.com → IPv6 Address
```

---

## CNAME Record

Maps one domain name to another.

Example:

```text
blog.example.com
      │
      ▼
example.com
```

---

## MX Record

Used for email services.

Example:

```text
gmail.com
```

uses MX records to route email.

---

## TXT Record

Stores text information.

Commonly used for:

* Domain Verification
* SPF Records
* DKIM Records

---

# Alias Record

AWS-specific feature.

Can point directly to:

* ELB
* CloudFront
* S3 Static Website
* API Gateway

Benefits:

* No extra DNS query charges
* Automatically tracks resource IP changes

---

# Routing Policies

Route 53 provides multiple routing policies.

---

## Simple Routing

Routes traffic to a single resource.

Example:

```text
example.com
    │
    ▼
EC2 Instance
```

---

## Weighted Routing

Distributes traffic based on percentages.

Example:

```text
Server A → 80%
Server B → 20%
```

Used for:

* A/B Testing
* Gradual Deployments

---

## Latency-Based Routing

Routes users to the lowest latency region.

Example:

```text
India User → Mumbai Region
USA User → Virginia Region
```

---

## Failover Routing

Routes traffic to a backup server if the primary server fails.

Example:

```text
Primary Server
      │
   Failure
      ▼
Backup Server
```

---

## Geolocation Routing

Routes traffic based on user location.

Example:

```text
India → Indian Website
USA → US Website
```

---

## Multi-Value Routing

Returns multiple healthy IP addresses.

Provides high availability.

---

# Route 53 Health Checks

Health Checks monitor resource availability.

Checks:

* HTTP
* HTTPS
* TCP

If resource becomes unhealthy:

```text
Route53
    │
    ▼
Redirect Traffic
```

---

# Route 53 Architecture

```text
User
 │
 ▼
Route 53
 │
 ▼
DNS Record
 │
 ▼
EC2 / ELB / S3
```

---

# Real-World Example

```text
www.mycompany.com
        │
        ▼
Route 53
        │
        ▼
Application Load Balancer
        │
        ▼
EC2 Instances
```

---

# Best Practices

* Use Alias Records for AWS Resources
* Enable Health Checks
* Use Failover Routing
* Use Multiple Availability Zones
* Enable Domain Locking

---
