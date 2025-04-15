![[Pasted image 20250408214647.png]]
- near real time
- can transform the data using lambda on hte fly, but takes time
- billed based on the volume pf data being passed thorugh it.
- remember, used for data analytics, data storing, and data lakes.



### Details
![[Pasted image 20250408220108.png]]

- first, always remeber its used to store Persistent data stream, which the usual kinesis stream cant do.
- NOw, rememebe rthe consumers- http, splunk, redshift, elaticsearch, S3 buckets.
- its producers? it can be the kinesis stream itself, or the production group directly.
- In either case we have a near real time buffer of data passing through it.
- kinesis stream has real time passing, but even still the kinesis firehose tkes it time.
- buffer time is 60 seconds, or 1 MB of data stored and readyv to send.
- it can be processed and channged into different data before sending as well, using lambda, **BUT its not real time**.
- **If you want real time data modification, you can use Kinesis stream to chang the data and then use other services.**
- Before sending the data to lambda from Firehose, one can send the **original data** to S3 buckets as well as backuop data.

- All the data are direct end to end transmission from the kinesis firehose to the consumer, but in redshift there is an intermediatery s3 bucket which copies the data. Even still, the data is then taken from S3 to the redshit thorough firehose (i guess, not sure). Sure, that there is an intermediatery tho.



Firehose cannot directly write into a DynamoDB table, so this option is incorrect.