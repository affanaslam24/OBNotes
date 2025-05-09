AWS Key Management Service (KMS) makes it easy for you to create and manage cryptographic keys and control their use across a wide range of AWS services and in your applications. AWS KMS is a secure and resilient service that uses hardware security modules that have been validated under FIPS 140-2.

Deleting an AWS KMS key in AWS Key Management Service (AWS KMS) is destructive and potentially dangerous. Therefore, AWS KMS enforces a waiting period. To delete a KMS key in AWS KMS you schedule key deletion. You can set the waiting period from a minimum of 7 days up to a maximum of 30 days. The default waiting period is 30 days. During the waiting period, the KMS key status and key state is Pending deletion. To recover the KMS key, you can cancel key deletion before the waiting period ends. After the waiting period ends you cannot cancel key deletion, and AWS KMS deletes the KMS key.


- keynote is,, can be in pending state between 7 t o30 days.

![[Pasted image 20250413200133.png]]

![[Pasted image 20250413200139.png]]

---

A developer created an application that uses Amazon EC2 and an Amazon RDS MySQL database instance. The developer stored the database user name and password in a configuration file on the root EBS volume of the EC2 application instance. A Solutions Architect has been asked to design a more secure solution.

What should the Solutions Architect do to achieve this requirement?

The key problem here is having plain text credentials stored in a file. Even if you encrypt the volume there is still as security risk as the credentials are loaded by the application and passed to RDS.

The best way to secure this solution is to get rid of the credentials completely by using an IAM role instead. The IAM role can be assigned permissions to the database instance and can be attached to the EC2 instance. The instance will then obtain temporary security credentials from AWS STS which is much more secure.


---


If you use KMS keys, you can use AWS KMS through the AWS Management Console or the AWS KMS API to do the following:

1. Centrally create, view, edit, monitor, enable or disable, rotate, and schedule deletion of KMS keys.
    
2. Define the policies that control how and by whom KMS keys can be used.
    
3. Audit their usage to prove that they are being used correctly. Auditing is supported by the AWS KMS API, but not by the AWS KMSAWS Management Console.
    

When you enable automatic key rotation for a KMS key, AWS KMS generates new cryptographic material for the KMS key every year.

AWS KMS keys:

![](https://assets-pt.media.datacumulus.com/aws-saa-pt/assets/pt2-q50-i2.jpg)

via - [https://docs.aws.amazon.com/kms/latest/developerguide/rotate-keys.html](https://docs.aws.amazon.com/kms/latest/developerguide/rotate-keys.html)

For the given use case, you can set up server-side encryption with AWS KMS Keys (SSE-KMS) with automatic key rotation.

Incorrect options:

**Server-side encryption with AWS Key Management Service (AWS KMS) keys (SSE-KMS) with manual key rotation** - Although it is possible to manually rotate the AWS KMS key, it is not the best fit solution as it is not operationally efficient.

**Server-side**