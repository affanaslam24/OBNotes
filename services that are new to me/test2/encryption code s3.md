If you need server-side encryption for all of the objects that are stored in a bucket, use a bucket policy. For example, the following bucket policy denies permissions to upload an object unless the request includes the **x-amz-server-side-encryption** header to request server-side encryption:

However, if you choose to use server-side encryption with customer-provided encryption keys (SSE-C), you must provide encryption key information using the following request headers:

`x-amz-server-side-encryption-customer-algorithm`

`x-amz-server-side-encryption-customer-key`

`x-amz-server-side-encryption-customer-key-MD5`

Hence, using the **x-amz-server-side-encryption** header is correct as this is the one being used for Amazon S3-Managed Encryption Keys (SSE-S3).

All other options are incorrect since they are used for SSE-C.

