- as it turns out DAX is not bullshit.
- An **in-memory database** is a database that **stores all its data in the computer's main memory (RAM)** instead of on disk (like SSDs or hard drives).
- Dynamo Db itself is not an in memory caching, meaning, it stores it data in disk format, not fast for caching.
- But using DAX you can have fast caching, low latency, and since oyure using Dynamo Db along wiht it, it provides high availibility and fault tolerance.


- elasticache is also something similar, with redis as its database prvider for transactional kind, it can be used for high end caching and low latency kinda shit. And its real time, because its transactional.


**NEPTUNE**
- **Amazon Neptune is a fast, reliable, fully-managed graph database service that makes it easy to build and run applications that work with highly connected datasets. Neptune is not an in-memory database, so this option is not correct.**

---

**Amazon DynamoDB Accelerator (DAX)**

	Amazon DynamoDB Accelerator (DAX) is a fully managed, highly available, in-memory cache for DynamoDB that delivers up to a 10x performance improvement – from milliseconds to microseconds – even at millions of requests per second. DAX does all the heavy lifting required to add in-memory acceleration to your DynamoDB tables, without requiring developers to manage cache invalidation, data population, or cluster management. Therefore, this is a correct option.

![[Pasted image 20250413165707.png]]

And its used inside a vpc.

Also, it seems DAX and elasticache are used in the same questions most of the time.


**Amazon ElastiCache**

Amazon ElastiCache for Memcached is an ideal front-end for data stores like **Amazon RDS or Amazon DynamoDB**, providing a high-performance middle tier for applications with extremely high request rates and/or low latency requirements.

----




When to use elasticache and when to use dynamoDB?
![[elsaticache and DB]]