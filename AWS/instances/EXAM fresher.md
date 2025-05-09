A research group runs its flagship application on a fleet of Amazon EC2 instances for a specialized task that must deliver high random I/O performance. Each instance in the fleet would have access to a dataset that is replicated across the instances by the application itself. Because of the resilient application architecture, the specialized task would continue to be processed even if any instance goes down, as the underlying application would ensure the replacement instance has access to the required dataset.

Which of the following options is the MOST cost-optimal and resource-efficient solution to build this fleet of Amazon EC2 instances?
- check the keywords properly-
it needs high IOps.
with low cost
there id an application that will do the necessary copy of dataset before the instance closes.
All of this points to a situation to use Instance store.


---

An Amazon Machine Image (AMI) provides the information required to launch an instance. You must specify an AMI when you launch an instance. When the new AMI is copied from Region A into Region B, it automatically creates a snapshot in Region B because AMIs are based on the underlying snapshots. Further, an instance is created from this AMI in Region B. Hence, we have 1 Amazon EC2 instance, 1 AMI and 1 snapshot in Region B.


---

ST1 and SC1 cannot be used for booting.


---


The key thing to understand in this question is that HPC workloads need to achieve low-latency network performance necessary for tightly-coupled node-to-node communication that is typical of HPC applications. Cluster placement groups pack instances close together inside an Availability Zone. These are recommended for applications that benefit from low network latency, high network throughput, or both. Therefore this option is the correct answer.

- so the cluster group gives maximuum HPC in one AZ.
- partition plkacement does has one partition with a huge number of instances placed in one AZ, but the partitions cant communicate with each ohter. At the sam time, it can be uploaded in various other Azs as well.
- spread is when you need maximum isolatin between instances. One Az has 7 instaces.

A partition placement group spreads your instances across logical partitions such that groups of instances in one partition do not share the underlying hardware with groups of instances in different partitions. This strategy is typically used by large distributed and replicated workloads, such as Hadoop, Cassandra, and Kafka. A partition placement group can have a maximum of seven partitions per Availability Zone. Since a partition placement group can have partitions in multiple Availability Zones in the same region, therefore instances will not have low-latency network performance. Hence the partition placement group is not the right fit for HPC applications.

---


- cross AZ in Ec2, there are charges involced.
- inside same zone, its free

---


**Set the `DeleteOnTermination` attribute to false**

An Amazon EC2 instance can be launched from either an instance store-backed AMI or an Amazon EBS-backed AMI. Instances that use Amazon EBS for the root device automatically have an Amazon EBS volume attached. By default, the root volume for an AMI backed by Amazon EBS is deleted when the instance terminates. The default behavior can be changed to ensure that the volume persists after the instance terminates. To change the default behavior, set the DeleteOnTermination attribute to false using a block device mapping.


---

Always allow roles for accessing differetn services rsather than using credentials or access keys and everyting of  a specific user inside an instance, that unsafe.

---

**User Data scripts in EC2 run as the `root` user by default**.


