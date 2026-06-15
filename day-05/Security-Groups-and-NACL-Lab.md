# Lab: Understanding Security Groups and NACL

## Objective

Learn the difference between:

* Security Groups
* NACLs
* Stateful vs Stateless Security

---

# Architecture

```text
Internet
   │
   ▼
Public Subnet
   │
   ▼
EC2 Instance
```

---

# Step 1: Launch EC2 Instance

Launch:

* Amazon Linux 2023
* t2.micro
* Public Subnet

Allow:

```text
SSH (22)
My IP
```

Connect using MobaXterm.

Verify:

```bash
whoami
```

---

# Step 2: Create Security Group

Create:

```text
Web-SG
```

Inbound Rules:

| Type | Port | Source    |
| ---- | ---- | --------- |
| SSH  | 22   | My IP     |
| HTTP | 80   | 0.0.0.0/0 |

Attach it to EC2.

---

# Step 3: Install Apache

```bash
sudo dnf install httpd -y
```

Start Apache:

```bash
sudo systemctl start httpd
```

Enable Apache:

```bash
sudo systemctl enable httpd
```

---

# Step 4: Create Test Page

```bash
echo "Security Group Lab" | sudo tee /var/www/html/index.html
```

Open:

```text
http://PUBLIC-IP
```

Page should load successfully.

---

# Step 5: Remove HTTP Rule

Delete:

```text
HTTP (80)
```

from Security Group.

Try:

```text
http://PUBLIC-IP
```

Result:

```text
Connection Failed
```

This proves Security Groups control instance access.

---

# Step 6: Create Custom NACL

Navigate:

```text
VPC → Network ACLs
```

Create:

```text
Web-NACL
```

Associate with Public Subnet.

---

# Step 7: Add NACL Rules

Inbound:

| Rule | Type        | Action |
| ---- | ----------- | ------ |
| 100  | HTTP 80     | Allow  |
| 200  | SSH 22      | Allow  |
| *    | All Traffic | Deny   |

Outbound:

| Rule | Type        | Action |
| ---- | ----------- | ------ |
| 100  | All Traffic | Allow  |

Save.

---

# Step 8: Test Access

Verify:

* SSH Works
* HTTP Works

---

# Step 9: Block HTTP Using NACL

Change:

```text
HTTP 80 → Deny
```

Test:

```text
http://PUBLIC-IP
```

Result:

```text
Website Blocked
```

Even though Security Group allows HTTP.

This proves:

```text
NACL Rules Override at Subnet Level
```

---

