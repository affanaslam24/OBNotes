- sp this is interesting: global accelarator is where you want to directy transfer data inn speed.
- But unlike caching in cloudfront, it sends through the edge location to the AWS private pipes of metwork.

NOw, for this question:
A gaming company is looking at improving the availability and performance of its global flagship application which utilizes User Datagram Protocol and needs to support fast regional failover in case an AWS Region goes down. The company wants to continue using its own custom Domain Name System (DNS) service.

keywords are:
1. UDP
2. fast regional failover for AWS region
3. Cant use ROUTE53.

So thinking of these, first thing we know is ELB is regional, so even if it failover protected, it cant help.
next up, CloudFront is for caching, and in UDP you are sending real time data, so the caching system of cloudfront will be of no use.
next, cloudfront doesnt has failover options
Cloudfront works in HTTP or HTTPs layers. not TCP or UDP.

THESE are enough, but more theory:


AWS Global Accelerator utilizes the Amazon global network, allowing you to improve the performance of your applications by lowering first-byte latency (the round trip time for a packet to go from a client to your endpoint and back again) and jitter (the variation of latency), and increasing throughput (the amount of time it takes to transfer data) as compared to the public internet.

AWS Global Accelerator improves performance for a wide range of applications over TCP or UDP by proxying packets at the edge to applications running in one or more AWS Regions. Global Accelerator is a good fit for non-HTTP use cases, such as gaming (UDP), IoT (MQTT), or Voice over IP, as well as for HTTP use cases that specifically require static IP addresses or deterministic, fast regional failover.



ELB:
**AWS Global Accelerator relies on ELB to provide the traditional load balancing features such as support for internal and non-AWS endpoints, pre-warming, and Layer 7 routing.** However, while ELB provides load balancing within one Region, AWS Global Accelerator provides traffic management across multiple Regions.


A regional ELB load balancer is an ideal target for AWS Global Accelerator. By using a regional ELB load balancer, you can precisely distribute incoming application traffic across backends, such as Amazon EC2 instances or Amazon ECS tasks, within an AWS Region.

If you have workloads that cater to a global client base, AWS recommends that you use AWS Global Accelerator. If you have workloads hosted in a single AWS Region and used by clients in and around the same Region, you can use an Application Load Balancer or Network Load Balancer to manage your resources.


understand the difference!!!


---

**Use AWS Global Accelerator for faster file uploads into the destination Amazon S3 bucket** - AWS Global Accelerator is a service that improves the availability and performance of your applications with local or global users. It provides static IP addresses that act as a fixed entry point to your application endpoints in a single or multiple AWS Regions, such as your Application Load Balancers, Network Load Balancers or Amazon EC2 instances. AWS Global A



---

![[Pasted image 20250413183526.png]]

this is a crucial drawing or overview of cloudfron..


---

**Use Amazon CloudFront with a custom origin pointing to the DNS record of the website on Amazon Route 53** - This option has been added as a distractor. CloudFront cannot have a custom origin pointing to the DNS record of the website on Route 53.

remember, it cannot point to a DNS record.

**Leverage a Amazon Route 53 geo-proximity routing policy pointing to on-premises servers** - Since the on-premises servers continue to be in the US, so even using a Route 53 geo-proximity routing policy that directs the users in Asia to the on-premises servers in the US would not reduce the latency for the users in Asia. So this option is incorrect.


we need to understand the different types of routing style in route53.

---


There is a geo location restriction feature in cloudfront!!!!

Geo Restriction feature of Amazon CloudFront helps in restricting traffic based on the user's geographic location. But, CloudFront works from edge locations and doesn't belong to a VPC. Hence, this option itself is incorrect and given only as a distractor.


ALso, cloudfront doesnt works from a VPC


**Use Amazon Route 53 based geolocation routing policy to restrict distribution of content to only the locations in which you have distribution rights**

Geolocation routing lets you choose the resources that serve your traffic based on the geographic location of your users, meaning the location that DNS queries originate from. For example, you might want all queries from Europe to be routed to an ELB load balancer in the Frankfurt region. You can also use geolocation routing to restrict the distribution of content to only the locations in which you have distribution rights.

**Use georestriction to prevent users in specific geographic locations from accessing content that you're distributing through a Amazon CloudFront web distribution**

You can use georestriction, also known as geo-blocking, to prevent users in specific geographic locations from accessing content that you're distributing through a Amazon CloudFront web distribution. When a user requests your content, Amazon CloudFront typically serves the requested content regardless of where the user is located. If you need to prevent users in specific countries from accessing your content, you can use the CloudFront geo restriction feature to do one of the following: Allow your users to access your content only if they're in one of the countries on a whitelist of approved countries. Prevent your users from accessing your content if they're in one of the countries on a blacklist of banned countries. So this option is also correct.

[[RoutingPolicy of R53]]

---

A custom origin can point to an on-premises server and CloudFront is able to cache content for dynamic websites. CloudFront can provide performance optimizations for custom origins even if they are running on on-premises servers. These include persistent TCP connections to the origin, SSL enhancements such as Session tickets and OCSP stapling.

Additionally, connections are routed from the nearest Edge Location to the user across the AWS global network. If the on-premises server is connected via a Direct Connect (DX) link this can further improve performance.

**CORRECT:** "Use Amazon CloudFront with a custom origin pointing to the on-premises servers" is the correct answer.

**INCORRECT:** "Use Amazon CloudFront with Lambda@Edge to direct traffic to an on-premises origin" is incorrect. Lambda@Edge is not used to direct traffic to on-premises origins.

---


remember that cloudfront doesnt goes well with real time purposes.

---
An Amazon S3 bucket in the us-east-1 Region hosts the static website content of a company. The content is made available through an Amazon CloudFront origin pointing to that bucket. A second copy of the bucket is created in the ap-southeast-1 Region using cross-region replication. The chief solutions architect wants a solution that provides greater availability for the website.

Which combination of actions should a solutions architect take to increase availability? (Select TWO.)


You can set up CloudFront with origin failover for scenarios that require high availability. To get started, you create an _origin group_ with two origins: a primary and a secondary. If the primary origin is unavailable or returns specific HTTP response status codes that indicate a failure, CloudFront automatically switches to the secondary origin.

**CORRECT:** "Add an origin for ap-southeast-1 to CloudFront” is the correct answer (as explained above.)

**CORRECT:** "Using us-east-1 bucket as the primary bucket and ap-southeast-1 bucket as the secondary bucket, create a CloudFront origin group” is also a correct answer (as explained above.)

**INCORRECT:** "Create an origin for CloudFront for both buckets” is incorrect. This would not increase the availability of the solution on its own.

**INCORRECT:** "Set up failover routing in Amazon Route 53” is incorrect as we are trying to enable failover in CloudFront and using Route 53 is for routing domain names.

**INCORRECT:** "Create a record in Amazon Route 53 pointing to the replica bucket" is incorrect as we are trying to enable failover in CloudFront and using Route 53 is for routing domain names.


---
 price class:

With Amazon CloudFront you can set the price class to determine where in the world the content will be cached. One of the price classes is “U.S, Canada and Mexico” and this is where the company’s users are located. Choosing this price class will result in lower costs and better performance for the company’s users.

---

. Certificates provided by ACM are automatically renewed. ACM does not automatically renew the certificates that you import.


