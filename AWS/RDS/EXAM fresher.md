- AWS rds custom oracle.
now this i sa new feature where suppose you have an on premesis environment with an racle legacy database installed and you want to migrate this to cloud database, but you also want to keep the layers instact as well as the custom OS to be configured.
AWS provided a new feature which lets you do this with custom oracle.
provides high availibility using multi az feautres.
Also,
![[Pasted image 20250413094151.png]]

it allows to customise the database host and OS.

---

- the fuck, theere is aurora global database, one that allows aurora to e global.
- i didnt think this was a feature of RDS, but only dynamoDB.
**Use an Amazon Aurora Global Database for the `games` table and use Amazon Aurora for the `users` and `games_played` tables**

Amazon Aurora is a MySQL and PostgreSQL-compatible relational database built for the cloud, that combines the performance and availability of traditional enterprise databases with the simplicity and cost-effectiveness of open source databases. Amazon Aurora features a distributed, fault-tolerant, self-healing storage system that auto-scales up to 128TB per database instance. Aurora is not an in-memory database.

Amazon Aurora Global Database is designed for globally distributed applications, allowing a single Amazon Aurora database to span multiple AWS regions. It replicates your data with no impact on database performance, enables fast local reads with low latency in each region, and provides disaster recovery from region-wide outages. Amazon Aurora Global Database is the correct choice for the given use-case.

For the given use-case, we, therefore, need to have two Aurora clusters, one for the global table (games table) and the other one for the local tables (users and games_played tables).

---

**Tier-1 (32 terabytes)**

Amazon Aurora features a distributed, fault-tolerant, self-healing storage system that auto-**scales up to 128TB** per database instance. It delivers high performance and availability with up to **15 low-latency read replicas**, point-in-time recovery, continuous backup to Amazon S3, and **replication across three Availability Zones (AZs).**

For Amazon Aurora, each Read Replica is associated with a priority **tier (0-15).** In the event of a failover, Amazon Aurora will promote the Read Replica that has the highest priority (the lowest numbered tier). **If two or more Aurora Replicas share the same priority, then Amazon RDS promotes the replica that is largest in size.** If two or more Aurora Replicas share the same priority and size, then Amazon Aurora promotes an arbitrary replica in the same promotion tier.

Therefore, for this problem statement, the Tier-1 (32 terabytes) replica will be promoted.

---

This is incorrect because while read replicas can improve performance for read-heavy workloads, they do not reduce query latency as effectively as an in-memory caching solution like ElastiCache.

**rds read replica vs elasticache.**

---

**Configure Amazon RDS automated backups. Set the retention period to 35 days and enable point-in-time recovery for the past 10 days. Use AWS Backup to retain additional backups for 120 days:** This is correct because RDS automated backups support up to 35 days of retention and point-in-time recovery. AWS Backup can extend the retention period to 120 days without additional complexity.  
**Create an Amazon RDS manual snapshot every week. Use an AWS Lambda function to delete snapshots that are older than 120 days:** This is incorrect because manual snapshot management introduces operational overhead and is not as scalable or reliable as RDS automated backups combined with AWS Backup.  
**Use AWS Backup to create a backup plan for Amazon RDS with a 120-day retention period. Enable point-in-time recovery by combining AWS Backup and RDS automated backups:** This is incorrect because while AWS Backup can retain backups for 120 days, it cannot directly handle point-in-time recovery, which requires native RDS automated backups.

---

- multi Az is region specific, inside one VPC

The issue here is latency with read queries being directed from Australia to UK which is great physical distance. A solution is required for improving read performance in Australia.

An Aurora global database consists of one primary AWS Region where your data is mastered, and up to five read-only, secondary AWS Regions. Aurora replicates data to the secondary AWS Regions with typical latency of under a second. You issue write operations directly to the primary DB instance in the primary AWS Region.

![](https://img-c.udemycdn.com/redactor/raw/2020-05-21_01-05-41-0e623951d5ed62017a22f93bb14c6c67.jpg)

This solution will provide better performance for users in the Australia Region for queries. Writes must still take place in the UK Region but read performance will be greatly improved.

**CORRECT:** "Migrate the database to an Amazon Aurora global database in MySQL compatibility mode. Configure read replicas in ap-southeast-2" is the correct answer.

**INCORRECT:** "Migrate the database to Amazon RDS for MySQL. Configure Multi-AZ in the Australian Region" is incorrect. The database is located in UK. If the database is migrated to Australia then the reverse problem will occur. Multi-AZ does not assist with improving query performance across Regions.

---
### IMPORTANT TO UNDERSTAND

You cannot enable/disable encryption in transit using the RDS management console or use a KMS key.

Download the AWS-provided root certificates. Use the certificates when connecting to the RDS DB instance.

---

bitchy one

![[Pasted image 20250415202815.png]]

- You cannot change the encryption status of an existing RDS DB instance.
- Encryption must be specified when creating the RDS DB instance. T
- The best way to encrypt an existing database is to take a snapshot, encrypt a copy of the snapshot and restore the snapshot to a new RDS DB instance.
- This results in an encrypted database that is a new instance. Applications must be updated to use the new RDS DB endpoint.
In this scenario as there is a high rate of change, the databases will be out of sync by the time the new copy is created and is functional. The best way to capture the changes between the source (unencrypted) and destination (encrypted) DB is to use AWS Database Migration Service (DMS) to synchronize the data.

---

GLoabal database:
![[Pasted image 20250416001606.png]]
Amazon Aurora Global Database is designed for globally distributed applications, allowing a single Amazon Aurora database to span multiple AWS regions. It replicates your data with no impact on database performance, enables fast local reads with low latency in each region, and provides disaster recovery from region-wide outages.

A global database can be configured in the European region and then the application tier in Europe will need to be configured to use the local database for reads/queries. The diagram below depicts an Aurora Global Database deployment.

---


A company operates an e-commerce application hosted on Amazon EC2 instances in an Auto Scaling group behind an Application Load Balancer (ALB). Customer transactions and order information are stored in an Amazon Aurora PostgreSQL DB cluster. The company wants to implement a disaster recovery (DR) plan to prepare for Region-wide outages. The DR solution must provide a recovery time objective (RTO) of 30 minutes. The DR infrastructure does not need to be operational unless the primary Region becomes unavailable.

Which solution will meet these requirements?


**Deploy the DR infrastructure in a second AWS Region, including an ALB and an Auto Scaling group with desired and maximum capacities set to zero. Convert the Aurora PostgreSQL DB cluster into an Aurora global database. Use Amazon Route 53 to configure active-passive failover**: This approach provides minimal operational overhead while meeting the 30-minute RTO. Aurora global database ensures replication with low latency, while Route 53 handles DNS failover.

**Deploy an ALB and Auto Scaling group in a second AWS Region. Set the Auto Scaling group desired capacity to a minimum value. Use Amazon RDS Cross-Region Read Replicas to replicate the Aurora DB cluster. Configure Amazon Route 53 for active-active failover**: This solution increases costs because active-active failover is unnecessary. Additionally, using read replicas does not provide write capabilities during a failover.

**Use AWS Backup to schedule regular backups of the Aurora DB cluster and EC2 instances. In the second AWS Region, create infrastructure using AWS CloudFormation templates upon failure. Configure Amazon Route 53 with a failover policy to redirect traffic**: While this reduces costs, it increases the RTO significantly due to the need to create infrastructure and restore data after a failure.

	**Deploy the DR infrastructure in a second AWS Region. Include an Aurora DB cluster configured with Cross-Region Replication and an ALB with the same configuration. Set up an Amazon CloudWatch alarm to increase the Auto Scaling group desired capacity upon failure**: This is less operationally efficient compared to the Aurora global database. Additionally, the solution introduces unnecessary complexity.

---


This is correct because RDS backup retention policies can only be applied to automated backups.

---

Aurora custom endpoints allow you to define a subset of replicas for specific workloads

---


Amazon Aurora Global Database is designed for globally distributed applications, allowing a single Amazon Aurora database to span multiple AWS regions. It replicates your data with no impact on database performance, enables fast local reads with low latency in each region, and provides disaster recovery from region-wide outages. Amazon Aurora Global Database is the correct choice for the given use-case.


---

On a database instance running with Amazon RDS encryption, data stored at rest in the underlying storage is encrypted, as are its automated backups, read replicas, and snapshots
this is about read replica between primary and the read replica instance


---


- RDS has auto scaling option which can be enabled later on for storage purposes.
- If your workload is unpredictable, you can enable storage autoscaling for an Amazon RDS DB instance. With storage autoscaling enabled, when Amazon RDS detects that you are running out of free database space it automatically scales up your storage. Amazon RDS starts a storage modification for an autoscaling-enabled DB instance when these factors apply:

Free available space is less than 10 percent of the allocated storage.

The low-storage condition lasts at least five minutes.

At least six hours have passed since the last storage modification.

The maximum storage threshold is the limit that you set for autoscaling the DB instance. You can't set the maximum storage threshold for autoscaling-enabled instances to a value greater than the maximum allocated storage.

Incorrect options:


---


there is nothing like a standby instance in aurora!!


---


You are not charged for the data transfer incurred in replicating data between your source DB instance and read replica within the same AWS Region.
- for different regions readrEPLICA you will be charged for data transfer