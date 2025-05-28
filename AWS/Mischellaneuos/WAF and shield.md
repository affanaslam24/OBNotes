**AWS WAF** is a web application firewall that lets you monitor the HTTP(S) requests that are forwarded to an Amazon CloudFront distribution, an Amazon API Gateway REST API, an Application Load Balancer, or an AWS AppSync GraphQL API.

**AWSManagedRulesSQLiRuleSet** – The SQL database rule group contains rules to block request patterns associated with the exploitation of SQL databases, like SQL injection attacks. This can help prevent remote injection of unauthorized queries. Evaluate this rule group for use if your application interfaces with an SQL database.

![](https://media.tutorialsdojo.com/aws-waf-sql-injection-attack-prevention.png)

AWS WAF is easy to deploy and protect applications deployed on either Amazon CloudFront as part of your CDN solution, the Application Load Balancer that fronts all your origin servers, Amazon API Gateway for your REST APIs, or AWS AppSync for your GraphQL APIs. There is no additional software to deploy, DNS configuration, SSL/TLS certificate to manage, or need for a reverse proxy setup.

With AWS Firewall Manager integration, you can centrally define and manage your rules and reuse them across all the web applications that you need to protect.


![[Pasted image 20250410121132.png]]


![[Pasted image 20250410121244.png]]

- ddos with shield
- layer 7, alb, api gateway, http/s with waf
![[Pasted image 20250410121550.png]]

- provides global perimeter protection!




Difference between WAF and Security groups:


**Level:** _Network layer (Layer 4)_  
**Think of it as:** A **firewall for your EC2 instances / ENIs / RDS / etc.**
#### ✅ What it does:
- Controls **who can connect** to your resource (IP address, port, protocol)
- Allows or denies **inbound** and **outbound** traffic
- Works at **instance level**
#### ❌ What it **doesn't** do:
- It doesn’t inspect the actual **contents** of the HTTP requests.
- No filtering based on URLs, query strings, headers, or cookies.

### **AWS WAF (Web Application Firewall)**

**Level:** _Application layer (Layer 7)_  
**Think of it as:** A **firewall for your website/app's HTTP/HTTPS traffic**
#### ✅ What it does:
- Inspects **actual HTTP/S requests** (headers, methods, query strings)
- Blocks **malicious payloads** like SQL injection, XSS, bots, bad agents
- Can **rate-limit** or filter based on geo/IP/header
#### ❌ What it **doesn't** do:
- Doesn't control low-level network access like ports or protocols
- Needs to be attached to services like CloudFront, ALB, API Gateway


But most importantly:


AWS Web Application Firewall (AWS WAF) is a web application firewall service that lets you monitor web requests and protect your web applications from malicious requests. Use AWS WAF to block or allow requests based on conditions that you specify, such as the IP addresses. You can also use AWS WAF preconfigured protections to block common attacks like SQL injection or cross-site scripting.

**Configure AWS Web Application Firewall (AWS WAF) on the Application Load Balancer in a Amazon Virtual Private Cloud (Amazon VPC)**

You can use AWS WAF with your Application Load Balancer to allow or block requests based on the rules in a web access control list (web ACL). Geographic (Geo) Match Conditions in AWS WAF allows you to use AWS WAF to restrict application access based on the geographic location of your viewers. With geo match conditions you can choose the countries from which AWS WAF should allow access.

Geo match conditions are important for many customers. For example, legal and licensing requirements restrict some customers from delivering their applications outside certain countries. These customers can configure a whitelist that allows only viewers in those countries. Other customers need to prevent the downloading of their encrypted software by users in certain countries. These customers can configure a blacklist so that end-users from those countries are blocked from downloading their software.



ALSO, Security Groups cannot restrict access based on the user's geographic location.



