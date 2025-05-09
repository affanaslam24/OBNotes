so you get the url with the same acess as the identity thats making the url.
if in between the usage of the url, the access of the identity gets compromised for that particular onject, then the url also shows access denied..

similarly, you can create urls even 8if the object doesnt exist, or even if oyu dont have aceess to view it, but in both cases the object will not be visible through the url.

Why presigned url?
![[Screenshot from 2025-03-29 18-55-05.png]]

How presigned url?
![[Screenshot from 2025-03-29 18-58-26.png]]

An example?
![[Screenshot from 2025-03-29 18-59-37.png]]
movie watching system

![[Screenshot from 2025-03-29 19-01-00.png]]
Do not generate with a role.



---



A presigned URL gives you access to the object identified in the URL. When you create a presigned URL, you must provide your security credentials and then specify a bucket name, an object key, an HTTP method (PUT for uploading objects), and an expiration date and time. The presigned URLs are valid only for the specified duration. That is, you must start the action before the expiration date and time.

This is the most secure way to provide the vendor with time-limited access to the log file in the S3 bucket.

**CORRECT:** "Generate a presigned URL and ask the vendor to download the log file before the URL expires" is the correct answer.

**INCORRECT:** "Create an IAM user for the vendor to provide access to the S3 bucket and the application. Enforce multi-factor authentication" is incorrect. This is less secure as you have to create an account to access AWS and then ensure you lock down the account appropriately.

**INCORRECT:** "Create access keys using an administrative account and share the access key ID and secret access key with the vendor" is incorrect. This is extremely insecure as the access keys will provide administrative permissions to AWS and should never be shared.

**INCORRECT:** "Enable default encryption for the bucket and public access. Provide the S3 URL of the file to the vendor" is incorrect. Encryption does not assist here as the bucket would be public and anyone could access it.