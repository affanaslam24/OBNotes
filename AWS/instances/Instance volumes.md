![[Screenshot from 2025-03-30 14-14-42.png]]
They are generally bettee than EBS in terms of throuput and IPS

![[Screenshot from 2025-03-30 14-15-15.png]]

can it be detached? nopes.
Can we get the data out of it? probably, there could be ways.

When we first configure an instance you will see an ebs volume of it created by default, thats not the instance volyme. Instance volume is different.

![[Screenshot from 2025-03-30 14-17-50.png]]![[AWS/instances/photos/Screenshot from 2025-03-30 14-19-51.png]]

Solid state drive (SSD) backed volumes optimized for transactional workloads involving frequent read/write operations with small I/O size, where the dominant performance attribute is IOPS.

Hard disk drive (HDD) backed volumes optimized for large streaming workloads where throughput (measured in MiB/s) is a better performance measure than IOPS.


Also, ST1 and SC1 cannot be used for booting.


# Steps to configure
![[Screenshot from 2025-03-30 14-57-06.png]]
- it isnt configured directly just because its connected to the instance
- check the blocks
- make it into a file system type block, use mkfs
- then make a directory to mount it into
- can go to the etc/fstab to configure it as well.

Check [[Steos to configure]] for EBS and [[Steps to cnonfigure]] for EFS.