A systems administrator has created a private hosted zone and associated it with a Virtual Private Cloud (VPC). However, the Domain Name System (DNS) queries for the private hosted zone remain unresolved.

As a Solutions Architect, can you identify the Amazon Virtual Private Cloud (Amazon VPC) options to be configured in order to get the private hosted zone to work?

**Enable DNS hostnames and DNS resolution for private hosted zones**

DNS hostnames and DNS resolution are required settings for private hosted zones. DNS queries for private hosted zones can be resolved by the Amazon-provided VPC DNS server only. As a result, these options must be enabled for your private hosted zone to work.

DNS hostnames: For non-default virtual private clouds that aren't created using the Amazon VPC wizard, this option is disabled by default. If you create a private hosted zone for a domain and create records in the zone without enabling DNS hostnames, private hosted zones aren't enabled. To use a private hosted zone, this option must be enabled.

DNS resolution: Private hosted zones accept DNS queries only from a VPC DNS server. The IP address of the VPC DNS server is the reserved IP address at the base of the VPC IPv4 network range plus two. Enabling DNS resolution allows you to use the VPC DNS server as a Resolver for performing DNS resolution. Keep this option disabled if you're using a custom DNS server in the DHCP Options set, and you're not using a private hosted zone.

Incorrect options:

**Remove any overlapping namespaces for the private and public hosted zones** - If you have private and public hosted zones that have overlapping namespaces, such as example.com and accounting.example.com, then the Resolver routes traffic based on the most specific match. It won't result in unresolved queries, hence this option is wrong.

**Fix the Name server (NS) record and Start Of Authority (SOA) records that may have been created with wrong configurations** - When you create a hosted zone, Amazon Route 53 automatically creates a name server (NS) record and a start of authority (SOA) record for the zone for public hosted zone. However, this issue is about the private hosted zone, hence this is an incorrect option.

**Fix conflicts between your private hosted zone and any Resolver rule that routes traffic to your network for the same domain name, as it results in ambiguity over the route to be taken** - If you have a private hosted zone (example.com) and a Resolver rule that routes traffic to your network for the same domain name, the Resolver rule takes precedence. It won't result in unresolved queries.

---


A silicon valley based startup has a content management application with the web-tier running on Amazon EC2 instances and the database tier running on Amazon Aurora. Currently, the entire infrastructure is located in `us-east-1` region. The startup has 90% of its customers in the US and Europe. The engineering team is getting reports of deteriorated application performance from customers in Europe with high application load time.

As a solutions architect, which of the following would you recommend addressing these performance issues? (Select two)


**Setup another fleet of Amazon EC2 instances for the web tier in the `eu-west-1` region. Enable latency routing policy in Amazon Route 53**

Amazon Route 53 is a highly available and scalable cloud Domain Name System (DNS) web service. Use latency based routing when you have resources in multiple AWS Regions and you want to route traffic to the region that provides the lowest latency. To use latency-based routing, you create latency records for your resources in multiple AWS Regions. When Amazon Route 53 receives a DNS query for your domain or subdomain (example.com or acme.example.com), it determines which AWS Regions you've created latency records for, determines which region gives the user the lowest latency, and then selects a latency record for that region. Route 53 responds with the value from the selected record, such as the IP address for a web server.

As customers in Europe are facing performance issues with high application load time, you can use latency based routing to reduce the latency. Hence this is the correct option.

Amazon Route 53 Routing Policy Overview:

![](https://assets-pt.media.datacumulus.com/aws-saa-pt/assets/pt2-q6-i1.jpg)

via - [https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html)

**Create Amazon Aurora read replicas in the `eu-west-1` region**

Amazon Aurora is a MySQL and PostgreSQL-compatible relational database built for the cloud, that combines the performance and availability of traditional enterprise databases with the simplicity and cost-effectiveness of open source databases. Amazon Aurora features a distributed, fault-tolerant, self-healing storage system that auto-scales up to 64TB per database instance.

Amazon Aurora read replicas can be used to scale out reads across regions. This will improve the application performance for users in Europe. Therefore, this is also a correct option for the given use-case.

Incorrect options:

**Setup another fleet of Amazon EC2 instances for the web tier in the `eu-west-1` region. Enable geolocation routing policy in Amazon Route 53** - Geolocation routing lets you choose the resources that serve your traffic based on the geographic location of your users, meaning the location that DNS queries originate from. For example, you might want all queries from Europe to be routed to an ELB load balancer in the Frankfurt region. You can also use geolocation routing to restrict the distribution of content to only the locations in which you have distribution rights. You cannot use geolocation routing to reduce latency, hence this option is incorrect.

**Setup another fleet of Amazon EC2 instances for the web tier in the `eu-west-1` region. Enable failover routing policy in Amazon Route 53** - Failover routing lets you route traffic to a resource when the resource is healthy or to a different resource when the first resource is unhealthy. The primary and secondary records can route traffic to anything from an Amazon S3 bucket that is configured as a website to a complex tree of records. You cannot use failover routing to reduce latency, hence this option is incorrect.

**Create Amazon Aurora Multi-AZ standby instance in the `eu-west-1` region** - Amazon Aurora Multi-AZ enhances the availability and durability for the database, it does not help in read scaling, so it is not a correct option for the given use-case.

References:

[https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy.html)

[https://aws.amazon.com/blogs/aw](https://aws.amazon.com/blogs/aws/new-cross-region-read-replicas-for-amazon-aurora/)


### Why Latency-Based Routing (LBR) instead of Geolocation Routing?

#### 🤔 **Geolocation Routing**

- Routes traffic **based on the location of the user**, not the health or performance of resources.
    
- Example: "Users from France always go to the EU server."
    
- **Use case:** Content must follow regional laws (e.g., GDPR), or serve content tailored by location.
    

#### ⚡ **Latency-Based Routing** (LBR)

- Routes traffic to the **region with the lowest latency**, based on real-time network performance.
    
- Example: "Users in Europe are routed to us-east-1 _unless_ there's a replica in eu-west-1 with lower latency."
    
- **Use case:** Global applications where user experience (speed) is the priority.
- 