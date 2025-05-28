In **Amazon RDS**, failover is automatically handled so that you can resume database operations as quickly as possible without administrative intervention in the event that your primary database instance goes down. When failing over, Amazon RDS simply flips the canonical name record (CNAME) for your DB instance to point at the standby, which is in turn promoted to become the new primary.

![Amazon RDS](https://media.tutorialsdojo.com/rds_ha_5.png)

Hence, the correct answer is: **The canonical name record (CNAME) is switched from the primary to standby instance.**

The option that says: **The IP address of the primary DB instance is switched to the standby DB instance** is incorrect because IP addresses are per subnet, and subnets simply cannot span multiple AZs.

---


Amazon RDS automatically performs a failover in the event of any of the following:

1. Loss of availability in primary Availability Zone.
2. Loss of network connectivity to primary.
3. Compute unit failure on primary.
4. Storage failure on primary.