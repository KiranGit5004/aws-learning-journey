# AWS IAM (Identity and Access Management)

## 📌 What is IAM?

AWS IAM (Identity and Access Management) is a service provided by Amazon Web Services (AWS) that helps you manage access to your AWS resources. It's like a security system for your AWS account.

IAM allows you to:

* Create and manage users
* Create groups
* Create roles
* Assign permissions
* Control access to AWS services and resources

IAM is a Global Service, meaning it is not tied to a specific AWS Region.

---

# Why IAM is Important

IAM helps organizations:

* Secure AWS resources
* Control user access
* Follow the Principle of Least Privilege
* Enable Multi-Factor Authentication (MFA)
* Audit user activities
* Manage permissions centrally

---

# Core Components of IAM

## 1. IAM Users

Users: IAM users represent individual people or entities (such as applications or services) that interact with your AWS resources. Each user has a unique name and security credentials (password or access keys) used for authentication and access control.

### Features

* Unique username
* Password for AWS Console access
* Access Keys for CLI/API access

### Example

* Admin User
* Developer User
* DevOps User

---

## 2. IAM Groups

An IAM Group is a collection of IAM Users. Instead of assigning permissions individually, permissions can be assigned to groups,  making it easier to manage access control. Users can be added or removed from groups as needed.

### Example

Developers Group

Members:

* User1
* User2
* User3

All users inherit the permissions assigned to the group.

---

## 3. IAM Roles

IAM Roles provide temporary access to AWS resources. Roles do not have permanent credentials. Roles are typically used by applications or services that need to access AWS resources on behalf of users or other services.

Roles are assumed by:

* AWS Services
* Applications
* EC2 Instances
* Lambda Functions
* External Users

### Example

An EC2 instance accesses an S3 bucket using an IAM Role instead of storing Access Keys.

---

## 4. IAM Policies

IAM policies are JSON documents that define permissions. 
Policies specify the actions that can be performed on AWS resources and the resources to which the actions apply. 
Policies can be attached to users, groups, or roles to control access. IAM provides both AWS managed policies (predefined policies maintained by AWS) and customer managed policies (policies created and managed by you).

### Example Policy

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "*"
    }
  ]
}
```

### Policy Components

| Component | Description           |
| --------- | --------------------- |
| Effect    | Allow or Deny         |
| Action    | AWS operation         |
| Resource  | AWS resource          |
| Condition | Optional restrictions |

---

# Types of IAM Policies

## AWS Managed Policies

Created and maintained by AWS.

Examples:

* AdministratorAccess
* AmazonS3FullAccess
* AmazonEC2FullAccess

### Advantages

* Easy to use
* Maintained by AWS

---

## Customer Managed Policies

Created and managed by the customer (you).

### Advantages

* More control
* Custom permissions

---

## Inline Policies

Directly attached to:

* User
* Group
* Role

Used when permissions should exist only for a single entity.

---

# Principle of Least Privilege

IAM follows the principle of least privilege, meaning users and entities are given only the necessary permissions required for their tasks, minimizing potential security risks. IAM also provides features like multi-factor authentication (MFA) for added security and an audit trail to track user activity and changes to permissions.

---

# Multi-Factor Authentication (MFA)

MFA adds an additional security layer.

Users provide:

1. Password
2. OTP from authenticator application

### Benefits

* Better account security
* Protection against stolen passwords

---

# IAM Best Practices

* Never use Root User for daily tasks
* Enable MFA on Root Account
* Create IAM Users instead of sharing Root credentials
* Use IAM Groups
* Follow Least Privilege Principle
* Rotate Access Keys regularly
* Use IAM Roles whenever possible
* Review permissions periodically

---

# Root User vs IAM User

| Root User                           | IAM User                      |
| ----------------------------------- | ----------------------------- |
| Full Account Access                 | Limited Access                |
| Created During AWS Account Creation | Created by Admin              |
| Cannot be restricted                | Permissions can be controlled |
| One per AWS Account                 | Multiple Users Allowed        |

---

# Real-World Example

A company has:

* 1 Admin Team
* 5 Developers
* 3 DevOps Engineers

IAM Setup:

* Admin Group → AdministratorAccess
* Developer Group → Limited S3 and EC2 Access
* DevOps Group → EC2, VPC, CloudWatch Access

Users are added to groups and automatically inherit permissions.

---