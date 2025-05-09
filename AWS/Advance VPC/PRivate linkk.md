**Configure AWS  PrivateLink to create a private connection between the VPC and the third-party SaaS provider's APIs:** This is correct because AWS PrivateLink enables private connectivity between VPCs and supported AWS or third-party services, ensuring that traffic does not traverse the public internet.

**PrivateLink** allows you to **privately access services across VPCs** or from **your VPC to AWS services** using **private IP addresses**, keeping traffic **within the AWS network**.


**AWS PrivateLink** is a **secure, scalable** way to connect **VPCs to AWS services** or **third-party services** without sending traffic over the **public internet**.



|Feature|Description|
|---|---|

|   |   |
|---|---|
|**Private connectivity**|Traffic never leaves the AWS backbone—no public internet exposure.|

|   |   |
|---|---|
|**Simplified network architecture**|No need for VPC peering, NAT gateways, or VPNs.|

|   |   |
|---|---|
|**Supports interface endpoints**|It uses **ENIs (Elastic Network Interfaces)** with private IPs.|

|   |   |
|---|---|
|**Secure service access**|Reduces surface area for security threats.|


---


Using AWS PrivateLink to create an interface endpoint will allow your traffic to traverse the AWS Global Backbone to allow maximum performance and security. Also by using an AWS Direct Connect cable you can ensure you have a dedicated cable to provide maximum performance and low latency to and from AWS.

A company needs to connect its on-premises data center network to a new virtual private cloud (VPC). There is a symmetrical internet connection of 100 Mbps in the data center network. The data transfer rate for an on-premises application is multiple gigabytes per day. Processing will be done using an Amazon Kinesis Data Firehose stream.

What should a solutions architect recommend for maximum performance?


---


A company runs an application in an Amazon VPC that requires access to an Amazon Elastic Container Service (Amazon ECS) cluster that hosts an application in another VPC. The company’s security team requires that all traffic must not traverse the internet.

Which solution meets this requirement?


The correct solution is to use AWS PrivateLink in a service provider model. In this configuration a network load balancer will be implemented in the service provider VPC (the one with the ECS cluster in this example), and a PrivateLink endpoint will be created in the consumer VPC (the one with the company’s application).

![](https://img-c.udemycdn.com/redactor/raw/test_question_description/2021-02-25_12-11-25-32f12f4c4d3d65de75af283af88992aa.jpg)

**CORRECT:** "Create a Network Load Balancer in one VPC and an AWS PrivateLink endpoint for Amazon ECS in another VPC" is the correct answer.

**INCORRECT:** "Create a



 why do we use PrivateLink? And can it be used along with DirectConnect to have onPrem connection with services inside AWS?


**AWS PrivateLink** enables **private connectivity** between VPCs and **AWS services** (or your own services) **without traversing the public internet**. It uses **ENIs (Elastic Network Interfaces)** and **interface endpoints** within your VPC to route traffic privately.


Great — let’s break down **AWS PrivateLink** so you can confidently handle any tough questions in the future.

---

### 🔐 **What is AWS PrivateLink?**

**AWS PrivateLink** enables **private connectivity** between VPCs and **AWS services** (or your own services) **without traversing the public internet**. It uses **ENIs (Elastic Network Interfaces)** and **interface endpoints** within your VPC to route traffic privately.

---

### 📌 **When to Use PrivateLink**

1. **Accessing AWS Services Privately**
    
    - Example: Connect to **Amazon EFS**, **S3**, **Kinesis**, etc., without going over the public internet.
        
2. **Private Access to Services in Another VPC or Account**
    
    - You can expose your service in one VPC and let other VPCs (even in different accounts or organizations) access it **securely and privately**.
        
3. **Meeting Compliance Requirements**
    
    - Especially in healthcare, finance, or government — when **internet exposure must be avoided**.
        
4. **Using Direct Connect or VPN**
    
    - If you're using Direct Connect with a **Private VIF**, you **can’t reach AWS services** unless you use **PrivateLink endpoints**.
        

---

### 💡 **How Does It Work?**

Let’s say you want to access EFS from your on-premises network over **Direct Connect**:

- Normally, AWS services like EFS are public.
    
- But **Direct Connect + Private VIF** only routes to **private IPs**, not public endpoints.
    
- So you create an **interface VPC endpoint** (via **PrivateLink**) for EFS in your VPC.
    
- Now, EFS is accessible using a **private IP inside your VPC**.
    
- You mount EFS from on-prem via Direct Connect, going through that private IP — boom, fully private and compliant.
    

---

### ✅ **Key Benefits**

|Feature|Benefit|
|---|---|
|Private connectivity|No public internet involved|
|Secure by design|Data stays inside AWS backbone or VPN/DC connection|
|Highly scalable|Works across multiple VPCs and accounts|
|Service isolation|You control who accesses your service|
|Compliance-ready|Helps meet strict regulatory and security standards|

---

### 🧠 **Common Scenarios in Exams & Real World**

|Scenario|PrivateLink Relevance|
|---|---|
|On-prem to EFS/S3 via Direct Connect|Required to access AWS services over private IP|
|Multi-account architecture|One VPC hosts a service, others access it via PrivateLink|
|Service exposure to partners|You want partners to use your service securely without peering networks|
|Public subnet needs to access private services|Use PrivateLink so you don't need NAT or IGW|

---

### 🔄 **How to Set Up PrivateLink (Simplified)**

1. **Service side** (provider):
    
    - Create a **Network Load Balancer** (NLB) that points to your service (if it's custom).
        
    - Create a **VPC endpoint service** using the NLB.
        
    - Share the service with accounts/orgs.
        
2. **Client side** (consumer):
    
    - Create an **interface endpoint** in their VPC for the service.
        
    - This creates an ENI in their subnet pointing to the provider service.
        

---

### ⚠️ Gotchas / Limitations

- Only **TCP** traffic supported.
    
- Only works with **interface-type VPC endpoints**.
    
- **Not free** — you pay for each hour and GB processed via the interface endpoint.
    
- Must be in the **same Region** (though you can do cross-region via other methods).
    

---

Want a diagram or specific scenario walkthrough next?