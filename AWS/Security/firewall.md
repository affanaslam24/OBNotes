![[Pasted image 20250416143039.png]]

	The AWS Network Firewall is a managed service that makes it easy to deploy essential network protections for all your Amazon Virtual Private Clouds, and you can then use domain list rules to block HTTP or HTTPS traffic to domains identified as low-reputation, or that are known or suspected to be associated with malware or botnets.

**CORRECT:** "Configure the route table for the private subnet so that it routes the outbound traffic to an AWS Network Firewall firewall then configure domain list rule groups" is the correct answer (as explained above.)

**INCORRECT:** "Create an AWS WAF web ACL. Filter traffic requests based on source and destination IP address ranges with custom rules" is incorrect. AWS WAF is a web application firewall that helps protect your web applications or APIs against common web exploits and bots that may affect availability, compromise security, or consume excessive resources. It is designed to protect your applications from malicious traffic, not your VPC.

**INCORRECT:** "Establish strict inbound rules for your security groups. Specify the URLs of the authorized software repositories on the internet in your outbound rule" is incorrect. You cannot specify URLs in security group rules so this would not work.

**INCORRECT:** "Place an Application Load Balancer in front of your EC2 instances. Direct all outbound traffic to the ALB. For outbound access to the internet, use a URL-based rule listener in the ALB's target group" is incorrect. The ALB would not work as this sits within the VPC and is unable to control traffic entering and leaving the VPC itself.




---


You have an EC2 instance in a private subnet. You want to **prevent it from accessing malicious IPs or domains** on the internet.

- Deploy **AWS Network Firewall** in the **VPC**
    
- Add **stateful rules** to block known bad IPs/domains
    
- Route traffic from EC2 through the firewall using **route tables**
- **nspects and filters network traffic** at the VPC level
    
- Protects workloads against **known bad IPs, domain names, or patterns**
    
- Uses **stateful** and **stateless** inspection rules
    
- Can detect **intrusions** or prevent **data exfiltration**
    
- Works at the **subnet level** — used with **VPC routing**