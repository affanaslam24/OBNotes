**Use DynamoDB global tables to replicate data automatically across multiple Regions. Deploy the tables in on-demand capacity mode to handle workload variability:** This is correct because DynamoDB global tables provide automatic multi-Region replication, ensuring low latency and high availability for a global user base. On-demand capacity mode is a cost-effective choice for workloads with unpredictable demand, as it adjusts capacity based on usage.

**Deploy DynamoDB tables in a single AWS Region using provisioned capacity mode. Use DynamoDB Streams to replicate data asynchronously to a secondary Region for failover:** This is incorrect because using DynamoDB Streams for cross-Region replication requires a custom implementation, which increases operational overhead. Additionally, a single primary Region does not ensure low latency for a global user base.

**Use Amazon S3 to store user data and replicate the data across multiple Regions using S3 Cross-Region Replication. Use AWS Lambda to perform real-time data updates for the application:** This is incorrect because S3 is not designed for transactional, low latency use cases like a social media platform. DynamoDB is the better choice for structured, real-time data access.

**Use DynamoDB Accelerator (DAX) to reduce read latency for frequently accessed items. Deploy DynamoDB tables in a single Region and use manual Cross-Region Replication to replicate data to other Regions for fault tolerance:** This is incorrect because DAX reduces read latency but does not provide global availability or automatic replication. Manual Cross-Region Replication adds operational complexity and is less reliable than global tables.


---


A stock trading startup company has a custom web application to sell trading data to its users online. The company uses Amazon DynamoDB to store its data and wants to build a new service that sends an alert to the managers of four internal teams every time a new trading event is recorded. The company does not want this new service to affect the performance of the current application.

What should a solutions architect do to meet these requirements with the LEAST amount of operational overhead?


DynamoDB Streams captures a time-ordered sequence of item-level modifications in any DynamoDB table and stores this information in a log for up to 24 hours. Applications can access this log and view the data items as they appeared before and after they were modified, in near-real time. This is the native way to handle this within DynamoDB, therefore will incur the least amount of operational overhead.

**CORRECT:** "On the table, enable Amazon DynamoDB Streams. Subscriptions can be made to a single Amazon Simple Notification Service (Amazon SNS) topic using triggers” is the correct answer (as explained above.)

**INCORRECT:** "Write new event data to the table using DynamoDB transactions. The transactions should be configured to notify internal teams” is incorrect. With Amazon DynamoDB transactions, you can group multiple actions together and submit them as a single all-or-nothing TransactWriteItems or TransactGetItems operation. The following sections describe API operations, capacity management, best practices, and other details about using transactional operations in DynamoDB. This is not suitable for this use case.

**INCORRECT:** "Use the current application to publish a message to four Amazon Simple Notification Service (Amazon SNS) topics. Each team should subscribe to one topic” is incorrect. Using four separate SNS topics will take a significant amount of overhead, and this functionality can be managed natively within DynamoDB using DynamoDB streams.

**INCORRECT:** "Create a custom attribute for each record to flag new items. A cron job can be written to scan the table every minute for new items and notify an Amazon Simple Queue Service (Amazon SQS) queue” is incorrect. Writing a CRON job also takes significant overhead compared to using DynamoDB streams.


---


Reapreplica and elasticache

The performance issues can be easily resolved by offloading the SQL queries the business analysts are performing to a read replica. This ensures that data that is being queries is up to date and the existing web application does not require any modifications to take place.

**CORRECT:** "Create a read replica of the primary database and instruct the business analysts to direct queries to the replica" is the correct answer.

**INCORRECT:** "Export the data to Amazon S3 and instruct the business analysts to run their queries using Amazon Athena" is incorrect. The data must be the latest data and this method would therefore require constant exporting of the data.

**INCORRECT:** "Load the data into an Amazon Redshift cluster and instruct the business analysts to run their queries against the cluster" is incorrect. This is another solution that requires exporting the loading the data which means over time it will become out of date.

**INCORRECT:** "Load the data into Amazon ElastiCache and instruct the business analysts to run their queries against the ElastiCache endpoint" is incorrect. It will be much easier to create a read replica. ElastiCache requires updates to the application code so should be avoided in this example.


A group of business analysts perform read-only SQL queries on an Amazon RDS database. The queries have become quite numerous and the database has experienced some performance degradation. The queries must be run against the latest data. A Solutions Architect must solve the performance problems with minimal changes to the existing web application.

What should the Solutions Architect recommend?

