A website runs on a Microsoft Windows server in an on-premises data center. The web server is being migrated to Amazon EC2 Windows instances in multiple Availability Zones on AWS. The web server currently uses data stored in an on-premises network-attached storage (NAS) device.

Which replacement to the NAS file share is MOST resilient and durable?

Amazon FSx for Windows File Server provides fully managed, highly reliable file storage that is accessible over the industry-standard Server Message Block (SMB) protocol. It is built on Windows Server, delivering a wide range of administrative features such as user quotas, end-user file restore, and Microsoft Active Directory (AD) integration. It offers single-AZ and multi-AZ deployment options, fully managed backups, and encryption of data at rest and in transit.

![](https://img-c.udemycdn.com/redactor/raw/2020-05-21_01-28-32-63d08e70f92de39652bd9053f98f90df.jpg)

This is the only solution presented that provides resilient storage for Windows instances.

**CORRECT:** "Migrate the file share to Amazon FSx for Windows File Server" is the correct answer.

**INCORRECT:** "Migrate the file share to Amazon Elastic File System (Amazon EFS)" is incorrect as you cannot use Windows instances with Amazon EFS.

**INCORRECT:** "Migrate the file share to Amazon EBS" is incorrect as this is not a shared storage solution for multi-AZ deployments.

**INCORRECT:** "Migrate the file share to AWS Storage Gateway" is incorrect as with Storage Gateway replicated files end up on Amazon S3. The replacement storage solution should be a file share, not an object-based storage system.


**Note that EBS is not multi AZ**