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