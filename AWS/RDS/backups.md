
![[Pasted image 20250331005945.png]]
rto and rpo.


![[Pasted image 20250331010026.png]]
the s3 bucket which has the snapshot will not be usualkly seen in the console, and the snapshots are made by aws.

now, for snapshots, the standby instance is used. But if its single az rds, the single instance is used for backup.

automatic snapshots are deleted when the rds is removed, and if you configure so. but manual snapshots doesnt gets deleted unless we go and delete specifically.

![[Pasted image 20250331010311.png]]

if we are making manual snapshots, then the rpo depends upon us.
more frequent backup means lesser rpo.

before deleting the rds instance, itll ask you for a final snapshot, and this snapshot will contain everything about the database instance.

AT the same time, it provides a transaction log insid ethe same s3 every 5 mmin, so it minimises the rpo by giving us chance to go 5 minutes back.

### Retention period
its between 0 to 35 days, 0 meaning it doesnt backs up the data. and 35 means it can retain the snapshot or data between any day of  that 35 day. but it will still expire after 35 days. the only way to retain backup forever is to manually store it or when deleting the rds it asks for a final snapshot.

Next, we will talk about ![[RTO and restores]]