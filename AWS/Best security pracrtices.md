Here are some of the best practices while creating an AWS account root user:

1) Use a strong password to help protect account-level access to the AWS Management Console. 2) Never share your AWS account root user password or access keys with anyone. 3) If you do have an access key for your AWS account root user, delete it. If you must keep it, rotate (change) the access key regularly. You should not encrypt the access keys and save them on Amazon S3. 4) If you don't already have an access key for your AWS account root user, don't create one unless you absolutely need to. 5) Enable AWS multi-factor authentication (MFA) on your AWS account root user account.

![[Pasted image 20250413191214.png]]


**Encrypt the access keys and save them on Amazon S3** - AWS recommends that if you don't already have an access key for your AWS account root user, don't create one unless you absolutely need to. Even an encrypted access key for the root user poses a significant security risk. Therefore, this option is incorrect.

**Create AWS account root user access keys and share those keys only with the business owner** - AWS recommends that if you don't already have an access key for your AWS account root user, don't create one unless you absolutely need to. Hence, this option is incorrect.

**Send an email to the business owner with details of the login username and password for the AWS root user. This will help the business owner to troubleshoot any login issues in future** - AWS recommends that you should never share your AWS account root user password or access keys with anyone. Sending an email with AWS account root user credentials creates a security risk as it can be misused by anyone reading the email.


