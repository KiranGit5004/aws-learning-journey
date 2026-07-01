# S3 Storage Classes

Amazon S3 provides multiple **Storage Classes** to help optimize storage costs based on how frequently data is accessed.

Instead of storing all objects in the same type of storage, you can choose the most cost-effective option depending on your workload.

For example:

* Frequently accessed data → S3 Standard
* Rarely accessed data → S3 Standard-IA
* Archived data → Glacier

Using the correct storage class helps reduce AWS costs significantly.

---

# S3 Storage Classes Overview

Amazon S3 currently provides the following storage classes:

* S3 Standard
* S3 Intelligent-Tiering
* S3 Standard-Infrequent Access (Standard-IA)
* S3 One Zone-Infrequent Access (One Zone-IA)
* S3 Glacier Instant Retrieval
* S3 Glacier Flexible Retrieval
* S3 Glacier Deep Archive

---

# 1. S3 Standard

S3 Standard is the default storage class.

It is designed for frequently accessed data.

### Features

* Low latency
* High throughput
* Multi-AZ storage
* 99.99% Availability
* 11 Nines Durability

### Best Use Cases

* Websites
* Mobile Applications
* Content Distribution
* Frequently Accessed Images
* Videos
* Documents

---

# 2. S3 Intelligent-Tiering

Amazon automatically moves objects between storage tiers based on access patterns.

No manual intervention is required.

### Benefits

* Cost optimization
* Automatic tier management
* No performance impact

### Best Use Cases

* Unknown access patterns
* Long-term business data
* User uploads

---

# 3. S3 Standard-Infrequent Access (Standard-IA)

Designed for data that is accessed less frequently but must be available immediately.

### Features

* Lower storage cost
* Retrieval charges apply
* Multi-AZ storage

### Best Use Cases

* Backup Files
* Disaster Recovery
* Old Project Files

---

# 4. S3 One Zone-Infrequent Access

Stores data in only one Availability Zone.

Lower storage cost than Standard-IA.

### Warning

If the Availability Zone fails, data may become unavailable.

### Best Use Cases

* Temporary backups
* Re-creatable data
* Secondary copies

---

# 5. S3 Glacier Instant Retrieval

Designed for archive data that still requires immediate access.

### Features

* Low storage cost
* Millisecond retrieval

### Best Use Cases

* Medical Records
* Archived Images
* Compliance Documents

---

# 6. S3 Glacier Flexible Retrieval

Previously called:

Amazon Glacier

Suitable for archive data that is accessed occasionally.

Retrieval time ranges from minutes to hours depending on the selected retrieval option.

### Best Use Cases

* Monthly Backups
* Financial Records
* Compliance Data

---

# 7. S3 Glacier Deep Archive

The lowest-cost storage class in Amazon S3.

Retrieval can take several hours.

### Best Use Cases

* Legal Documents
* Historical Data
* Long-Term Archives
* Regulatory Compliance

---

# Storage Class Comparison

| Storage Class              | Access Frequency  | Retrieval Time   | Cost     |
| -------------------------- | ----------------- | ---------------- | -------- |
| S3 Standard                | Frequent          | Milliseconds     | High     |
| Intelligent-Tiering        | Unknown           | Milliseconds     | Medium   |
| Standard-IA                | Rare              | Milliseconds     | Lower    |
| One Zone-IA                | Rare              | Milliseconds     | Lower    |
| Glacier Instant Retrieval  | Archive           | Milliseconds     | Very Low |
| Glacier Flexible Retrieval | Archive           | Minutes to Hours | Low      |
| Glacier Deep Archive       | Long-Term Archive | Hours            | Lowest   |

---

# Lifecycle Management

Lifecycle Management automatically moves objects between storage classes or deletes them after a specified period.

This helps reduce storage costs without manual intervention.

---

# Why Use Lifecycle Rules?

Benefits include:

* Reduce storage costs
* Automate storage management
* Delete unnecessary data
* Move older data to cheaper storage

---

# Lifecycle Workflow

```text
Upload Object
      │
      ▼
S3 Standard
      │
After 30 Days
      ▼
Standard-IA
      │
After 90 Days
      ▼
Glacier
      │
After 365 Days
      ▼
Delete Object
```

---

# Lifecycle Rule Components

A lifecycle rule can include:

* Rule Name
* Filter (Prefix/Tag)
* Transition Actions
* Expiration Actions

---

# Transition Rule

Moves objects between storage classes.

Example:

```text
After 30 Days
↓

Move to Standard-IA
```

Another example:

```text
After 90 Days
↓

Move to Glacier
```

---

# Expiration Rule

Automatically deletes objects after a specified number of days.

Example:

```text
Delete Backup Files

After 365 Days
```

Useful for:

* Temporary Files
* Logs
* Reports
* Test Data

---

# Real-World Lifecycle Example

Company stores server logs.

Lifecycle Policy:

```text
Day 0
↓

S3 Standard

↓

Day 30

↓

Standard-IA

↓

Day 90

↓

Glacier Flexible Retrieval

↓

Day 365

↓

Delete
```

No manual work is required.

---

# S3 Replication

Replication automatically copies objects from one bucket to another.

It improves:

* Disaster Recovery
* High Availability
* Compliance

Replication only works when **Versioning** is enabled on both source and destination buckets.

---

# Types of Replication

Amazon S3 supports:

* Same-Region Replication (SRR)
* Cross-Region Replication (CRR)

---

# Same-Region Replication (SRR)

Copies objects within the same AWS Region.

Example:

```text
Mumbai Region

Bucket-A
     │
     ▼
Bucket-B
```

### Use Cases

* Log Aggregation
* Development and Testing
* Internal Backup

---

# Cross-Region Replication (CRR)

Copies objects to another AWS Region.

Example:

```text
Mumbai Region
      │
Bucket-A
      │
      ▼
Singapore Region
      │
Bucket-B
```

### Benefits

* Disaster Recovery
* Business Continuity
* Regulatory Compliance

---

# Requirements for Replication

Before enabling replication:

* Versioning enabled on both buckets
* IAM Role with required permissions
* Destination bucket created
* Replication Rule configured

---

# S3 Event Notifications

Amazon S3 can automatically trigger AWS services when events occur.

Supported Events:

* Object Created
* Object Deleted
* Object Restored
* Replication Completed

---

# Supported Destinations

S3 can trigger:

* AWS Lambda
* Amazon SNS
* Amazon SQS

---

# Example

```text
Upload Image
      │
      ▼
S3 Bucket
      │
      ▼
Lambda Function
      │
      ▼
Resize Image
```

This is commonly used in serverless applications.

---

# Monitoring with Amazon CloudWatch

Amazon S3 integrates with CloudWatch.

CloudWatch helps monitor:

* Bucket Size
* Number of Objects
* Request Count
* Data Transfer
* Storage Usage

Benefits:

* Performance Monitoring
* Alerting
* Capacity Planning

---

# Access Logging

Server Access Logging records requests made to an S3 bucket.

Logs include:

* Request Time
* Source IP
* Request Type
* Response Code
* Requester Identity

Useful for:

* Auditing
* Security
* Troubleshooting

---

# CloudTrail Integration

AWS CloudTrail records API calls made to Amazon S3.

Examples:

* Create Bucket
* Delete Bucket
* Upload Object
* Delete Object
* Modify Bucket Policy

CloudTrail helps answer:

* Who performed the action?
* When was it performed?
* From which IP address?

---

# Real-World Example

An e-commerce company stores:

* Product Images
* Videos
* Customer Documents
* Backups

Storage Strategy:

```text
Product Images
↓

S3 Standard

↓

Old Images

↓

Standard-IA

↓

Archived Images

↓

Glacier

↓

Delete after 5 Years
```

This reduces storage costs while maintaining data availability.

---
