# Amazon S3 Hands-On Lab

## Objective

In this lab, you will learn how to:

* Create an S3 Bucket
* Upload Objects
* Create Folders
* Enable Versioning
* Recover Deleted Files
* Configure Default Encryption
* Create Bucket Policies
* Enable Static Website Hosting
* Configure Lifecycle Rules
* Delete S3 Resources

By the end of this lab, you will have practical experience with the most commonly used Amazon S3 features.

---

# Architecture

```text
             User
               │
               ▼
        Amazon S3 Bucket
               │
      ┌────────┼────────┐
      ▼        ▼        ▼
   Images   Documents  Backups
      │
      ▼
Versioning & Encryption
      │
      ▼
Lifecycle Rules
```

---

# Lab 1: Create an S3 Bucket

### Step 1

Login to the AWS Management Console.

---

### Step 2

Search for:

```text
Amazon S3
```

Open the S3 Dashboard.

---

### Step 3

Click:

```text
Create bucket
```

---

### Step 4

Configure the bucket.

Example:

```text
Bucket Name:
kiran-s3-lab-demo

AWS Region:
Asia Pacific (Mumbai) - ap-south-1
```

> **Note:** Bucket names must be globally unique.

---

### Step 5

Keep the default settings.

Ensure:

* Block Public Access = Enabled
* Versioning = Disabled (for now)

Click:

```text
Create bucket
```

---

# Lab 2: Upload Objects

Open your bucket.

Click:

```text
Upload
```

Upload:

* image.png
* resume.pdf
* notes.txt

Click:

```text
Upload
```

Verify all files are uploaded successfully.

---

# Lab 3: Create Folders

Inside the bucket create folders:

```text
images/

documents/

backups/
```

Move or upload files into their respective folders.

Verify the folder structure.

---

# Lab 4: Enable Bucket Versioning

Open:

```text
Bucket

↓

Properties

↓

Bucket Versioning

↓

Enable
```

Save the changes.

---

# Lab 5: Test Versioning

Upload a file named:

```text
resume.pdf
```

Upload another file with the same name.

Navigate to:

```text
Show Versions
```

Verify multiple versions of the object are available.

---

# Lab 6: Recover Deleted Object

Delete:

```text
resume.pdf
```

Enable:

```text
Show Versions
```

Locate the previous version.

Delete the **Delete Marker** to restore the object.

Verify the file is accessible again.

---

# Lab 7: Enable Default Encryption

Navigate:

```text
Bucket

↓

Properties

↓

Default Encryption
```

Enable:

```text
Server-Side Encryption

↓

SSE-S3
```

Save the configuration.

Upload a new file.

Verify the uploaded object is encrypted.

---

# Lab 8: Configure Bucket Policy

Navigate:

```text
Permissions

↓

Bucket Policy
```

Paste a sample read-only policy (or a policy appropriate for your use case).

Save the policy.

> **Note:** Keep **Block Public Access** enabled unless you intentionally need public access.

---

# Lab 9: Enable Static Website Hosting

Navigate:

```text
Properties

↓

Static Website Hosting

↓

Enable
```

Configuration:

```text
Index Document

index.html
```

Upload:

```text
index.html
```

If you want the website to be publicly accessible:

* Disable Block Public Access
* Attach a Bucket Policy allowing public read access

Copy the website endpoint and verify the page loads in your browser.

---

# Lab 10: Create Lifecycle Rule

Navigate:

```text
Management

↓

Lifecycle Rules

↓

Create Lifecycle Rule
```

Example:

```text
Rule Name:
Move-To-IA
```

Configuration:

* Transition objects to Standard-IA after 30 days
* Delete objects after 365 days

Save the rule.

---

# Lab 11: Delete Objects

Delete all uploaded objects.

Delete all object versions.

Delete all delete markers.

---

# Lab 12: Delete Bucket

After the bucket is empty:

Click:

```text
Delete Bucket
```

Type the bucket name to confirm.

Click:

```text
Delete Bucket
```

---

# Verification Checklist

✔ Bucket Created

✔ Objects Uploaded

✔ Folder Structure Created

✔ Versioning Enabled

✔ Deleted Object Recovered

✔ Default Encryption Enabled

✔ Bucket Policy Configured

✔ Static Website Hosting Enabled

✔ Lifecycle Rule Created

✔ Bucket Deleted Successfully

---

# Troubleshooting

### Bucket name already exists

Use a unique bucket name.

Example:

```text
kiran-s3-lab-2026
```

---

### Access Denied

Verify:

* IAM Permissions
* Bucket Policy
* Block Public Access settings

---

### Website returns Access Denied

Check:

* Static Website Hosting is enabled
* Bucket Policy allows public read access
* `index.html` exists in the bucket root

---

### Unable to Delete Bucket

Ensure:

* All objects are deleted
* All object versions are deleted
* All delete markers are removed

---

# Learning Outcomes

✅ Create and manage S3 Buckets

✅ Upload and organize objects

✅ Understand folders and object keys

✅ Enable Versioning

✅ Restore deleted files

✅ Configure Server-Side Encryption

✅ Understand Bucket Policies

✅ Host a static website

✅ Create Lifecycle Rules

✅ Clean up AWS resources

--- 
