
![[Pasted image 20250402155716.png]]

So i am a lot confused about this right now, but i think and i am sure this is the case, thhat rds uses one vpc and inside it chooses a subnet group for its instances to be launched and everything. and its only AZ bases, tha means in the same region of that vpc, only those AZ are used for replicstion purposes.
But i ama little confused about the aruora, and how it works. i think iit also works in the same vpc and the AZ rule applies to it, with 15 replications allowed and 6 storage facilities, sure, but eventually i think it isnt alllowed to replicate outside of the region.

But there is a feature named aurora global database, which allows READ replicas outside of the rtegion, with one second delay over the data replication.

primary to secondary region(s)


![[Pasted image 20250402160714.png]]


