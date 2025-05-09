- kms keys can be multi regional, but that needs to be done prior to it being created.
- A key already created as asingle regional cannot be changed.

- a key cannot be shared between regions as well.

Now, knowing all this look into this question-


A company has historically operated only in the `us-east-1` region and stores encrypted data in Amazon S3 using SSE-KMS. As part of enhancing its security posture as well as improving the backup and recovery architecture, the company wants to store the encrypted data in Amazon S3 that is replicated into the `us-west-1` AWS region. The security policies mandate that the data must be encrypted and decrypted using the same key in both AWS regions.

Which of the following represents the best solution to address these requirements?


**Create a new Amazon S3 bucket in the `us-east-1` region with replication enabled from this new bucket into another bucket in `us-west-1` region. Enable SSE-KMS encryption on the new bucket in `us-east-1` region by using an AWS KMS multi-region key. Copy the existing data from the current Amazon S3 bucket in `us-east-1` region into this new Amazon S3 bucket in `us-east-1` region**

AWS KMS supports multi-region keys, which are AWS KMS keys in different AWS regions that can be used interchangeably – as though you had the same key in multiple regions. Each set of related multi-region keys has the same key material and key ID, so you can encrypt data in one AWS region and decrypt it in a different AWS region without re-encrypting or making a cross-region call to AWS KMS.

You can use multi-region AWS KMS keys in Amazon S3. However, Amazon S3 currently treats multi-region keys as though they were single-region keys, and does not use the multi-region features of the key.

Multi-region AWS KMS keys:

![](https://assets-pt.media.datacumulus.com/aws-saa-pt/assets/pt2-q46-i1.jpg)

via - [https://docs.aws.amazon.com/kms/latest/developerguide/multi-region-keys-overview.html](https://docs.aws.amazon.com/kms/latest/developerguide/multi-region-keys-overview.html)

For the given use case, you must create a new bucket in the `us-east-1` region with replication enabled from this new bucket into another bucket in `us-west-1` region. This would ensure that the data is available in another region for backup and recovery purposes. You should also enable SSE-KMS encryption on the new bucket in `us-east-1` region by using an AWS KMS multi-region key so that the data can be encrypted and decrypted using the same key in both AWS regions. Since the existing data in the current bucket was encrypted using the AWS KMS key restricted to the `us-east-1` region, so data must be copied to the new bucket in `us-east-1` region for replication as well as multi-region KMS key based encryption to kick-in.

To require server-side encryption of all objects in a particular Amazon S3 bucket, you can use a policy. For example, the following bucket policy denies the upload object (s3:PutObject) permission to everyone if the request does not include the x-amz-server-side-encryption header requesting server-side encryption with SSE-KMS.

```
{
   "Version":"2012-10-17",
   "Id":"PutObjectPolicy",
   "Statement":[{
         "Sid":"DenyUnEncryptedObjectUploads",
         "Effect":"Deny",
         "Principal":"*",
         "Action":"s3:PutObject",
         "Resource":"arn:aws:s3:::DOC-EXAMPLE-BUCKET1/*",
         "Condition":{
            "StringNotEquals":{
               "s3:x-amz-server-side-encryption":"aws:kms"
            }
         }
      }
   ]
}
```

The following example IAM policies show statements for using AWS KMS server-side encryption with replication.

In this example, the encryption context is the object ARN. If you use SSE-KMS with an Amazon S3 Bucket Key enabled, you must use the bucket ARN as the encryption context.

```
{
    "Version": "2012-10-17",
    "Statement": [{
            "Action": ["kms:Decrypt"],
            "Effect": "Allow",
            "Resource": "List of AWS KMS key ARNs used to encrypt source objects.",
            "Condition": {
                "StringLike": {
                    "kms:ViaService": "s3.source-bucket-region.amazonaws.com",
                    "kms:EncryptionContext:aws:s3:arn": "arn:aws:s3:::source-bucket-name/key-prefix1/*"
                }
            }
        },

        {
            "Action": ["kms:Encrypt"],
            "Effect": "Allow",
            "Resource": "AWS KMS key ARNs (for the AWS Region of the destination bucket 1). Used to encrypt object replicas created in destination bucket 1.",
            "Condition": {
                "StringLike": {
                    "kms:ViaService": "s3.destination-bucket-1-region.amazonaws.com",
                    "kms:EncryptionContext:aws:s3:arn": "arn:aws:s3:::destination-bucket-name-1/key-prefix1/*"
                }
            }
        },
        {
            "Action": ["kms:Encrypt"],
            "Effect": "Allow",
            "Resource": "AWS KMS key ARNs (for the AWS Region of destination bucket 2). Used to encrypt object replicas created in destination bucket 2.",
            "Condition": {
                "StringLike": {
                    "kms:ViaService": "s3.destination-bucket-2-region.amazonaws.com",
                    "kms:EncryptionContext:aws:s3:arn": "arn:aws:s3:::destination-bucket-2-name/key-prefix1*"
                }
            }
        }
    ]
}
```

Incorrect options:

**Change the AWS KMS single region key used for the current Amazon S3 bucket into an AWS KMS multi-region key. Enable Amazon S3 batch replication for the existing data in the current bucket in `us-east-1` region into another bucket in `us-west-1` region** - Amazon S3 batch replication can certainly be used to replicate the existing data in the current bucket in `us-east-1` region into another bucket in `us-west-1` region.

However, you cannot convert an existing single-Region key to a multi-Region key. This design ensures that all data protected with existing single-Region keys maintain the same data residency and data sovereignty properties. So this option is incorrect.

**Enable replication for the current bucket in `us-east-1` region into another bucket in `us-west-1` region. Share the existing AWS KMS key from `us-east-1` region to `us-west-1` region** - You cannot share an AWS KMS key to another region, so this option is incorrect.

**Create an Amazon CloudWatch scheduled rule to invoke an AWS Lambda function to copy the daily data from the source bucket in `us-east-1` region to the destination bucket in `us-west-1` region. Provide AWS KMS key access to the AWS Lambda function for encryption and decryption operations on the data in the source and destination Amazon S3 buckets** - This option is a distractor as the daily frequency of data replication would result in significant data loss in case of a disaster. In addition, this option involves significant development effort to create the functionality to reliably replicate the data from source to destination buckets. So this option is not the best fit for the given use case.

References: