To improve the performance and security of the application, the engineering team at a company has created an Amazon CloudFront distribution with an Application Load Balancer as the custom origin. The team has also set up an AWS Web Application Firewall (AWS WAF) with Amazon CloudFront distribution. The security team at the company has noticed a surge in malicious attacks from a specific IP address to steal sensitive data stored on the Amazon EC2 instances.

As a solutions architect, which of the following actions would you recommend to stop the attacks?


Correct option:

**Create an IP match condition in the AWS WAF to block the malicious IP address**

AWS WAF is a web application firewall that helps protect your web applications or APIs against common web exploits that may affect availability, compromise security, or consume excessive resources. AWS WAF gives you control over how traffic reaches your applications by enabling you to create security rules that block common attack patterns, such as SQL injection or cross-site scripting, and rules that filter out specific traffic patterns you define.

How AWS WAF Works:

![](https://d1.awsstatic.com/products/WAF/product-page-diagram_AWS-WAF_How-it-Works@2x.452efa12b06cb5c87f07550286a771e20ca430b9.png)

via - [https://aws.amazon.com/waf/](https://aws.amazon.com/waf/)

If you want to allow or block web requests based on the IP addresses that the requests originate from, create one or more IP match conditions. An IP match condition lists up to 10,000 IP addresses or IP address ranges that your requests originate from. So, this option is correct.

Incorrect options:

**Create a deny rule for the malicious IP in the network access control list (network ACL) associated with each of the instances** - Network access control list (network ACL) are not associated with instances. So this option is also ruled out.

**Create a deny rule for the malicious IP in the Security Groups associated with each of the instances** - You cannot deny rules in Security Groups. So this option is ruled out.

**Create a ticket with AWS support to take action against the malicious IP** - Managing the security of your application is your responsibility, not that of AWS, so you cannot raise a ticket for this issue.

Reference:





Also:
### Scenario Recap:

- You're using **CloudFront + ALB + EC2**.
    
- You want to block a **specific IP address** sending **malicious traffic**.
    
- You already have **AWS WAF** associated with **CloudFront**.
    

---

### 🛡️ Why **not NACL**?
|**Aspect**|**NACL**|**AWS WAF**|
|---|---|---|
|**Layer**|Operates at **VPC level (Network Layer)**|Operates at **Application Layer**|
|**Scope**|Can only protect **VPC-based resources** like EC2|Can protect **CloudFront**, **ALB**, **API Gateway**, etc.|
|**Where it applies**|At the **subnet** level (after traffic enters VPC)|At the **edge**, before it reaches your network|
|**CloudFront Compatibility**|❌ Not applicable|✅ Fully supported|
|**Ease of Blocking IPs**|Static rules, less flexible|Dynamic IP sets, rate limiting, geo rules, etc.|
|**Logging & Visibility**|Basic logging|Detailed logs with request info|

---

### 🎯 The Key Difference:

Your traffic is coming through **CloudFront**, which is a **global service**, **outside the VPC**.

➡️ **NACLs don't work outside the VPC**, so they **cannot protect CloudFront** or block traffic **before it reaches ALB**.

---

### ✅ Final Verdict:

Use **AWS WAF** when:

- You want to block **IP addresses before traffic hits your infrastructure**.
    
- You need **Layer 7 filtering** (e.g., IPs, URIs, headers, user-agent, SQL injection, etc.).
    

Use **NACLs** when:

- You want to control traffic **in/out of subnets inside your VPC** at the **network level** (e.g., blocking ports or IP ranges for EC2s).

