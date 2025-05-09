![[Pasted image 20250416143434.png]]

**Collect survey responses via an Amazon API Gateway endpoint integrated with Amazon Kinesis Data Firehose. Configure Firehose to stream the data to an Amazon S3 bucket. Use S3 Event Notifications to invoke an AWS Lambda function that calls Amazon Comprehend for sentiment analysis and writes results to an Amazon DynamoDB table with TTL configured to delete records after 12 months:**

This is correct because this architecture is highly scalable and cost-effective. Kinesis Data Firehose automatically scales to handle large volumes of data, and S3 provides reliable storage for raw survey responses. Using Lambda for sentiment analysis with Amazon Comprehend reduces operational complexity, and DynamoDB with TTL ensures data is stored efficiently for 12 months.

**Send survey responses to an Amazon EventBridge rule, which routes the data to an AWS Step Functions workflow. Use Step Functions to trigger AWS Lambda for data processing and sentiment analysis with Amazon Comprehend. Store the results in an Amazon DynamoDB table, and use DynamoDB's TTL feature to expire data after 12 months:**

This is incorrect because using EventBridge and Step Functions adds unnecessary complexity to the workflow. Kinesis Data Firehose with S3 provides a simpler and more efficient mechanism for streaming and storing data.

**Write survey responses directly to an Amazon Redshift database. Configure Amazon Redshift ML to perform sentiment analysis on the feedback data in real time. Use Amazon S3 to archive the processed results, and configure lifecycle policies to delete S3 objects after 12 months:**

This is incorrect because Amazon Redshift is better suited for analytical queries and is not optimized for real-time sentiment analysis. This solution introduces higher costs and complexity compared to using Amazon Comprehend and DynamoDB.

**Deploy an on-premises server that receives survey responses via a REST API. Process the data locally, use a custom machine learning model for sentiment analysis, and upload results to Amazon S3. Use Amazon S3 lifecycle policies to delete the data after 12 months:**

This is incorrect because deploying and managing on-premises servers increases operational overhead. AWS services like Lambda and Comprehend provide a more scalable and managed solution for this use case.


---
![[Pasted image 20250416151415.png]]


Firstly, S3 is a highly available and durable place to store these JSON documents that will be written once and read many times (WORM). As this application runs thousands of times per day, AWS Lambda would be ideal to use as it will scale whenever the application needs to be ran, and Python is a runtime environment that is natively supported by AWS Lambda, whenever the events arrive in the S3 bucket, and this could be easily achieved using S3 event notifications. Finally Amazon Aurora is a highly available and durable AWS managed database. Amazon Aurora automatically maintains six copies of your data across three Availability Zones (AZs) to adhere to your redundancy requirements.

**CORRECT:** "Put the JSON documents in an Amazon S3 bucket. As documents arrive in the S3 bucket, create an AWS Lambda function that runs Python code to process them. Use Amazon Aurora DB clusters to store the results" is the correct answer (as explained above.)

**INCORRECT:** "Build an S3 bucket to place the JSON documents in. Run the Python code on multiple Amazon EC2 instances to process the documents. Store the results in a database using the Amazon Aurora Database engine” is incorrect.

Multiple EC2 instances could work, however if you wanted to use EC2 to process the JSON documents you would need to either leave the EC2 instances running all the time (not cost effective) or have them spin up and spin down thousands of times per day (this would be slow and not ideal).

**INCORRECT:** "Create an Amazon Elastic Block Store (Amazon EBS) volume for the JSON documents. Attach the volume to multiple Amazon EC2 instances using the EBS Multi-Attach feature. Process the documents with Python code on the EC2 instances and then extract the results to an Amazon RDS DB instance" is incorrect.

EBS is not optimized for write once read many use-cases, and if you wanted to use EC2 to process the JSON documents you would need to either leave the EC2 instances running all the time (not cost effective) or have them spin up and spin down thousands of times per day (this would be slow and not ideal).

**INCORRECT:** "The JSON documents should be queued as messages in the Amazon Simple Queue Service (Amazon SQS). Using the Amazon Elastic Container Service (Amazon ECS) with the Amazon EC2 launch type, deploy the Python code as a container. The container can be used to process SQS messages. Using Amazon RDS, store the results” is incorrect.


---


A big data consulting firm needs to set up a data lake on Amazon S3 for a Health-Care client. The data lake is split in raw and refined zones. For compliance reasons, the source data needs to be kept for a minimum of 5 years. The source data arrives in the raw zone and is then processed via an AWS Glue based extract, transform, and load (ETL) job into the refined zone. The business analysts run ad-hoc queries only on the data in the refined zone using Amazon Athena. The team is concerned about the cost of data storage in both the raw and refined zones as the data is increasing at a rate of 1 terabyte daily in each zone.

As a solutions architect, which of the following would you recommend as the MOST cost-optimal solution?


**Setup a lifecycle policy to transition the raw zone data into Amazon S3 Glacier Deep Archive after 1 day of object creation**

You can manage your objects so that they are stored cost-effectively throughout their lifecycle by configuring their Amazon S3 Lifecycle. An S3 Lifecycle configuration is a set of rules that define actions that Amazon S3 applies to a group of objects. For example, you might choose to transition objects to the Amazon S3 Standard-IA storage class 30 days after you created them, or archive objects to the Amazon S3 Glacier storage class one year after creating them.

For the given use-case, the raw zone consists of the source data, so it cannot be deleted due to compliance reasons. Therefore, you should use a lifecycle policy to transition the raw zone data into Amazon S3 Glacier Deep Archive after 1 day of object creation.

Please read more about Amazon S3 Object Lifecycle Management:

![](https://assets-pt.media.datacumulus.com/aws-saa-pt/assets/pt2-q34-i1.jpg)

via - [https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html](https://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html)

**Use AWS Glue ETL job to write the transformed data in the refined zone using a compressed file format**

AWS Glue is a fully managed extract, transform, and load (ETL) service that makes it easy for customers to prepare and load their data for analytics. You cannot transition the refined zone data into Amazon S3 Glacier Deep Archive because it is used by the business analysts for ad-hoc querying. Therefore, the best optimization is to have the refined zone data stored in a compressed format via the Glue job. The compressed data would reduce the storage cost incurred on the data in the refined zone.

Please see this example for a AWS Glue ETL Pipeline:

![](https://d1.awsstatic.com/Products/product-name/diagrams/product-page-diagram_Glue_Event-driven-ETL-Pipelines.e24d59bb79a9e24cdba7f43ffd234ec0482a60e2.png)

via - [https://aws.amazon.com/glue/](https://aws.amazon.com/glue/)

Incorrect options:

**Create an AWS Lambda function based job to delete the raw zone data after 1 day** - As mentioned in the use-case, the source data needs to be kept for a minimum of 5 years for compliance reasons. Therefore the data in the raw zone cannot be deleted after 1 day.

**Setup a lifecycle policy to transition the refined zone data into Amazon S3 Glacier Deep Archive after 1 day of object creation** - You cannot transition the refined zone data into Amazon S3 Glacier Deep Archive because it is used by the business analysts for ad-hoc querying. Hence this option is incorrect.

**Use AWS Glue ETL job to write the transformed data in the refined zone using CSV format** - It is cost-optimal to write the data in the refined zone using a compressed format instead of CSV format. The compressed data would reduce the storage cost incurred on the data in the refined zone. So, this option is incorrect.

References:
