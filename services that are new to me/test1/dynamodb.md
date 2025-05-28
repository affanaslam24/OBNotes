![[Pasted image 20250515181838.png]]

This doesn’t mean that you must access all partition key values to achieve an efficient throughput level, or even that the percentage of accessed partition key values must be high. It does mean that the more distinct partition key values that your workload accesses, the more those requests will be spread across the partitioned space. In general, you will use your provisioned throughput more efficiently as the ratio of partition key values accessed to the total number of partition key values increases.


**Reducing the number of partition keys in the DynamoDB table** is incorrect. Instead of doing this, you should actually add more to improve its performance to distribute the I/O requests evenly and not simply avoid “hot” partitions.


**Avoid using a composite primary key, which is composed of a partition key and a sort key** is incorrect because as mentioned, a composite primary key will provide more partition for the table and in turn, improves the performance. Hence, it should be used and not avoided

