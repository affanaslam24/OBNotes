![[Pasted image 20250331011630.png]]
we will talk about restore and replications.

so replication inside the rds can also replicate the corrupted data, and thats where restoring data from snapshot can be used.

But we need to figure out how low rto can be achieved, because restores can take time.

Also, the transaction logs can very well be used to achieve better rpo, but it will not be of much use for rto, because back ups are restored to the ladt backup and transaction log replays the db to bring to a desired point, if possible.
(i dont understand this much)


## Asyncronous and synchroinous replicatin

read replica uses asynchronous, thats why its read only.And multiaz arch where the standby instance is continuosly filled, can be used using ynchoronous.

## Multi az and read replica
multi az happens in the same region only. Meanwhile read replica can happpen in cross region manner using asynchronous replicstipn



![[Pasted image 20250331013002.png]]


![[Pasted image 20250331013147.png]]

**so we can use multiaz as well as readreplica to provide availibility as well as performance increment as well**
you can make it such that the primary instance has only write property and the readreplica instanes can have read property.



### **How does it effects availibility?**
![[Pasted image 20250331013540.png]]
A snapshot and backup doesnt improves RTO, it just imprives RPO, basically how quickly a database is restored is not handled by snapshot or backups.

ReadReplica can improve this, not only will it provide good RPO, availibility, but it can also provide low RTO. 

Usually ReadReplica only has read property, but in case of a primay instance going down, we can promote readreplica to have both read and write properties.
Watch the others in the diagram.


