# Install Jenkins on EC2 (Amazon Linux 2023 & Ubuntu 24.04)

## Objective

In this lab, you will learn how to:

* Launch an EC2 Instance
* Connect using MobaXterm
* Install Java
* Install Jenkins
* Start and Enable Jenkins Service
* Configure Security Groups
* Access Jenkins Web Interface
* Create Jenkins Admin User
* Verify Jenkins Installation

---

# Architecture

```text
Windows Laptop
      │
      │ Browser
      ▼
http://PUBLIC-IP:8080
      │
      ▼
Jenkins Server
      │
      ▼
EC2 Instance
      │
      ├── Amazon Linux 2023
      └── Ubuntu 24.04 LTS
```

---

# Prerequisites

* AWS Account
* Running EC2 Instance
* Key Pair (.pem)
* MobaXterm Installed
* Security Group with SSH Access

---

# Step 1: Launch EC2 Instance

Launch an EC2 Instance with:

| Setting        | Value               |
| -------------- | ------------------- |
| Instance Type  | t2.micro / t3.micro |
| Storage        | 8 GB                |
| Security Group | Allow SSH (22)      |
| Key Pair       | Existing or New     |

### Amazon Linux

```text
Amazon Linux 2023 AMI
```

### Ubuntu

```text
Ubuntu Server 24.04 LTS
```

Launch the instance and wait until it reaches the **Running** state.

---

# Step 2: Connect Using MobaXterm

Open MobaXterm.

Click:

```text
Session → SSH
```

### Remote Host

```text
<PUBLIC-IP>
```

### Username

Amazon Linux:

```text
ec2-user
```

Ubuntu:

```text
ubuntu
```

### Private Key

Select:

```text
your-key.pem
```

Click:

```text
OK
```

Verify connection:

```bash
whoami
```

---

# Step 3: Update Packages

## Amazon Linux 2023

```bash
sudo dnf update -y
```

---

## Ubuntu 24.04

```bash
sudo apt update
sudo apt upgrade -y
```

---

# Step 4: Install Java

Jenkins requires Java.

## Amazon Linux 2023

Install Amazon Corretto 17:

```bash
sudo dnf install java-17-amazon-corretto -y
```

Verify:

```bash
java -version
```

---

## Ubuntu 24.04

Install OpenJDK 17:

```bash
sudo apt install openjdk-17-jdk -y
```

Verify:

```bash
java -version
```

---

# Step 5: Install Jenkins

## Amazon Linux 2023

Add Jenkins Repository:

```bash
sudo wget -O /etc/yum.repos.d/jenkins.repo \
https://pkg.jenkins.io/redhat-stable/jenkins.repo
```

Import Jenkins Key:

```bash
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
```

Install Jenkins:

```bash
sudo dnf install jenkins -y
```

---

## Ubuntu 24.04

Add Jenkins Key:

Install Jenkins:

```bash
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian/jenkins.io-2026.key
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins
```

---

# Step 6: Start Jenkins Service

Start Jenkins:

```bash
sudo systemctl start jenkins
```

Verify Status:

```bash
sudo systemctl status jenkins
```

Expected:

```text
active (running)
```

---

# Step 7: Enable Jenkins on Boot

```bash
sudo systemctl enable jenkins
```

Verify:

```bash
sudo systemctl is-enabled jenkins
```

Expected:

```text
enabled
```

---

# Step 8: Configure Security Group

Navigate:

```text
EC2 → Security Groups → Inbound Rules
```

Add:

| Type       | Protocol | Port | Source   |
| ---------- | -------- | ---- | -------- |
| SSH        | TCP      | 22   | My IP    |
| Custom TCP | TCP      | 8080 | Anywhere |

Save Rules.

---

# Step 9: Access Jenkins

Open Browser:

```text
http://<PUBLIC-IP>:8080
```

Example:

```text
http://13.233.xxx.xxx:8080
```

Jenkins Unlock Screen should appear.

---

# Step 10: Get Initial Admin Password

Retrieve password:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Example Output:

```text
7f4f8e0f1d9b6c2a123456789abcdef
```

Copy the password.

Paste it into Jenkins Unlock Page.

Click:

```text
Continue
```

---

# Step 11: Install Suggested Plugins

Select:

```text
Install Suggested Plugins
```

Wait for installation to complete.

---

# Step 12: Create Jenkins Admin User

Provide:

```text
Username
Password
Full Name
Email Address
```

Click:

```text
Save and Continue
```

---

# Step 13: Configure Jenkins URL

Default:

```text
http://PUBLIC-IP:8080/
```

Click:

```text
Save and Finish
```

---

# Step 14: Start Using Jenkins

Click:

```text
Start Using Jenkins
```

You should now see the Jenkins Dashboard.

---

# Useful Jenkins Commands

## Check Status

```bash
sudo systemctl status jenkins
```

## Start Jenkins

```bash
sudo systemctl start jenkins
```

## Stop Jenkins

```bash
sudo systemctl stop jenkins
```

## Restart Jenkins

```bash
sudo systemctl restart jenkins
```

## Enable Jenkins

```bash
sudo systemctl enable jenkins
```

## Disable Jenkins

```bash
sudo systemctl disable jenkins
```

---

# Interview Questions

## What is Jenkins?

Jenkins is an open-source automation server used for Continuous Integration and Continuous Deployment (CI/CD).

---

## Why Does Jenkins Require Java?

Jenkins is written in Java and runs on the Java Virtual Machine (JVM).

---

## Which Port Does Jenkins Use by Default?

```text
8080
```

---

## How Do You Start Jenkins?

```bash
sudo systemctl start jenkins
```

---

## How Do You Check Jenkins Status?

```bash
sudo systemctl status jenkins
```

---

## How Do You Enable Jenkins at Boot?

```bash
sudo systemctl enable jenkins
```

---

## Where Is Jenkins Initial Password Stored?

```text
/var/lib/jenkins/secrets/initialAdminPassword
```

---
