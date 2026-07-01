# Amazon S3 (Simple Storage Service) 

## Introduction

Amazon Simple Storage Service (Amazon S3) is one of the core storage services provided by Amazon Web Services (AWS). It offers highly scalable, secure, durable, and cost-effective object storage for storing and retrieving any amount of data from anywhere in the world.

Unlike traditional storage systems where data is stored on a local disk or server, Amazon S3 stores data as **objects** inside **buckets**. It is designed to provide **99.999999999% (11 nines) durability** and high availability, making it suitable for storing critical business data.

Amazon S3 is used by individuals, startups, enterprises, and government organizations for various workloads such as website hosting, backups, disaster recovery, big data analytics, media storage, application hosting, and log management.

---

# What is Amazon S3?

Amazon S3 (Simple Storage Service) is an **object storage service** that allows users to store, retrieve, and manage data over the internet.

Instead of storing files on a physical hard drive, S3 stores data in **objects**, and those objects are organized inside **buckets**.

Each object consists of:

* File (Data)
* Object Key (Unique Name)
* Metadata

S3 provides virtually unlimited storage capacity, allowing you to store anything from a few bytes to multiple terabytes of data.

---

# What are S3 buckets?

S3 buckets are containers for storing objects (files) in Amazon S3. Each bucket has a unique name globally across all of AWS. You can think of an S3 bucket as a top-level folder that holds your data.

---

# Why Use Amazon S3?

Amazon S3 is designed to solve common storage challenges faced by businesses and developers.

Some of the primary reasons for using Amazon S3 are:

* Store unlimited amounts of data
* Securely store important business files
* Host static websites
* Backup and restore applications
* Store images, videos, and documents
* Archive old data at low cost
* Store application logs
* Build Data Lakes for Analytics and Machine Learning
* Disaster Recovery (DR)

---

# Key Features of Amazon S3

## 1. Highly Scalable

Amazon S3 automatically scales to store virtually unlimited amounts of data without any manual intervention.

Example:

A company starts with 10 GB of data today and grows to 500 TB after five years.

No storage expansion or server upgrades are required.

---

## 2. High Durability

Amazon S3 is designed for:

**99.999999999% (11 Nines) Durability**

AWS automatically stores multiple copies of your data across multiple devices.

Even if one storage device fails, your data remains safe.

---

## 3. High Availability

Amazon S3 provides:

**99.99% Availability**

This ensures that your data is accessible whenever required.

---

## 4. Secure Storage

Amazon S3 offers multiple security features:

* IAM Policies
* Bucket Policies
* Access Control Lists (ACLs)
* Block Public Access
* Server-Side Encryption
* Client-Side Encryption
* MFA Delete

---

## 5. Cost Effective

Amazon S3 offers multiple storage classes.

You pay only for:

* Storage used
* Requests
* Data transfer

This Pay-As-You-Go pricing model helps reduce infrastructure costs.

---

## 6. Global Accessibility

Objects stored in Amazon S3 can be accessed securely from anywhere in the world using:

* AWS Console
* AWS CLI
* SDKs
* REST APIs

---

# Benefits of Amazon S3

Amazon S3 offers several advantages over traditional storage solutions.

### Durability

Provides 11 nines of durability.

### Scalability

Automatically scales without downtime.

### Security

Supports encryption, IAM policies, bucket policies, and logging.

### Performance

Designed for high-speed upload and download operations.

### Cost Optimization

Multiple storage classes allow businesses to reduce storage costs.

### Reliability

AWS manages storage infrastructure, hardware failures, and data replication.

---

# Amazon S3 Architecture

```text
                    Users / Applications
                           │
                           ▼
                  Amazon S3 Bucket
                           │
        ┌──────────────────┼──────────────────┐
        ▼                  ▼                  ▼
     Images             Documents          Videos
        │                  │                  │
        └──────────────────┼──────────────────┘
                           ▼
                 Versioning & Encryption
                           │
                           ▼
             Lifecycle Rules & Storage Classes
```
---

# S3 Terminology

Before working with Amazon S3, it is important to understand its basic components.

---

## Bucket

A Bucket is a container that stores objects.

Think of it as a folder that holds files.

Example:

```text
company-backup
```

A bucket can contain:

* Images
* Videos
* PDFs
* Logs
* Documents

Every object must belong to exactly one bucket.

---

## Object

An Object is the actual file stored inside a bucket.

Examples:

```text
resume.pdf

image.png

backup.zip

movie.mp4
```

Every object contains:

* File Data
* Object Key
* Metadata

---

## Object Key

The Object Key is the unique name of an object inside a bucket.

Example:

```text
images/profile.jpg
```

Here,

```text
Bucket
```

```
company-data
```

```text
Object Key
```

```
images/profile.jpg
```

The object key acts like the file path.

---

## Metadata

Metadata provides additional information about an object.

Examples:

* File Size
* Content Type
* Upload Date
* Encryption Type
* Cache Control
* Custom Metadata

Example:

```text
Content-Type:
image/png
```

---

# Bucket Naming Rules

Bucket names must be globally unique across all AWS accounts.

Example:

If someone has already created:

```text
mybucket
```

No one else in the world can create another bucket with the same name.

---

## Rules

Bucket names:

* Must be between **3 and 63 characters**
* Must contain only lowercase letters
* Can contain numbers
* Can contain hyphens (-)
* Can contain periods (.)
* Must begin and end with a letter or number
* Cannot contain uppercase letters
* Cannot contain spaces

---

# AWS Region Selection

While creating a bucket, AWS asks you to choose a Region.

Example:

* ap-south-1 (Mumbai)
* us-east-1 (N. Virginia)
* eu-west-1 (Ireland)

Choosing the correct region helps reduce latency and comply with data residency regulations.

Choose the region closest to your users whenever possible.

---

# Creating an Amazon S3 Bucket

An S3 bucket can be created using:

* AWS Management Console
* AWS CLI
* AWS SDKs
* AWS CloudFormation
* Terraform

---

## Steps to Create a Bucket Using AWS Console

1. Sign in to the AWS Management Console.
2. Search for **Amazon S3**.
3. Click **Create Bucket**.
4. Enter a globally unique bucket name.
5. Select an AWS Region.
6. Configure bucket settings.
7. Review the configuration.
8. Click **Create Bucket**.

Your bucket is now ready to store objects.

---

# Bucket Properties

Amazon S3 provides several bucket-level features.

## Versioning

Keeps multiple versions of an object.

Protects against accidental deletion and overwriting.

*(Covered in detail in Part 2.)*

---

## Default Encryption

Automatically encrypts newly uploaded objects.

Supported options:

* SSE-S3
* SSE-KMS

---

## Server Access Logging

Records all requests made to the bucket.

Useful for:

* Auditing
* Security Monitoring
* Troubleshooting

---

## Tags

Tags help organize buckets.

Example:

```text
Environment = Production

Project = AWS-Learning

Owner = Kiran
```

---

## Event Notifications

Automatically trigger AWS services when objects are created or deleted.

Example:

* AWS Lambda
* Amazon SNS
* Amazon SQS

*(Covered in detail in Part 3.)*

---

# Uploading and Managing Objects

An **Object** is the actual file stored inside an Amazon S3 bucket.

Examples:

* Images
* Videos
* PDF Files
* Documents
* Backup Files
* ZIP Files
* Log Files

Each object stored in S3 consists of:

* Object Data
* Object Key (Unique Name)
* Metadata
* Version ID (If Versioning is Enabled)

---

# Ways to Upload Objects

Amazon S3 allows uploading objects using multiple methods.

## 1. AWS Management Console

The easiest method for beginners.

Steps:

1. Open AWS Console.
2. Navigate to Amazon S3.
3. Select your bucket.
4. Click **Upload**.
5. Select files or folders.
6. Click **Upload**.

---

## 2. AWS CLI

Example:

```bash
aws s3 cp image.png s3://my-learning-bucket/
```

Upload an entire folder:

```bash
aws s3 cp ./images s3://my-learning-bucket/images --recursive
```

---

## 3. AWS SDK

Developers can upload objects using SDKs such as:

* Python (Boto3)
* Java
* Node.js
* .NET
* Go

---

## 4. REST APIs

Applications can upload files directly using Amazon S3 REST APIs.

---

# Object Metadata

Metadata provides additional information about an object.

Metadata helps S3 understand the characteristics of the uploaded object.

Examples include:

* File Size
* Content Type
* Last Modified Date
* Cache Control
* Encryption Type
* Custom Metadata

Example:

```text
Content-Type: image/png

Content-Length: 5.4 MB

Server-Side Encryption: AES256
```

---

# Object Versioning

## What is Versioning?

Versioning is an S3 feature that stores multiple versions of the same object.

Instead of permanently replacing or deleting a file, Amazon S3 keeps previous versions.

---

## Why Enable Versioning?

Versioning protects data from:

* Accidental deletion
* Accidental overwrite
* Application errors
* User mistakes

---

## Example

Initially:

```text
resume.pdf
```

Upload a new file with the same name:

```text
resume.pdf
```

Without Versioning:

```text
Old File
    ↓
Deleted
```

With Versioning:

```text
Version 1

Version 2

Version 3
```

All versions remain available.

---

# Version ID

When Versioning is enabled, every object receives a unique Version ID.

Example:

```text
resume.pdf

Version ID:
3L4kQTJlcpXroDTDmJ
```

---

# Delete Marker

When Versioning is enabled and you delete an object:

Amazon S3 does not permanently remove it.

Instead, it creates a **Delete Marker**.

Example:

```text
Version 1

Version 2

Delete Marker
```

The object can still be recovered.

---

# Object Encryption

Encryption protects stored data from unauthorized access.

Amazon S3 supports three types of Server-Side Encryption.

---

## 1. SSE-S3

(Server-Side Encryption with Amazon Managed Keys)

AWS manages the encryption keys.

Features:

* Easy to use
* No key management
* Enabled automatically if configured

Best for:

General-purpose storage.

---

## 2. SSE-KMS

(Server-Side Encryption using AWS Key Management Service)

Encryption keys are managed using AWS KMS.

Benefits:

* Better security
* Access logging
* Key rotation
* Permission control

Best for:

Production environments.

---

## 3. SSE-C

(Server-Side Encryption with Customer-Provided Keys)

Customer provides the encryption key.

AWS never stores the encryption key.

Best for:

Organizations with strict security requirements.

---

# Client-Side Encryption

Instead of AWS encrypting data,

the application encrypts files before uploading them to Amazon S3.

Advantages:

* Complete control over encryption
* Maximum security

Disadvantages:

* Customer manages keys
* More complex implementation

---

# Access Control in Amazon S3

Amazon S3 provides multiple methods to control access.

* IAM Policies
* Bucket Policies
* Access Control Lists (ACLs)
* Block Public Access

---

# IAM Policies

IAM Policies are **identity-based policies**.

They define what actions a user, group, or role can perform.

Example:

Allow:

* Upload Objects
* Download Objects
* Delete Objects

---

Example JSON Policy:

```json
{
  "Version":"2012-10-17",
  "Statement":[
    {
      "Effect":"Allow",
      "Action":"s3:*",
      "Resource":"*"
    }
  ]
}
```

---

# Bucket Policies

Bucket Policies are **resource-based policies**.

They define who can access a specific bucket.

Example:

Allow only one AWS Account to access the bucket.

---

Example:

```text
Bucket:
company-backup

Only:
Backup Team
```

can access the bucket.

---

# Access Control Lists (ACLs)

ACLs are the older permission model in Amazon S3.

They define permissions for:

* Individual Objects
* Buckets

Modern AWS environments usually prefer:

* IAM Policies
* Bucket Policies

instead of ACLs.

---

# Block Public Access

Amazon S3 blocks public access by default.

This feature protects buckets from accidental exposure.

If enabled:

```text
Public Access
      ❌ Blocked
```

Best Practice:

Always keep Block Public Access enabled unless public access is required.

---

# Making a Bucket Public

Sometimes public access is required.

Example:

* Static Website Hosting
* Public Images
* Software Downloads

To make a bucket public:

1. Disable Block Public Access.
2. Attach a Bucket Policy.
3. Allow public read permissions.

Only make buckets public when absolutely necessary.

---

# Multipart Upload

Uploading large files as one object is inefficient.

Amazon S3 provides Multipart Upload.

Instead of uploading one large file:

```text
10 GB File
```

Amazon S3 splits it into:

```text
Part 1

Part 2

Part 3

Part 4

...

Part N
```

Each part uploads independently.

After completion:

Amazon S3 combines all parts into a single object.

---

# Benefits of Multipart Upload

* Faster uploads
* Parallel uploads
* Better reliability
* Resume interrupted uploads

Recommended for files larger than **100 MB**.

Multipart Upload becomes especially useful for files larger than **5 GB**.

---

# S3 Batch Operations

S3 Batch Operations allow performing actions on millions or even billions of objects simultaneously.

Examples:

* Copy Objects
* Delete Objects
* Add Tags
* Replace Tags
* Restore Glacier Objects

Instead of processing objects one by one,

Amazon S3 performs the operation in bulk.

---

# Common Object Operations

Amazon S3 supports:

* Upload
* Download
* Copy
* Move
* Rename (Copy + Delete)
* Delete
* Restore
* Tag
* Encrypt

---

# Object Tags

Tags help organize objects.

Example:

```text
Department = Finance

Environment = Production

Owner = Kiran
```

Benefits:

* Easy searching
* Cost allocation
* Lifecycle Rules
* Reporting

---

# Presigned URL

A Presigned URL allows temporary access to private objects.

Example:

Generate a URL valid for:

```text
24 Hours
```

Anyone with the URL can access the object until it expires.

Common use cases:

* Secure File Sharing
* Temporary Downloads
* Upload Files Without AWS Credentials

---

# Best Practices

* Enable Versioning for important buckets.
* Use SSE-KMS for production workloads.
* Keep Block Public Access enabled by default.
* Use Bucket Policies instead of ACLs whenever possible.
* Use Multipart Upload for large files.
* Use Presigned URLs instead of making buckets public.
* Organize objects using prefixes (folders).
* Apply tags to important objects.

---
