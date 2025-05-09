A developer needs to implement an AWS Lambda function in AWS account A that accesses an Amazon Simple Storage Service (Amazon S3) bucket in AWS account B.

As a Solutions Architect, which of the following will you recommend to meet this requirement?

Correct option:

**Create an IAM role for the AWS Lambda function that grants access to the Amazon S3 bucket. Set the IAM role as the AWS Lambda function's execution role. Make sure that the bucket policy also grants access to the AWS Lambda function's execution role**
*******
If the IAM role that you create for the Lambda function is in the same AWS account as the bucket, then you don't need to grant Amazon S3 permissions on both the IAM role and the bucket policy. Instead, you can grant the permissions on the IAM role and then verify that the bucket policy doesn't explicitly deny access to the Lambda function role. If the IAM role and the bucket are in different accounts, then you need to grant Amazon S3 permissions on both the IAM role and the bucket policy. Therefore, this is the right way of giving access to AWS Lambda for the given use-case.
********
Complete list of steps to be followed:

![](https://assets-pt.media.datacumulus.com/aws-saa-pt/assets/pt2-q16-i1.jpg)

via - [https://aws.amazon.com/premiumsupport/knowledge-center/lambda-execution-role-s3-bucket/](https://aws.amazon.com/premiumsupport/knowledge-center/lambda-execution-role-s3-bucket/)

Incorrect options:

**AWS Lambda cannot access resources across AWS accounts. Use Identity federation to work around this limitation of Lambda** - This is an incorrect statement, used only as a distractor.

**Create an IAM role for the AWS Lambda function that grants access to the Amazon S3 bucket. Set the IAM role as the Lambda function's execution role and that would give the AWS Lambda function cross-account access to the Amazon S3 bucket** - When the execution role of AWS Lambda and Amazon S3 bucket to be accessed are from different accounts, then you need to grant Amazon S3 bucket access permissions to the IAM role and also ensure that the bucket policy grants access to the AWS Lambda function's execution role.

**The Amazon S3 bucket owner should make the bucket public so that it can be accessed by the AWS Lambda function in the other AWS account** - Making the Amazon S3 bucket public for the given use-case will be considered as a security bad practice. It's usually done for very few use-cases such as hosting a website on Amazon S3. Therefore this option is incorrect.

Reference:

[https://aws.amazon.com/premi](https://aws.amazon.com/premiumsupport/knowledge-center/lambda-execution-role-s3-bucket/)