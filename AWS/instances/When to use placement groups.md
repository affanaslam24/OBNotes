A big-data consulting firm is working on a client engagement where the extract, transform, and load (ETL) workloads are currently handled via a Hadoop cluster deployed in the on-premises data center. The client wants to migrate their ETL workloads to AWS Cloud. The AWS Cloud solution needs to be highly available with about 50 Amazon Elastic Compute Cloud (Amazon EC2) instances per Availability Zone (AZ).

As a solutions architect, which of the following Amazon EC2 placement groups would you recommend for handling the distributed ETL workload?



**Partition placement group**

You can use placement groups to influence the placement of a group of interdependent instances to meet the needs of your workload. Depending on the type of workload, you can create a placement group using one of the following placement strategies:

Partition placement group – spreads your instances across logical partitions such that groups of instances in one partition do not share the underlying hardware with groups of instances in different partitions. This strategy is typically used by large distributed and replicated workloads, such as Hadoop, Cassandra, and Kafka. Therefore, this is the correct option for the given use-case.

![](https://assets-pt.media.datacumulus.com/aws-saa-pt/assets/pt2-q12-i2.jpg)

via - [https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html)

Incorrect options:

**Cluster placement group**

Cluster Placement Group – packs instances close together inside an Availability Zone. This strategy enables workloads to achieve the low-latency network performance necessary for tightly-coupled node-to-node communication that is typical of HPC applications. This is not suited for distributed and replicated workloads such as Hadoop.

![](https://assets-pt.media.datacumulus.com/aws-saa-pt/assets/pt2-q12-i1.jpg)

via - [https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html)

**Spread placement group**

Spread Placement Group – strictly places a small group of instances across distinct underlying hardware to reduce correlated failures. This is not suited for distributed and replicated workloads such as Hadoop.

![](https://assets-pt.media.datacumulus.com/aws-saa-pt/assets/pt2-q12-i3.jpg)

via - [https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html)

**Both Spread placement group and Partition placement group** - As mentioned earlier, the spread placement group is not suited for distributed and replicated workloads such as Hadoop. So this option is also incorrect.






- parition gives out 7 partition in each AZ, and each partition can have as many as you want instances.
- Spread can have 7 instances in one AZ only.
- Cluster is for high performance taska