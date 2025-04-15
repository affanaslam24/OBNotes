
![[Screenshot from 2025-03-30 20-18-01.png]]
![[Screenshot from 2025-03-30 20-19-48.png]]


### **CNAME vs. Alias Records in AWS Route 53**

Both **CNAME** and **Alias** records are used for domain name mapping, but they serve different purposes in AWS Route 53.

---

## **🔹 CNAME (Canonical Name) Record**

✅ **Maps a domain name to another domain name.**  
✅ Used when you want `www.example.com` to point to `example.com`.  
✅ Cannot be used for the **root domain** (apex domain).

### **Common Use Cases for Alias Records**

- **S3 Static Website Hosting**
    
- **CloudFront Distribution**
    
- **Elastic Load Balancer (ALB, NLB)**
    
- **API Gateway Endpoints**
    
- **Global Accelerator**
    

🚀 **Advantage:** Alias records handle AWS infrastructure changes **automatically**.

---

## **🔹 Key Differences:**

|Feature|CNAME|Alias|
|---|---|---|
|Points to|Another domain name|AWS service (S3, ALB, CloudFront, etc.)|
|Works on root domain|❌ No|✅ Yes|
|Supported by AWS Route 53|✅ Yes|✅ Yes|
|Free of charge|❌ No (DNS lookup charges apply)|✅ Yes|
|Faster resolution|❌ No|✅ Yes|
|Updates automatically for AWS resources|❌ No|✅ Yes|

---

## **🔹 When Should You Use Each?**

|Scenario|Use|
|---|---|
|Redirect `www.example.com` → `example.com`|**CNAME**|
|Point `myapp.com` to an S3 bucket|**Alias**|
|Point `myapp.com` to a CloudFront distribution|**Alias**|
|Point `sub.example.com` to `anotherdomain.com`|**CNAME**|
|Use a record at the root domain level|**Alias**|

---

### **💡 TL;DR**

- **Use CNAME** when pointing a **subdomain** (`www.example.com`) to another domain.
    
- **Use Alias** when pointing a **root domain** or AWS service (S3, ALB, CloudFront).



# What are apex, naked or root domains?
### **Apex Records (aka Naked Domains or Root Domains)**

**🔹 What is an Apex Record (Root Domain)?**  
An **apex record**, also called a **naked domain** or **root domain**, is the **top-level domain** without any subdomains.

**Example:**

- ✅ **Root domain (Apex record):** `example.com`
    
- ❌ **Subdomain:** `www.example.com`, `blog.example.com`, `api.example.com`
    

---

### **🔹 Why Are Apex Records Important?**

When users type `example.com` into a browser, **DNS needs to resolve it to an IP address**. However, traditional **CNAME records cannot be used at the root domain** due to DNS rules.

👉 **Solution?**

- Use **A records** (pointing to an IP address).
    
- Use **Alias records** (AWS-specific feature that works like CNAME but at the root level).
    

---

### **🔹 Apex Record vs. CNAME Limitation**

|Feature|Apex (Root) Record|CNAME|
|---|---|---|
|Works at `example.com`|✅ Yes|❌ No|
|Can point to another domain|❌ No|✅ Yes|
|Can point to AWS services like ALB, S3, CloudFront|✅ Yes (using Alias)|✅ Yes (but only for subdomains)|
|Requires an IP address|✅ Yes (if using A record)|❌ No|

---

### **🔹 Solutions for Root Domains in AWS**

- **Route 53 Alias Record** → Maps `example.com` to AWS services like ALB, S3, or CloudFront.
    
- **A Record** → Maps `example.com` to a specific IP address.
    
- **Redirect from `example.com` to `www.example.com`** using a static website (S3 or CloudFront).
    

---

### **🔹 TL;DR**

- **Apex Record = Root Domain (example.com)**
    
- **CNAME Cannot Be Used at the Root Level**
    
- **Use Alias Record in AWS for Root Domains**
    
- **Use A Record if you have a static IP**


-----------------------------------------------------

# where are they used?
### **Can You Use Both CNAME and Alias Together in Route 53?**

No, you **cannot** use an **Alias record within a CNAME record** because they serve different purposes. However, you **can create both separately** for different use cases.

---

### **✅ Correct Way to Set Up Alias and CNAME**

- If you want to map the **root domain (`example.com`)** → Use an **Alias record** (`A` type).
    
- If you want to map a **subdomain (`www.example.com`)** → You can use **either** a **CNAME record** or an **Alias record**, depending on the target.
    

---

## **🔹 Can You Select "CNAME" and Then Enable Alias?**

No, AWS **Alias is only available for "A" or "AAAA" record types**, not CNAME.  
If you try to create a **CNAME record**, the "Alias" option will not be available.

|**Scenario**|**Use Alias Record?**|**Use CNAME?**|
|---|---|---|
|Root domain (`example.com`) → CloudFront, ALB, S3|✅ Yes|❌ No|
|Subdomain (`www.example.com`) → CloudFront, ALB, S3|✅ Yes|✅ Yes|
|Subdomain (`www.example.com`) → Another domain (`example.net`)|❌ No|✅ Yes|

---

## **🔹 How to Set Up Both Alias & CNAME in Route 53**

1️⃣ **For the Root Domain (`example.com`) → Use an Alias Record**

- Type: **A**
    
- Alias: ✅ Enabled
    
- Target: **Choose CloudFront, ALB, or S3**
    

2️⃣ **For Subdomains (`www.example.com`) → Use CNAME or Alias**

- If pointing to another AWS service → Use **Alias**
    
- If pointing to an external domain (`example.net`) → Use **CNAME**
    

---

### **💡 TL;DR**

- You **can't use Alias inside CNAME**.
    
- Alias is available **only for A/AAAA records**.
    
- Use **Alias for AWS services**, and **CNAME for external domains**.
    
- Root domains must use **Alias**, not CNAME.




![[Pasted image 20250330203446.png]]



## In conclusion
Cname are used for pointing from one domain to subdomain, but not for static ip pointing or to point at dns names, likes for elb or s3 endpoints.
And alias is used for the other things which cname cant do.
At the same time, Alias is provided with A or AAAA record types. 