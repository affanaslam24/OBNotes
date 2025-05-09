![[Pasted image 20250416132546.png]]

**Set up Amazon S3 to use Multi-Region Access Points in an active-active configuration with a single global endpoint. Configure S3 Cross-Region Replication:** This is correct because S3 Multi-Region Access Points allow the application to route user requests automatically to the nearest S3 bucket based on network conditions and proximity, minimizing latency and avoiding public network congestion. It also provides failover capabilities with minimal management effort.

**Implement an active-active design between the two Regions. Configure the application to use the regional S3 endpoints closest to the user:** This is incorrect because this solution requires the application to manage the routing and failover logic, increasing operational overhead.

**Use an active-passive configuration with S3 Multi-Region Access Points. Create a global endpoint for each of the Regions:** This is incorrect because active-passive configurations introduce delays in failover and require more manual intervention.

**Send user data to the regional S3 endpoints closest to the user. Configure an S3 cross-account replication rule to keep the S3 buckets synchronized:** This is incorrect because this approach does not optimize routing and requires manual failover, which increases management overhead.



this was so fucked up tricky for me, because i didnt know any of this.


---

A research organization wants to move its data analytics application to a serverless solution. The organization stores scientific data in an Amazon S3 bucket and needs the solution to support SQL queries on both existing and new data. The data must be encrypted at rest and replicated to a different AWS Region to ensure durability and compliance.

Which solution will meet these requirements with the LEAST operational overhead?


Overall explanation

**Create a new S3 bucket that uses server-side encryption with AWS KMS multi-Region keys (SSE-KMS). Configure Cross-Region Replication (CRR). Load the data into the new S3 bucket. Use Amazon Athena to query the data:** This is correct because SSE-KMS provides encryption at rest with multi-Region replication, and Athena offers a serverless SQL querying solution with minimal operational overhead.

**Create a new S3 bucket that uses server-side encryption with Amazon S3 managed keys (SSE-S3). Configure Cross-Region Replication (CRR). Load the data into the new S3 bucket. Use Amazon Redshift Spectrum to query the data:** This is incorrect because Redshift Spectrum is not a fully serverless solution and requires managing the Redshift cluster, increasing operational overhead.

**Configure Cross-Region Replication (CRR) on the existing S3 bucket. Use server-side encryption with Amazon S3 managed keys (SSE-S3). Use Amazon Athena to query the data:** This is incorrect because SSE-S3 does not provide the same level of security as SSE-KMS, which is required for compliance in many scenarios.

**Configure S3 Cross-Region Replication (CRR) on the existing S3 bucket. Use server-side encryption with AWS KMS multi-Region keys (SSE-KMS). Use AWS Glue for ETL and Amazon Redshift to query the data:** This is incorrect because AWS Glue and Redshift require additional management and are not as cost-efficient as Athena for simple SQL querying tasks.