N### **AWS SSM (Systems Manager) - Overview**

**AWS Systems Manager (SSM)** is a service that helps you manage EC2 instances, on-prem servers, and cloud resources. It provides automation, patching, monitoring, and secure remote access to instances.

---

## **🔹 Key Features of AWS SSM**

### **1️⃣ Session Manager (SSM Session Manager)**

✅ **SSM Session Manager allows you to connect to EC2 instances** _without SSH keys or a bastion host_.  
✅ Works over **HTTPS (port 443)**, so no need to open port 22 (SSH).  
✅ **IAM Role Required**: The EC2 instance must have a role with the **SSM Managed Instance Core policy** attached.  
✅ Used for **secure shell access**, logging, and auditing.

> **Example Use Case:** Connect to an EC2 instance in a **private subnet** without using a NAT Gateway or VPN.

---

### **2️⃣ SSM Agent**

✅ Pre-installed on **Amazon Linux 2, Ubuntu, Windows Server** EC2 instances.  
✅ Runs in the background to handle commands from AWS.  
✅ Required for **Session Manager, Patch Manager, and other SSM features**.

> **If SSM isn’t working**, check if the **SSM Agent is installed and running** on the instance.

---

### **3️⃣ Run Command**

✅ Execute shell commands on **multiple EC2 instances at once**.  
✅ Works **without logging into the instances**.  
✅ Useful for **updates, configurations, and troubleshooting**.

> **Example:** Restart all EC2 instances with a specific tag: