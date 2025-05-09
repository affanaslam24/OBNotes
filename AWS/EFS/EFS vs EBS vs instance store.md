![[Pasted image 20250416142532.png]]
The problem that is being described is that the users are uploading the documents to an individual EC2 instance with a local EBS volume. Therefore, as EBS volumes cannot be shared across AZs, the data is stored separately and the ALB will be distributing incoming connections to different instances / data sets.

The simple resolution is to implement a shared storage layer for the documents so that they can be stored in one place and seen by any user who connects no matter which instance they connect to.

![](https://img-c.udemycdn.com/redactor/raw/2020-05-21_01-30-06-e730f4c928621d8e81593b31b92020f6.jpg)

**CORRECT:** "Copy the data from all EBS volumes to Amazon EFS. Modify the application to save new documents to Amazon EFS" is the correct answer.

**INCORRECT:** "Run a script to synchronize the data between Amazon EBS volumes" is incorrect. This is a complex and messy appr


---


![[Pasted image 20250416152959.png]]


keywords were: 
- replicated
- any deletion will not cause loss of data

An _instance store_ provides temporary block-level storage for your instance. This storage is located on disks that are physically attached to the host computer. Instance store is ideal for temporary storage of information that changes frequently, such as buffers, caches, scratch data, and other temporary content, or for data that is replicated across a fleet of instances, such as a load-balanced pool of web servers.

![](https://img-c.udemycdn.com/redactor/raw/2020-05-18_12-54-38-9844f13d68a10a257851c57f0f920791.JPG)

Some instance types use NVMe or SATA-based solid state drives (SSD) to deliver high random I/O performance. This is a good option when you need storage with very low latency, but you don't need the data to persist when the instance terminates or you can take advantage of fault-tolerant architectures.

In this scenario the data is replicated and fault tolerant so the best option to provide the level of performance required is to use instance store volumes.

**CORRECT:** "Amazon EC2 instance store" is the correct answer.

**INCORRECT:** "Amazon EBS " is incorrect. The Elastic Block Store (EBS) is a block storage device but as the data is distributed and fault tolerant a better option for performance would be to use instance stores.

**INCORRECT:** "Amazon EFS " is incorrect as EFS is not a block device, it is a filesystem that is accessed using the NFS protocol.

**INCORRECT:** "Amazon S3" is incorrect as S3 is an object-based storage system, not a block-based storage system.


