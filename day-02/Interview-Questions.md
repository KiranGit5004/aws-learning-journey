# AWS IAM Interview Questions and Answers

## Q1. What is AWS IAM?

**Answer:**

AWS IAM (Identity and Access Management) is a service that allows administrators to securely manage access to AWS resources by creating users, groups, roles, and permissions.

---

## Q2. Why is IAM Important?

**Answer:**

IAM improves security by ensuring only authorized users can access AWS resources. It helps implement the Principle of Least Privilege and provides centralized access management.

---

## Q3. What are the Main Components of IAM?

**Answer:**

The main components are:

* Users
* Groups
* Roles
* Policies

---

## Q4. What is an IAM User?

**Answer:**

An IAM User is an identity created within AWS that represents a person or application requiring access to AWS resources.

---

## Q5. What is an IAM Group?

**Answer:**

An IAM Group is a collection of IAM Users. Permissions assigned to the group are inherited by all users within the group.

---

## Q6. What is an IAM Role?

**Answer:**

An IAM Role is an AWS identity that provides temporary permissions to users, applications, or AWS services without using permanent credentials.

---

## Q7. What is the Difference Between IAM User and IAM Role?

| IAM User                      | IAM Role                          |
| ----------------------------- | --------------------------------- |
| Permanent Identity            | Temporary Identity                |
| Has Passwords and Access Keys | No Permanent Credentials          |
| Used by Humans                | Used by Services and Applications |

---

## Q8. What are IAM Policies?

**Answer:**

IAM Policies are JSON documents that define permissions and determine which actions are allowed or denied on AWS resources.

---

## Q9. What are the Types of IAM Policies?

**Answer:**

* AWS Managed Policies
* Customer Managed Policies
* Inline Policies

---

## Q10. What is an AWS Managed Policy?

**Answer:**

An AWS Managed Policy is a predefined policy created and maintained by AWS.

Example:

* AdministratorAccess
* AmazonS3FullAccess

---

## Q11. What is a Customer Managed Policy?

**Answer:**

A policy created and maintained by the customer to provide customized permissions.

---

## Q12. What is the Principle of Least Privilege?

**Answer:**

It means giving users only the minimum permissions required to perform their tasks.

---

## Q13. What is MFA in AWS?

**Answer:**

Multi-Factor Authentication (MFA) provides an additional security layer by requiring both a password and a one-time verification code.

---

## Q14. Why Should Root User Not Be Used Daily?

**Answer:**

The Root User has unrestricted access to the AWS account. Using it daily increases security risks.

---

## Q15. What is the Difference Between Authentication and Authorization?

**Answer:**

### Authentication

Verifies who you are.

Example:

* Username
* Password
* MFA

### Authorization

Determines what actions you can perform after login.

Example:

* Read S3 Bucket
* Launch EC2 Instance

---

## Q16. Can a User Belong to Multiple Groups?

**Answer:**

Yes. An IAM User can be a member of multiple IAM Groups.

---

## Q17. Can IAM Be Used Across Regions?

**Answer:**

Yes. IAM is a Global AWS Service and works across all AWS Regions.

---

## Q18. What are IAM Best Practices?

**Answer:**

* Enable MFA
* Avoid Root User usage
* Follow Least Privilege
* Use Groups
* Use Roles instead of Access Keys
* Rotate Credentials
* Review Permissions Regularly
