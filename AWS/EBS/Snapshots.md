![[Screenshot from 2025-03-30 14-21-29.png]]
- Its incremental, that means each snapshot is created on top of the previous one in S3.

THE ARCHITECTURE:
![[Screenshot from 2025-03-30 14-21-56.png]]


Key takaeays:

![[Screenshot from 2025-03-30 14-23-18.png]]

- restoring from a snapshot is lazy as compared to a new volume creation.
- nowadays it can be increased, the speed, by forcing a read of all data immediately
- or subsequently you can use FSR option.
- can be used in 50 SNAPS PER REGION.


![[Screenshot from 2025-03-30 14-25-56 2.png]]

storage works like this. Incremental.

VOLUME xhange:

![[Screenshot from 2025-03-30 14-48-29.png]]

in the same region, you can just detach and add based on the different AZ inside onlly,
To migrate you have a migrate option,

Check once propelry.
![[Screenshot from 2025-03-30 14-54-33.png]]
you need to copy the snapshot to a different region.





