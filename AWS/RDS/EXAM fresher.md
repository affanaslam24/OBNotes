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

