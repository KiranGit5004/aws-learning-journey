# Launch EC2 Instance and Connect Using MobaXterm (Windows)

## Objective

In this lab, you will:

* Launch an EC2 Instance
* Create a Key Pair
* Configure Security Groups
* Download and Install MobaXterm
* Connect to EC2 using SSH
* Verify Successful Connection

---

# Prerequisites

Before starting, ensure you have:

* AWS Account
* Internet Connection
* Windows System
* MobaXterm Installed

---

## Step 1: Login to AWS Console

1. Open AWS Management Console.
2. Login using your AWS credentials.
3. Search for **EC2** in the search bar.
4. Open the EC2 Dashboard.

---

## Step 2: Launch an EC2 Instance

1. Click **Launch Instance**.
2. Enter Instance Name.

Example:

```text
My-First-EC2
```

---

## Step 3: Select Amazon Machine Image (AMI)

Choose:

```text
Amazon Linux 2023 AMI
```

or

```text
Ubuntu Server 24.04 LTS
```

Click **Select**.

---

## Step 4: Select Instance Type

Choose:

```text
t2.micro
```

or

```text
t3.micro
```

These are Free Tier eligible (depending on your AWS account eligibility).

---

## Step 5: Create a Key Pair

Under Key Pair section:

1. Click **Create New Key Pair**
2. Enter Name

Example:

```text
ec2-key
```

3. Key Pair Type

```text
RSA
```

4. Private Key Format

```text
.pem
```

5. Click **Create Key Pair**

The `.pem` file will automatically download.

Example:

```text
ec2-key.pem
```

Store this file securely.

⚠️ Important:

If you lose the private key, you cannot SSH into the instance.

---

## Step 6: Configure Network Settings

Click **Edit**.

Allow:

| Type | Port |
| ---- | ---- |
| SSH  | 22   |

Source:

```text
My IP
```

This improves security.

---

## Step 7: Configure Storage

Default:

```text
8 GB gp3
```

is sufficient for learning.

---

## Step 8: Launch Instance

Click:

```text
Launch Instance
```

Wait until:

```text
Instance State = Running
```

---

## Step 9: Get Public IP Address

1. Open EC2 Dashboard.
2. Select Instance.
3. Copy:

```text
Public IPv4 Address
```

Example:

```text
13.234.xxx.xxx
```

You will use this for SSH connection.

---

# Step 10: Download MobaXterm

Download MobaXterm from:

https://mobaxterm.mobatek.net/

Recommended:

```text
MobaXterm Home Edition
```

Install using default settings.

---

## Step 11: Open MobaXterm

Launch:

```text
MobaXterm
```

Click:

```text
Session
```

---

## Step 12: Create SSH Session

Select:

```text
SSH
```

Fill details:

### Remote Host

```text
Public IPv4 Address
```

Example:

```text
13.234.xxx.xxx
```

---

## Step 13: Specify Username

Check:

```text
Specify Username
```

For Amazon Linux:

```text
ec2-user
```

For Ubuntu:

```text
ubuntu
```

---

## Step 14: Select Private Key

Go to:

```text
Advanced SSH Settings
```

Enable:

```text
Use Private Key
```

Browse and select:

```text
ec2-key.pem
```

---

## Step 15: Connect to EC2

Click:

```text
OK
```

or

```text
Connect
```

MobaXterm will establish SSH connection.

---

# Step 16: Verify Connection

Run:

```bash
whoami
```

Output:

```text
ec2-user
```

or

```text
ubuntu
```

Check hostname:

```bash
hostname
```

Check OS:

```bash
cat /etc/os-release
```

---

## Step 17: Disconnect Session

Type:

```bash
exit
```

Connection will close.

---

# Architecture

```text
Windows Laptop
      │
      │ SSH (Port 22)
      ▼
MobaXterm
      │
      ▼
EC2 Instance
      │
      ▼
Amazon Linux / Ubuntu
```

---

# Lab Summary

In this lab, you learned:

* How to launch an EC2 instance
* How to create a Key Pair
* How to configure Security Groups
* How to install MobaXterm
* How to connect to EC2 using SSH

