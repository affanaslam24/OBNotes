**When you apply a retention period to an object version explicitly, you specify a `Retain Until Date` for the object version**

You can place a retention period on an object version either explicitly or through a bucket default setting. When you apply a retention period to an object version explicitly, you specify a `Retain Until Date` for the object version. Amazon S3 stores the Retain Until Date setting in the object version's metadata and protects the object version until the retention period expires.

**Different versions of a single object can have different retention modes and periods**

Like all other Object Lock settings, retention periods apply to individual object versions. Different versions of a single object can have different retention modes and periods.

For example, suppose that you have an object that is 15 days into a 30-day retention period, and you PUT an object into Amazon S3 with the same name and a 60-day retention period. In this case, your PUT succeeds, and Amazon S3 creates a new version of the object with a 60-day retention period. The older version maintains its original retention period and becomes deletable in 15 days.

Incorrect options:

**You cannot place a retention period on an object version through a bucket default setting** - You can place a retention period on an object version either explicitly or through a bucket default setting.

**When you use bucket default settings, you specify a `Retain Until Date` for the object version** - When you use bucket default settings, you don't specify a Retain Until Date. Instead, you specify a duration, in either days or years, for which every object version placed in the bucket should be protected.

**The bucket default settings will override any explicit retention mode or period you request on an object version** - If your request to place an object version in a bucket contains an explicit retention mode and period, those settings override any bucket default settings for that object version.


find out more about this feature