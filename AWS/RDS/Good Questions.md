A retail company uses an Amazon Aurora MySQL DB cluster for its order management system. The cluster includes eight Aurora Replicas. The company wants to ensure that reporting queries from its analytics team are automatically distributed across three specific Aurora Replicas that have higher compute and memory capacity than the rest of the cluster.

Which solution will meet these requirements?'



**Create and use a custom endpoint that targets the three high-capacity replicas:** This is correct because Aurora custom endpoints allow you to define a subset of replicas for specific workloads. By creating a custom endpoint, the reporting queries can be automatically distributed across the three high-capacity replicas without involving the rest of the cluster.

**Use the reader endpoint to automatically distribute reporting queries across all replicas in the cluster:** This is incorrect because the reader endpoint distributes queries across all Aurora Replicas in the cluster, which does not restrict queries to the desired three replicas.

**Create a cluster clone for the reporting workload and use the writer endpoint of the cloned cluster:** This is incorrect because creating a cluster clone duplicates data unnecessarily, which increases costs and operational complexity. Additionally, the writer endpoint does not distribute queries among replicas.

**Direct reporting queries to the instance endpoints of the three high-capacity replicas:** This is incorrect because managing connections manually to individual instance endpoints is inefficient and does not provide automated query distribution across the replicas.

---


- serverless
- relational
- dynamic scaling
- autimatic backup 
- low overhead
A fitness application company is launching a platform to track user activity, workout logs, and personalized settings. The database must support structured data, allow for transactions between related data, and dynamically scale to handle unpredictable traffic spikes during peak hours. The solution must also support automated backups and minimize operational management.

Which solution will meet these requirements MOST cost-effectively?


**Use Amazon Aurora Serverless v2 to store the data. Enable serverless auto-scaling and configure automated backups to Amazon S3 with a 7-day retention period:** This is correct because Aurora Serverless supports relational data, transactions, and complex queries while scaling seamlessly to meet workload demands. It integrates natively with Amazon S3 for automated backups, eliminating operational overhead while remaining cost-effective.

**Use Amazon DynamoDB with on-demand capacity mode to handle fluctuating traffic. Enable DynamoDB Point-in-Time Recovery (PITR) for automated backups:** This is incorrect because, while DynamoDB is cost-effective and highly scalable, it lacks native support for relational data and transactions, which are required in this scenario. For structured data with relational dependencies, Aurora Serverless is the better fit.

**Deploy an open-source database on Amazon EC2 Spot Instances in an Auto Scaling group. Configure daily backups to Amazon S3 Intelligent-Tiering for cost optimization:** This is incorrect because managing an open-source database on EC2 Spot Instances introduces operational complexity and risks interruptions. Additionally, Spot Instances are less suitable for workloads requiring high availability.

**Deploy an Amazon RDS MySQL instance in a multi-AZ configuration. Use provisioned IOPS storage and configure automated backups to Amazon S3 Glacier Flexible Retrieval for long-term retention:** This is incorrect because provisioned IOPS increases costs unnecessarily, and Glacier Flexible Retrieval is unsuitable for backups requiring quick access.


---


### using RDS and Multi Az at the same time

An e-commerce application uses an Amazon Aurora Multi-AZ deployment for its database. While analyzing the performance metrics, the engineering team has found that the database reads are causing high input/output (I/O) and adding latency to the write requests against the database.

As an AWS Certified Solutions Architect Associate, what would you recommend to separate the read requests from the write requests?


**Set up a read replica and modify the application to use the appropriate endpoint**

An Amazon Aurora DB cluster consists of one or more DB instances and a cluster volume that manages the data for those DB instances. An Aurora cluster volume is a virtual database storage volume that spans multiple Availability Zones (AZs), with each Availability Zone (AZ) having a copy of the DB cluster data. Two types of DB instances make up an Aurora DB cluster:

Primary DB instance – Supports read and write operations, and performs all of the data modifications to the cluster volume. Each Aurora DB cluster has one primary DB instance.

Aurora Replica – Connects to the same storage volume as the primary DB instance and supports only read operations. Each Aurora DB cluster can have up to 15 Aurora Replicas in addition to the primary DB instance. Aurora automatically fails over to an Aurora Replica in case the primary DB instance becomes unavailable. You can specify the failover priority for Aurora Replicas. Aurora Replicas can also offload read workloads from the primary DB instance.

![](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/images/AuroraArch001.png)

via - [https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Overview.html](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Overview.html)

Aurora Replicas have two main purposes. You can issue queries to them to scale the read operations for your application. You typically do so by connecting to the reader endpoint of the cluster. That way, Aurora can spread the load for read-only connections across as many Aurora Replicas as you have in the cluster. Aurora Replicas also help to increase availability. If the writer instance in a cluster becomes unavailable, Aurora automatically promotes one of the reader instances to take its place as the new writer.

While setting up a Multi-AZ deployment for Aurora, you create an Aurora replica or reader node in a different Availability Zone (AZ).

Multi-AZ for Aurora:

![](https://assets-pt.media.datacumulus.com/aws-saa-pt/assets/pt2-q13-i1.jpg)

You use the reader endpoint for read-only connections for your Aurora cluster. This endpoint uses a load-balancing mechanism to help your cluster handle a query-intensive workload. The reader endpoint is the endpoint that you supply to applications that do reporting or other read-only operations on the cluster. The reader endpoint load-balances connections to available Aurora Replicas in an Aurora DB cluster.

![](https://assets-pt.media.datacumulus.com/aws-saa-pt/assets/pt2-q13-i2.jpg)

via - [https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Overview.Endpoints.html](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Overview.Endpoints.html)

Incorrect options:

**Provision another Amazon Aurora database and link it to the primary database as a read replica** - You cannot provision another Aurora database and then link it as a read-replica for the primary database. This option is ruled out.

**Configure the application to read from the Multi-AZ standby instance** - This option has been added as a distractor as Aurora does not have any entity called standby instance. You create a standby instance while setting up a Multi-AZ deployment for Amazon RDS and NOT for Aurora.

Multi-AZ for Amazon RDS:

![](https://assets-pt.media.datacumulus.com/aws-saa-pt/assets/pt2-q13-i3.jpg)

**Activate read-through caching on the Amazon Aurora database** - Amazon Aurora does not have built-in support for read-through caching, so this option just serves as a distractor. To implement caching, you will need to integrate something like Amazon ElastiCache and that would need code changes for the application.



### **Can you use both Multi-AZ and Read Replicas with Amazon Aurora?**

**Yes, absolutely!**

#### ✅ **Aurora automatically uses Multi-AZ architecture**

- Aurora clusters have a **single writer** and **multiple readers**.
    
- All instances (writer and readers) are spread across **multiple Availability Zones**.
    
- So, **Multi-AZ is built-in** — no need to explicitly enable it.
    

#### ✅ **Aurora Read Replicas:**

- You can add up to **15 Aurora Replicas** for read scaling.
    
- These replicas are part of the same cluster and **can be in different AZs**.
    
- Aurora uses **shared distributed storage**, so replication is **much faster** than RDS.
    

#### ✅ **High Availability + Read Scaling:**

When you create an Aurora cluster:

- You get Multi-AZ HA automatically (writer + storage spread across AZs).
    
- You can **add Aurora Replicas** in other AZs for read scaling and faster failover.

|Feature|RDS|Aurora|
|---|---|---|

|   |   |   |
|---|---|---|
|Multi-AZ|Needs to be enabled manually|Always enabled (built-in architecture)|

|   |   |   |
|---|---|---|
|Read Replicas|Optional|Optional (up to 15, very fast)|

|   |   |   |
|---|---|---|
|Failover|Multi-AZ: Automatic|Aurora: Automatic to replica in another AZ|

|             |              |                                     |
| ----------- | ------------ | ----------------------------------- |
| Replication | Asynchronous | Near real-time (via shared storage) |