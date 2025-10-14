# 🌩️ Lab 02 – Launch and Connect EC2 Instance

**Module:** 01 – Cloud Fundamentals  
**Author:** Farah Ejaz  
**Goal:** Learn how to create, connect, and terminate an **Amazon EC2 instance**.

---

## 🎯 Objective
By the end of this lab, you will be able to:
- Launch an EC2 instance using the AWS Console.
- Connect to the instance via SSH (Linux) or RDP (Windows).
- Understand instance types, security groups, and key pairs.
- Terminate an instance safely to avoid unnecessary charges.

---

## 🧩 Prerequisites
- AWS Free Tier account
- IAM user with EC2 full access
- Basic understanding of cloud compute

---

## 🪜 Step-by-Step Instructions

### **Step 1 – Sign in to AWS Console**
1. Go to [AWS Console](https://aws.amazon.com/console/)
2. Sign in with your IAM or root account.
3. Open **EC2** from the search bar.

---

### **Step 2 – Launch a New EC2 Instance**
1. Click **Launch Instances**.
2. Choose **Amazon Linux 2023 AMI (Free Tier eligible)**.
3. Select **t2.micro** instance type (Free Tier eligible) → Click Next.
4. Configure instance details as default → Next.
5. Add storage as default → Next.
6. Tag the instance (optional): `Name: Lab02-EC2`
7. Configure **Security Group**:
   - Allow **SSH (Port 22)** for Linux or **RDP (Port 3389)** for Windows.
8. Review → Click **Launch**.
9. Select **Create a new key pair**, name it `lab02-keypair.pem`, download it safely, and click **Launch Instances**.


### **Step 3 – Connect to EC2**
#### For Linux:
1. Open Terminal (or Git Bash on Windows).
2. Set permissions for the key:
```bash
chmod 400 lab02-keypair.pem
Connect via SSH:

ssh -i lab02-keypair.pem ec2-user@<Public-IP-of-EC2>

For Windows (RDP):

Click Connect → RDP Client in the console.

Download the remote desktop file.

Use the key to get the password → Connect.

Step 4 – Test the Instance

Run simple commands to verify Linux EC2:

uname -a
df -h


For Windows: check that you can open Notepad or cmd.

Step 5 – Terminate the Instance

In EC2 console → Instances → Select your instance → Actions → Terminate Instance.

Confirm termination to avoid charges.

🧠 Key Learnings

Difference between instance types (t2.micro for Free Tier)

Security Groups control network access

Key pairs are essential for secure access

Always terminate instances to save costs

🧾 Summary
Task	Completed
Launch EC2 instance	✅
Connect via SSH / RDP	✅
Test commands	✅
Terminate instance	✅
