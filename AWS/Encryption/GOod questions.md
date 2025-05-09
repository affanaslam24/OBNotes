A highly sensitive application runs on Amazon EC2 instances using EBS volumes. The application stores data temporarily on Amazon EBS volumes during processing before saving results to an Amazon RDS database. The company’s security team mandate that the sensitive data must be encrypted at rest.

Which solution should a Solutions Srchitect recommend to meet this requirement?


encryption at reest is the key:


As the data is stored both in the EBS volumes (temporarily) and the RDS database, both the EBS and RDS volumes must be encrypted at rest. This can be achieved by enabling encryption at creation time of the volume and AWS KMS keys can be used to encrypt the data. This solution meets all requirements.

**CORRECT:** "Configure encryption for the Amazon EBS volumes and Amazon RDS database with AWS KMS keys" is the correct answer.

**INCORRECT:** "Use AWS Certificate Manager to generate certificates that can be used to encrypt the connections between the EC2 instances and RDS" is incorrect. This would encrypt the data in-transit but not at-rest.

**INCORRECT:** "Use Amazon Data Lifecycle Manager to encrypt all data as it is stored to the EBS volumes and RDS database" is incorrect. DLM is used for automating the process of taking and managing snapshots for EBS volumes.

**INCORRECT:** "Configure SSL/TLS encryption using AWS KMS customer master keys (CMKs) to encrypt database volumes" is incorrect. You cannot configure SSL/TLS encryption using KMS CMKs or use SSL/TLS to encrypt data at rest.


