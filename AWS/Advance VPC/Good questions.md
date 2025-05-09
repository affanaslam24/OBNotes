![[Pasted image 20250416115723.png]]


Private access to public services such as Amazon S3 can be achieved by creating a VPC endpoint in the VPC. For S3 this would be a gateway endpoint. The bucket policy can then be configured to restrict access to the S3 endpoint only which will ensure that only services originating from the VPC will be granted access.

![](https://img-c.udemycdn.com/redactor/raw/test_question_description/2021-02-25_12-15-18-8ca86e9211911c46e6ebba4877ad1dca.jpg)

**CORRECT:** "Create a VPC endpoint for Amazon S3" is a correct answer.

**CORRECT:** "Apply a bucket policy to restrict access to the S3 endpoint" is also a correct answer.

**INCORRECT:** "Enable default encryption on the bucket" is incorrect. This will encrypt data at rest but does not restrict access.

**INCORRECT:** "Create a peering connection to the S3 bucket VPC" is incorrect. You cannot create a peering connection to S3 as it is a public service and does not run in a VPC.

**INCORRECT:** "Apply an IAM policy to a VPC peering connection" is incorrect. You cannot apply an IAM policy to a peering connection.


	