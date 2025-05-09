The engineering team at an e-commerce company wants to establish a dedicated, encrypted, low latency, and high throughput connection between its data center and AWS Cloud. The engineering team has set aside sufficient time to account for the operational overhead of establishing this connection.

As a solutions architect, which of the following solutions would you recommend to the company?

answer:
Direct connect gives, high throughput, low latency. BUT it is not encrypted.
Site to Site VPN is encrypted.
Although we are asked that we can take our time for this establishment.
So the best possible way would be to use Both, AND with the VPN endpoints we can also encrypt the Direct connect connection as well.


onnection from your premises to AWS. AWS Direct Connect lets you establish a dedicated network connection between your network and one of the AWS Direct Connect locations.

With AWS Direct Connect plus VPN, you can combine one or more AWS Direct Connect dedicated network connections with the Amazon VPC VPN. This combination provides an IPsec-encrypted private connection that also reduces network costs, increases bandwidth throughput, and provides a more consistent network experience than internet-based VPN connections.

This solution combines the AWS managed benefits of the VPN solution with low latency, increased bandwidth, more consistent benefits of the AWS Direct Connect solution, and an end-to-end, secure IPsec connection.

![[Pasted image 20250413151422.png]]


THIS IS A VERY IMPORTANT DIAGRAM.


However, Site-to-site VPN cannot provide low latency and high throughput connection.


THE ABOVE DIAGRAM is the traditional way, But there is also transit gateway, which can be used to connect on premesis with your netwrok, which we often forget about.
BUT, and this is important to note, that transit geteways cannot be used alone.
They use **site to site vpn** in the bakground.
Therefore, its better to use Direct connect and VPN as a combination in combination.



---

Direct Connect involves significant monetary investment and takes at least a month to set up

AWS Snowball Edge Storage Optimized is the optimal choice if you need to securely and quickly transfer dozens of terabytes to petabytes of data to AWS. It provides up to 80 Terabytes of usable HDD storage, 40 vCPUs, 1 TB of SATA SSD storage, and up to 40 Gigabytes network connectivity to address large scale data transfer and pre-processing use cases.

As each Snowball Edge Storage Optimized device can handle 80 Terabytes of data, you can order 10 such devices to take care of the data transfer for all applications.


---


You cannot use AWS Site-to-Site VPN to integrate data files via the NFS interface

---


A VPC peering connection is a networking connection between two VPCs that enables you to route traffic between them using private IPv4 addresses or IPv6 addresses. Instances in either VPC can communicate with each other as if they are within the same network.

You can create a VPC peering connection between your own VPCs, or with a VPC in another AWS account. The VPCs can be in different regions (also known as an inter-region VPC peering connection).
![[Pasted image 20250415182516.png]]

---

You cannot create VPC gateway endpoints for Amazon EC2 instances. These are used with DynamoDB and S3 only.

Direct Connect gateway is used to connect a Direct Connect connection to multiple VPCs, it is not useful in this scenario as there is no Direct Connect connection.

---


With a gateway endpoint you create the endpoint in the VPC, attach a policy allowing access to the service, and then specify the route table to create a route table entry in.

---

**Gateway Load Balancer endpoint in each service account:** This is correct because GWLB is specifically designed to simplify the deployment of security appliances. Using GWLB endpoints in service accounts ensures efficient routing and centralized inspection of traffic.

**Deploy a Network Load Balancer (NLB) in the networking account to route traffic to the security appliance. Configure the service accounts to send traffic to the NLB by using a VPC peering connection:** This is incorrect because NLB is not optimized for traffic inspection. Additionally, VPC peering lacks centralized management and scalability for large organizations.

**Deploy an Application Load Balancer (ALB) in the networking account to route traffic to the security appliance. Configure the service accounts to send traffic to the ALB by using a private link:** This is incorrect because ALB is primarily used for HTTP/HTTPS-based applications and is not suitable for routing traffic for inspection appliances.

**Deploy interface VPC endpoints in the networking account for each service in the service accounts. Configure the security appliance to inspect traffic sent through the endpoints:** This is incorrect because interface VPC endpoints do not inherently support routing all traffic through a centralized appliance and lack the capability for deep packet inspection

---


- Always use datasync for syncing data between 2 places.
- why do we use PrivateLink? And can it be used along with DirectConnect to have onPrem connection with services inside AWS?