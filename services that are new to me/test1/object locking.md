S3 Object Lock provides two retention modes:

-Governance mode

-Compliance mode

These retention modes apply different levels of protection to your objects. You can apply either retention mode to any object version that is protected by Object Lock.

![Amazon S3 Object Lock Retention Modes](https://media.tutorialsdojo.com/Amazon-S3-Object-Lock-Retention-Modes.png)

In governance mode, users can’t overwrite or delete an object version or alter its lock settings unless they have special permissions. With governance mode, you protect objects against being deleted by most users, but you can still grant some users permission to alter the retention settings or delete the object if necessary. You can also use governance mode to test retention-period settings before creating a compliance-mode retention period.

In compliance mode, a protected object version can’t be overwritten or deleted by any user, including the root user in your AWS account. When an object is locked in compliance mode, its retention mode can’t be changed, and its retention period can’t be shortened. Compliance mode helps ensure that an object version can’t be overwritten or deleted for the duration of the retention period.

To override or remove governance-mode retention settings, a user must have the `s3:BypassGovernanceRetention` permission and must explicitly include `x-amz-bypass-governance-retention:true` as a request header with any request that requires overriding governance mode.

**Legal Hold vs. Retention Period**

With Object Lock, you can also place a legal hold on an object version. Like a retention period, a legal hold prevents an object version from being overwritten or deleted. However, a legal hold doesn’t have an associated retention period and remains in effect until removed. Legal holds can be freely placed and removed by any user who has the `s3:PutObjectLegalHold` permission.

Legal holds are independent from retention periods. As long as the bucket that contains the object has Object Lock enabled, you can place and remove legal holds regardless of whether the specified object version has a retention period set. Placing a legal hold on an object version doesn’t affect the retention mode or retention period for that object version.

For example, suppose that you place a legal hold on an object version while the object version is also protected by a retention period. If the retention period expires, the object doesn’t lose its WORM protection. Rather, the legal hold continues to protect the object until an authorized user explicitly removes it. Similarly, if you remove a legal hold while an object version has a retention period in effect, the object version remains protected until the retention period expires.

Hence, the correct answer is: **Enable S3 Object Lock in compliance mode with a retention period of one year.**



---


With S3 Object Lock, you can store objects using a write-once-read-many (WORM) model. Object Lock can help prevent objects from being deleted or overwritten for a fixed amount of time or indefinitely. You can use Object Lock to help meet regulatory requirements that require WORM storage, or to simply add another layer of protection against object changes and deletion.

![Amazon S3 Object Lock](https://media.tutorialsdojo.com/public/td-s3-object-lock-08-14-2024.png)

Before locking any objects, it is essential to enable S3 Object Lock on a bucket. Previously, Object Lock could only be enabled at the time of bucket creation, but now, Amazon S3 allows you to enable S3 Object Lock for existing buckets with just a few clicks. Once S3 Object Lock is enabled on a bucket, it allows you to lock objects within that bucket to prevent them from being deleted or overwritten for a fixed amount of time or indefinitely. While Object Lock can now be enabled on existing buckets, it is important to note that once enabled, Object Lock itself cannot be disabled. However, you can still manage and configure object lock settings, including retention periods and legal holds, but the core feature of Object Lock remains active and irreversible. Also, versioning, which is required for Object Lock, cannot be suspended or disabled once Object Lock is enabled on the bucket.

Hence, the correct answers are:

**– Configure an Amazon S3 Access Point**