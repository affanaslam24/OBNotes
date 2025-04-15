![[Screenshot from 2025-03-30 14-50-36.png]]
- first check the blocks in device.
- check the file type pf the ebs volume
- use mkfs to make it into file system of -t type xfs which is a type of nfs
- then mount it into a directory

To aautomatically mounting it:
![[Screenshot from 2025-03-30 14-51-55.png]]
in FSTAB file
![[Screenshot from 2025-03-30 14-52-10.png]]


Check [[Instance volumes]] for steps to configure of instance volume.
Similarly to understnad the difference between this and EFs check the config steps of [[Steps to cnonfigure]] efs.

