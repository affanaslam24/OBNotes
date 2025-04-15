only the cname or the endpoint of the primary instance can be called for, we cannot access the standby instance directly.

![[Pasted image 20250331002555.png]]
so, the data replication is instantaneuos, both the priary and standby will have the same data quickly.

**then the primary instance fails, the standby instance is then called into use

standby proivdes availibilty usecase, not a performance one.
basically, it doesnt allows performance llike read and write operations or anything, it is not even used unless the primary inst4ance is failed. 
availibility is used, basically even if its go down, the standby starts working with low downtime.

![[Pasted image 20250331002852.png]]
its powerups

standby cant be used to optimise the read and write operatios, its just there for either good backup or for availibility.

no scaling benefits, only system updates, backup or instance type changes ca help