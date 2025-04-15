- DynamoDb has DAX whihc is integrated to it by default, so unless you have a specific usecase of memcached or redis, you need not use it.

What do memcached and redis has as use case?


Amazon ElastiCache for Memcached is a Memcached-compatible in-memory key-value store service that can be used as a cache or a data store. Amazon ElastiCache for Memcached is a great choice for implementing an in-memory cache to **decrease access latency, increase throughput, and ease the load off your relational or NoSQL database**.


Amazon ElastiCache for Redis is a blazing fast in-memory data store that provides sub-millisecond latency to power internet-scale real-time applications. Amazon ElastiCache for Redis is a great choice for **real-time transactional and analytical processing use cases such as caching, chat/messaging, gaming leaderboards, geospatial, machine learning, media streaming, queues, real-time analytics, and session store.**

![[Pasted image 20250413185025.png]]



Also remember that redis is transactional, and memcached is multithreaded.

For more details on that, go to [[Elasticache]]