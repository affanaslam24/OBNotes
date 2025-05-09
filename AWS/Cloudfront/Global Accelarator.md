![[Screenshot from 2025-04-09 14-31-16.png]]
- what is global accelarator?
- its a service by aws which uses its personal fibre connections to provide fast delivery of data to vaeious network.
- It is used, when you access a website or something, it find the closest edge location and thorugh that sends the data to the global accelarator fibre connection.
Why do we need this? 
because in normal routing, there are numerous hops, and more hops means worser qualitty of the content, and you dont want to corrupt your content.
And global accelarator provides this, it uses a direct connection through its fibre connection.

Also, it uses anycast ips.
What is Anycast IP?
- usually a single instance is attached to unicast ip, meaning single ip for single device, but with Anycast ip we can attach one ip to more than one Ip. And this makes the global accelarator flexible, beause you get 2 anycast ip, which are attached to different global accelarator, and this can be flexibly interchanged in bw=etween or whatever.



## Difference between global accelarator and cloudfrotn:
- **both provide speed optimisation**, but cloudfront caches the content, meanwhile global accelarator brings the network closer!!

![[Screenshot from 2025-04-09 14-32-48.png]]

- global accelaratpr uses tcp udp connecion, mesnwile cloudfront uses http/s connection.




|Feature|**CloudFront**|**Global Accelerator**|
|---|---|---|

|                    |                                |                            |
| ------------------ | ------------------------------ | -------------------------- |
| 🧠 **What is it?** | Content Delivery Network (CDN) | Global traffic accelerator |

|                         |                                                                                                    |                                                                                       |
| ----------------------- | -------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| 🎯 **Primary Use Case** | Caching and distributing **static and dynamic content** (websites, videos, images) closer to users | Speeding up **global traffic routing** to your **regional endpoints** (ALB, NLB, EC2) |

|   |   |   |
|---|---|---|
|📍 **Routing Level**|**Application layer** (HTTP/HTTPS)|**Network layer** (TCP/UDP)|

|   |   |   |
|---|---|---|
|🚀 **Performance Boost**|Uses edge locations to **cache content** for lower latency|Uses the AWS **global backbone** to find the shortest/fastest network path|

|   |   |   |
|---|---|---|
|🛡️ **Security Features**|DDoS protection, AWS WAF integration, SSL/TLS|DDoS protection, automatic failover, IP whitelisting|

|   |   |   |
|---|---|---|
|💰 **Caching?**|Yes, built-in caching for faster delivery of static assets|❌ No caching — just accelerates traffic to endpoints|

|   |   |   |
|---|---|---|
|🧭 **Can Route to:**|S3, EC2, ALB, Lambda@Edge, API Gateway|**Regional** ALB, NLB, EC2 instances (but **not S3 or Lambda**)|

|   |   |   |
|---|---|---|
|🌐 **IP Addressing**|Users connect via **CloudFront DNS (e.g. d123abc.cloudfront.net)**|Provides **2 static anycast IPs** (great for whitelisting in firewalls)|

|   |   |   |
|---|---|---|
|🔁 **Failover?**|Can do some routing via Lambda@Edge, but not ideal for failover|Built-in **automatic health checks and failover** to healthy endpoints|

---

AWS Global Accelerator uses the vast, congestion-free AWS global network to route TCP and UDP traffic to a healthy application endpoint in the closest AWS Region to the user.

This means it will intelligently route traffic to the closest point of presence (reducing latency). Seamless failover is ensured as AWS Global Accelerator uses anycast IP address which means the IP does not change when failing over between regions so there are no issues with client caches having incorrect entries that need to expire.\\




---


AWS Global Accelerator is a service that improves the availability and performance of applications with local or global users. You can configure the ALB as a target and Global Accelerator will automatically route users to the closest point of presence.

Failover is automatic and does not rely on any client side cache changes as the IP addresses for Global Accelerator are static anycast addresses. Global Accelerator also uses the AWS global network which ensures consistent performance.
![[Pasted image 20250416124429.png]]
**CORRECT:** "Configure AWS Global Accelerator and configure the ALBs as targets" is the correct answer.

**INCORRECT:** "Place an EC2 Proxy in front of the ALB and configure automatic failover" is incorrect. Placing an EC2 proxy in front of the ALB does not meet the requirements. This solution does not ensure deterministic routing the closest region and failover is happening within a region which does not protect against regional failure. Also, this introduces a potential bottleneck and lack of redundancy.

**INCORRECT:** "Create a Route 53 Alias record for each ALB and configure a latency-based routing policy" is incorrect. A Route 53 Alias record for each ALB with latency-based routing does provide routing based on latency and failover. However, the traffic will not traverse the AWS global network.

**INCORRECT:** "Use a CloudFront distribution with multiple custom origins in each region and configure for high availability" is incorrect. You can use CloudFront with multiple custom origins and configure for HA. However, the traffic will not traverse the AWS global network.