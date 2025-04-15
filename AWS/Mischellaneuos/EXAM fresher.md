- A **directory service** is like a **digital phonebook** or **database** that stores, organizes, and provides access to **information about users, computers, and resources** in a network.
### What does a directory service manage?
- **Users** (name, email, password, roles)
- **Groups** (e.g., Developers, HR, Admins)
- **Computers and servers**
- **Permissions** (who can access what)
- **Policies** (like password rules or login times)

- and FSx is like efs, but for windows.

- Amazon FSx supports the use of Microsoft’s Distributed File System (DFS) to organize shares into a single folder structure up to **hundreds of PB in size** (this is important). So this option is correct.
- WS Managed Microsoft AD is built on the actual Microsoft Active Directory and does not require you to synchronize or replicate data from your existing Active Directory to the cloud.



- so this distinction is important: Microsoft AWS AD CAN integrate with your on prem Directory, but it wont allow **repplicstion or syncronisation**!
- ALso, AD is a directory service, whicha llows more about sign in s etc, a directory management service of kind.
- FSx is more of a ifle sttorage type, and the keyword here is WIndows servers File system. LASO, you can integrate your FSx with AWS AD, later on.

---


A financial services company recently launched an initiative to improve the security of its AWS resources and it had enabled AWS Shield Advanced across multiple AWS accounts owned by the company. Upon analysis, the company has found that the costs incurred are much higher than expected.

Which of the following would you attribute as the underlying reason for the unexpectedly high costs for AWS Shield Advanced service?

- so it works like this, each account has a cap of 3k dollar for one account.
- but if you use consolidated bills via AWS organisation, then all the different accounts will be though of as one account.

ANSER: **Consolidated billing has not been enabled. All the AWS accounts should fall under a single consolidated billing for the monthly fee to be charged only once**

If your organization has multiple AWS accounts, then you can subscribe multiple AWS Accounts to AWS Shield Advanced by individually enabling it on each account using the AWS Management Console or API. You will pay the monthly fee once as long as the AWS accounts are all under a single consolidated billing, and you own all the AWS accounts and resources in those accounts.
- **Shield Advanced is account-specific**
    - You must **manually enable** it in each AWS account that you want protected.
- **You pay once if:**
    - All accounts are under **consolidated billing** (via AWS Organizations).
    - You **own all those accounts and their resources**.
- **Without consolidated billing**  
    → AWS assumes these are **independent entities**, so it **charges $3,000/month for each**.
---


**Amazon ElastiCache**

Amazon ElastiCache for Memcached is an ideal front-end for data stores like **Amazon RDS or Amazon DynamoDB**, providing a high-performance middle tier for applications with extremely high request rates and/or low latency requirements.

---

AWS Storage Gateway's file interface, or file gateway, offers you a seamless way to connect to the cloud in order to store application data files and backup images as durable objects on Amazon S3 cloud storage. File gateway offers SMB or NFS-based access to data in Amazon S3 with local caching. As the company wants to integrate data files from its analytical instruments into AWS via an NFS interface,

**As it turns out: storage gateway is when your on premesis things needs to extend or attach their data to cloud.**

---


AWS Storage Gateway’s File Gateway does not support file shares in Amazon FSx for Windows File Server, so this option is incorrect. it only uses S3
	When you need to access S3 using a file system protocol, you should use File Gateway. You get a local cache in the gateway that provides high throughput and low latency over SMB.
![[Pasted image 20250413193149.png]]
Amazon FSx File Gateway provides access to fully managed file shares in Amazon FSx for Windows File Server and it does not support EFS. You should also note that EFS uses the Network File System version 4 (NFS v4) protocol and it does not support SMB protocol.


---

For user or team file shares, and file-based application migrations, Amazon FSx File Gateway provides low-latency, on-premises access to fully managed file shares in Amazon FSx for Windows File Server. For applications deployed on AWS, you may access your file shares directly from Amazon FSx in AWS.

For your native Windows workloads and users, or your SMB clients, Amazon FSx for Windows File Server provides all of the benefits of a native Windows SMB environment that is fully managed and secured and scaled like any other AWS service. You get detailed reporting, replication, backup, failover, and support for native Windows tools like DFS and Active Directory.


this is a feature i didnt know of, so.....

-----




Understand the difference between guardduty and inspector.

guardduty is to check log files of various services in aws and then find any malicious activities inside them.
Inspector inspects inside an ec2 instance.


SO guardduty CAN work with ec2 instances, but it checks the runtime issues, not whos accessing and gaining access of it.

Inspector does that.

read the guard duty and inspector files again.