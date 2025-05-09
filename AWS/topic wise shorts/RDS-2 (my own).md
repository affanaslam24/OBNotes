
**Basics:**
- Availibiliy = can go down, but allows for as immediate as possible of uptime again.
- consistency- would be to have same data immediately at the database instances
- scalability- scale up scale down
availibility- think of AZs, multi-az
scalability- think of readReplica

RDS provides an instance to run your database in, stores your data in EBS, and has security Group attached to it.

---

**RDS**
- MySql, MariaDB, PostgresQl, Oracle, MSSQL, oracle custom.
- Can have both ReadReplica as well as Multi-Az configuration.
- By default, Amazon RDS (Relational Database Service) is ==regional==, not Availability Zone (AZ) specific. This means that when you create an RDS instance, it's placed within a specific AWS Region, and you can choose whether to deploy it as a single-AZ or a Multi-AZ instance
- YOu can make your rds instance cross regional b using cross regional read replica.
- 


RDs restores
- creates a new instance, with new adress

RDS has auto scaling option which can be enabled later on for storage purposes. But this is only for storage purposes.
**Storage Auto Scaling**: Can be enabled so that the DB automatically increases its allocated storage as needed.
Only **scales storage**, not compute or instances.




---

**Aurora**

- By default, ==Amazon Aurora is deployed across multiple Availability Zones (AZs) within a single AWS Region==, ensuring high availability and resilience. This multi-AZ deployment means that your data is replicated across several physical locations within the same Region, providing redundancy and allowing for automatic failover if one AZ experiences an issue.
- While Aurora is deployed across multiple AZs within a Region, it's important to understand that you can also deploy Aurora clusters across multiple Regions using Aurora Global Database. This provides an even higher level of redundancy and disaster recovery capabilities
- Aurora's storage is distributed across the AZs, and data is replicated in a way that minimizes latency and ensures high availability

-

- it uses a cluster
- There must be a single primary instance and can have 0+ replica instances
- Uses cluster volumes, the volume is direct write in all the AZs
- only the primary instance can write to the storage, other storage only have read propoperties.
- Can have upto 15 replicas
- the data is the one that gets synchronous persistend, that means the storage only. the instances have no use in this case, unlike how the regular rds uses the instance to first syncronise and then write it to the storgae, aurora doesnt needs the instances.


-

- 2 endpoints, reader ad cluster endpont.
- Aurora custom endpoints allow you to define a subset of replicas for specific workloads
- Restore creates a new cluster here
- **Also, even though aurora uses cluster mode, it still requires a subnet group to know where to deploy the rds instance.**

-

- Storage in Aurora is by default configured for autoscaling upto 128 tb
- You can **enable autoscaling for Aurora Replicas** in an **Aurora Auto Scaling Group** (works with Amazon RDS Aurora + Application Auto Scaling).

---
**RDS proxy**
Instead of your app hitting the database directly, it connects to the **RDS Proxy**, which handles:
- Managing and reusing DB connections
- Queueing and retrying failed attempts
- Managing failover seamlessly
---

**Snapshots** 
- snapshots are not your typical ebs snapshots.
- they are snapshots which you will see inside the rds section.
- the backups done by rds creates S3 storage which you cant see through console.
- now, for snapshots, the standby instance is used. But if its single az rds, the single instance is used for backup.
- automatic snapshots are deleted when the rds is removed, and if you configure so. but manual snapshots doesnt gets deleted unless we go and delete specifically.
- Automatic snapshots are incremental
- Snapshots can be shared in between 2 accounts, but the encryption option needs to be checked



**Retention**
- its between 0 to 35 days, 0 meaning it doesnt backs up the data. and 35 means it can retain the snapshot or data between any day of  that 35 day. but it will still expire after 35 days. the only way to retain backup forever is to manually store it or when deleting the rds it asks for a final snapshot.
- RDS backup retention policies can only be applied to automated backups.
- No retention policy for manual

**Encrytion**
- encryption is done at rest using AWS kms
	- automated backkups
	- snapshots
	- readReplicas are the terms related with encryption
- First note that once something is enabled cant be suddenly changed and vice versa.
 - you can encrypt a copy of an unencrypted DB snapshot,
 - When copying an **encrypted snapshot**, you can use a **different KMS key** (great for cross-account access).
 - If the master is not encrypted, the read replicas cannot be encrypted
 - Multi-AZ is to help with High Availability, not encryption. 
 - Aurora Global Databases also support encryption.
 - **for RDS encryption at rest**, AWS **only supports KMS** (either AWS-managed or customer-managed keys).
 - encryptions keys from KMS can be shared in different accounts.


---

Multi-AZ
- need to be isnide a vpc
- must have 2 or more AZs 
- only the cname or the endpoint of the primary instance can be called for, we cannot access the standby instance directly.
- Its suncronous- meaning, that both the primary and the secondary gets a write in their data immediately.
- first the data in the primary instance is replicated to the database in the secondary instance, and then the write happens.
- Standby is not used for read or write until the primary faisl; thats where the failover option comes in.
- standby proivdes availibilty usecase, not a performance one.
- basically, it doesnt allows performance llike read and write operations or anything, it is not even used unless the primary inst4ance is failed. 
- availibility is used, basically even if its go down, the standby starts working with low downtime.
- BACKUP CAN BE TAKEN FROM THE STANDBY INSTANCES
- its just there for either good backup or for availibility. no scaling benefits, only system updates, backup or instance type changes ca help

---

ReadReplica
- upto 5 RR for rds, upto 15 for aurora
- can be cross regional
- Provides READ capabilities, that is why its for scalability of the rds.

So, snapshots and backups provided great RPO but not good RTO. RPO is how well the data can be restored in case of data loss. And RTO is how quickly. And snapshots have no say with how quickly, because it can take time.

BUt with readreplica, you can have great RPO as well as RTO, because a readReplica can be upgraded to read and write in low RTO.


You are not charged for the data transfer incurred in replicating data between your source DB instance and read replica within the same AWS Region.
- for different regions readrEPLICA you will be charged for data transfer


---

You can use both readReplica as well as multiAz for RDS and aurora. BUt aurora has a built in multiAz, and it has no standby instances.


---

Redshift and RDS
- Use **AWS Data Migration Service (DMS)** to replicate data from RDS to Redshift.
- then use redshit for analytical and data =warehouse trends and stuff

---

If we have readreplicas, then why do we need to use elasticache?


###### When to use readreplica:
- You want to **offload read queries** from the primary RDS database.
- Your app performs **read operations that must stay consistent** with the database (minimal replication lag).
- You want a **failover-ready standby** (read replica can be promoted).
- You are dealing with **complex queries** or **joins** that are best executed on a relational DB.

- It’s still a **full RDS instance** — costs more than caching.
- **No caching logic** — data is always read from disk/memory of the replica DB., meaning that its not In-memory.

###### When to use Elasticache:
- You want **sub-millisecond response times**.
- You are okay with **eventual consistency** and can handle **stale data**.
- You want to **cache results of frequent queries**, sessions, tokens, leaderboard scores, etc.
- You need **rate-limiting**, **counters**, or **pub/sub** functionality (only in Redis).
- **Data loss possible** unless configured with replication and persistence.

Many production-grade architectures use **both** together:

1. **ElastiCache** for **fast reads of hot data** (caching layer)
2. **Read Replicas** to **scale consistent reads** for non-cacheable data (like personalized dashboards or transactions)

---

There is an aurora Global database, for global resiliency

- nd up to five read-only, secondary AWS Regions.
- master database in primary region.
- enables **fast local reads** with **low latency** in **each region**, and provides **disaster recovery** from region-wide outages

---


There is the failover trick where if there is multiAz in an RDS, and if your primary instance fails, the standby instance will be the one to take over.

In readReplica, you have to promote automatically.

In Aurora, the endpoints are remapped in case of failover and the readReplica is turned into the primary instance. 

---


Aurora multi master is used for single region, where the write is heavy.
You use Global Database when the read is heavy and you require global access of your database.



---


An important question based on the revision:

A media company is migrating its flagship application from its on-premises data center to AWS for improving the application's read-scaling capability as well as its availability. The existing architecture leverages a Microsoft SQL Server database that sees a heavy read load. The engineering team does a full copy of the production database at the start of the business day to populate a dev database. During this period, application users face high latency leading to a bad user experience.

The company is looking at alternate database options and migrating database engines if required. What would you suggest?

KEYWORD:
heavyv read = read replica, NOT multiAZ(multiAz doesnt provides read or write, its for availibility)
Read-Scaling capability = read replica




**Leverage Amazon Aurora MySQL with Multi-AZ Aurora Replicas and create the dev database by restoring from the automated backups of Amazon Aurora**

Amazon Aurora (Aurora) is a fully managed relational database engine that's compatible with MySQL and PostgreSQL. An Amazon Aurora DB cluster consists of one or more DB instances and a cluster volume that manages the data for those DB instances. An Aurora cluster volume is a virtual database storage volume that spans multiple Availability Zones (AZs), with each Availability Zone (AZ) having a copy of the Amazon Aurora DB cluster data. Aurora supports Multi-AZ Aurora Replicas that improve the application's read-scaling and availability.

Amazon Aurora Overview:

![](https://d1.awsstatic.com/Product-Page-Diagram_Amazon-Aurora_How-it-Works.b1c2b37e7548757780b195c6dcceb58511de5b1d.png)

via - [https://aws.amazon.com/rds/aurora/](https://aws.amazon.com/rds/aurora/)

Aurora backs up your cluster volume automatically and retains restore data for the length of the backup retention period. Aurora backups are continuous and incremental so you can quickly restore to any point within the backup retention period. No performance impact or interruption of database service occurs as backup data is being written.

![](https://assets-pt.media.datacumulus.com/aws-saa-pt/assets/pt2-q52-i1.jpg)

via - [https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Managing.Backups.html](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Managing.Backups.html)

Automated backups occur daily during the preferred backup window. If the backup requires more time than allotted to the backup window, the backup continues after the window ends, until it finishes. The backup window can't overlap with the weekly maintenance window for the DB cluster. Aurora backups are continuous and incremental, but the backup window is used to create a daily system backup that is preserved within the backup retention period. The latest restorable time for a DB cluster is the most recent point at which you can restore your DB cluster, typically within 5 minutes of the current time.

For the given use case, you can create the dev database by restoring from the automated backups of Amazon Aurora.

Incorrect options:

**Leverage Amazon Aurora MySQL with Multi-AZ Aurora Replicas and restore the dev database via mysqldump** - Restoring the dev database via mysqldump would still result in a significant load on the primary DB, so this option fails to address the given requirement.

**Leverage Amazon RDS for MySQL with a Multi-AZ deployment and use the standby instance as the dev database** - The standby is there just for handling failover in a Multi-AZ deployment. You cannot access the standby instance and use it as a dev database. Hence this option is incorrect.

**Leverage Amazon RDS for SQL server with a Multi-AZ deployment and read replicas. Use the read replica as the dev database** - Amazon RDS supports Multi-AZ deployments for Microsoft SQL Server by using either SQL Server Database Mirroring (DBM) or Always On Availability Groups (AGs). Amazon RDS monitors and maintains the health of your Multi-AZ deployment.

Multi-AZ deployments provide increased availability, data durability, and fault tolerance for DB instances. In the event of planned database maintenance or unplanned service disruption, Amazon RDS automatically fails over to the up-to-date secondary DB instance. For SQL Server, I/O activity is suspended briefly during backup for Multi-AZ deployments.

A read replica is only meant to serve read traffic. The primary purpose of the read replica is to replicate the data in the primary DB instance. A read replica cannot be used as a dev database because it does not allow any database write operations.

