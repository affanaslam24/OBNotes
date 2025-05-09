Upon a security review of your AWS account, an AWS consultant has found that a few Amazon RDS databases are unencrypted. As a Solutions Architect, what steps must be taken to encrypt the Amazon RDS databases?

Correct option:

**Take a snapshot of the database, copy it as an encrypted snapshot, and restore a database from the encrypted snapshot. Terminate the previous database**

Amazon Relational Database Service (Amazon RDS) makes it easy to set up, operate, and scale a relational database in the cloud. It provides cost-efficient and resizable capacity while automating time-consuming administration tasks such as hardware provisioning, database setup, patching and backups.

You can encrypt your Amazon RDS DB instances and snapshots at rest by enabling the encryption option for your Amazon RDS DB instances. Data that is encrypted at rest includes the underlying storage for DB instances, its automated backups, read replicas, and snapshots.

You can only enable encryption for an Amazon RDS DB instance when you create it, not after the DB instance is created. However, **because you can encrypt a copy of an unencrypted DB snapshot,** you can effectively add encryption to an unencrypted DB instance. That is, you can create a snapshot of your DB instance, and then create an encrypted copy of that snapshot. So this is the correct option.

Incorrect options:

**Create a Read Replica of the database, and encrypt the read replica. Promote the read replica as a standalone database, and terminate the previous database** - If the master is not encrypted, the read replicas cannot be encrypted. So this option is incorrect.

**Enable Multi-AZ for the database, and make sure the standby instance is encrypted. Stop the main database to that the standby database kicks in, then disable Multi-AZ** - Multi-AZ is to help with High Availability, not encryption. So this option is incorrect.

**Enable encryption on the Amazon RDS database using the AWS Console** - There is no direct option to encrypt an Amazon RDS database using the AWS Console.

# Steps to encrypt an un-encrypted RDS database: 1. Create a snapshot of the un-encrypted database 2. Copy the snapshot and enable encryption for the snapshot 3. Restore the database from the encrypted snapshot 4. Migrate applications to the new database, and delete the old database



---\




- First note that once something is enabled cant be suddenly changed and vice versa.
 - you can encrypt a copy of an unencrypted DB snapshot,
 - If the master is not encrypted, the read replicas cannot be encrypted
 - Multi-AZ is to help with High Availability, not encryption. 

---


![[Pasted image 20250417224335.png]]


verall explanation

Correct option:

**Create an encrypted snapshot of the database, share the snapshot, and allow access to the AWS Key Management Service (AWS KMS) encryption key**

You can share the AWS Key Management Service (AWS KMS) key that was used to encrypt the snapshot with any accounts that you want to be able to access the snapshot. You can share AWS KMS Key with another AWS account by adding the other account to the AWS KMS key policy.

Making an encrypted snapshot of the database will give the auditor a copy of the database, as required for the given use case.

Incorrect options:

**Create a snapshot of the database in Amazon S3 and assign an IAM role to the auditor to grant access to the object in that bucket** - Amazon RDS stores the DB snapshots in the Amazon S3 bucket belonging to the same AWS region where the Amazon RDS instance is located. Amazon RDS stores these on your behalf and you do not have direct access to these snapshots in Amazon S3, so it's not possible to grant access to the snapshot objects in Amazon S3.

**Export the database contents to text files, store the files in Amazon S3, and create a new IAM user for the auditor with access to that bucket** - This solution is feasible though not optimal. It requires a lot of unnecessary work and is difficult to audit when such bulk data is exported into text files.

**Set up a read replica of the database and configure IAM standard database authentication to grant the auditor access** - Read Replicas make it easy to elastically scale out beyond the capacity constraints of a single DB instance for read-heavy database workloads. Creating Read Replicas for audit purposes is overkill. Also, the question mentions that the auditor needs to have their own copy of the database, which is not possible with replicas.
