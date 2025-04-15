![[Screenshot from 2025-03-30 14-01-07.png]]
EBS is like harddisk allocated to instances.

- Can only be in one AZ.
- Can only be attached to one instance at a time.
- is persistent.
- Csn migrate to other AZs and cross region as well.
- Billed based on storage per month. IMPIRTANT
**because snapshots are billed based on the storage that they consume, in rds.** Check this out once.
Ok it was this::
![[Screenshot from 2025-03-30 14-25-56.png]]

So the snapshots made are billed on gigabyte per month. Also, the data doesnt gets coiped again and again.
And on the mistake with rds, rds USES ebs for storage, and it uses the same billing at this.


### Overview of the Architecture:
![[Screenshot from 2025-03-30 14-02-14.png]]

