**AWS Database Migration Service (AWS DMS)** is a cloud service that makes it easy to migrate relational databases, data warehouses, NoSQL databases, and other types of data stores. You can use AWS DMS to migrate your data into the AWS Cloud, between on-premises instances (through an AWS Cloud setup) or between combinations of cloud and on-premises setups. With AWS DMS, you can perform one-time migrations, and you can replicate ongoing changes to keep sources and targets in sync.

![](https://media.tutorialsdojo.com/aws-dms-tutorialsdojo-SSL-endpoint-saa-c03.png)

You can migrate data to Amazon S3 using AWS DMS from any of the supported database sources. When using Amazon S3 as a target in an AWS DMS task, both full load and change data capture (CDC) data is written to comma-separated value (.csv) format by default.

The comma-separated value (.csv) format is the default storage format for Amazon S3 target objects. For more compact storage and faster queries, you can instead use Apache Parquet (.parquet) as the storage format.

You can encrypt connections for source and target endpoints by using Secure Sockets Layer (SSL). To do so, you can use the AWS DMS Management Console or AWS DMS API to assign a certificate to an endpoint. You can also use the AWS DMS console to manage your certificates.

Not all databases use SSL in the same way. Amazon Aurora MySQL-Compatible Edition uses the server name, the endpoint of the primary instance in the cluster, as the endpoint for SSL. An Amazon Redshift endpoint already uses an SSL connection and does not require an SSL connection set up by AWS DMS.

Hence, the correct answer is: **Create a full load and change data capture (CDC) replication task using AWS Database Migration Service (AWS DMS). Add a new Certificate Authority (CA) certificate and create an AWS DMS endpoint with SSL.**

The option that says: **Set up a full load replication task using AWS Database Migration Service (AWS DMS). Launch an AWS DMS endpoint with SSL using the AWS Network Firewall service** is incorrect because a full load replication task alone won't capture ongoing changes to the database. You still need to implement a change data capture (CDC) replication to copy the recent changes after the migration. Moreover, the AWS Network Firewall service is not capable of creating an AWS DMS endpoint with SSL. The Certificate Authority (CA) certificate can be directly uploaded to the AWS DMS console without the AWS Network Firewall at all.

The