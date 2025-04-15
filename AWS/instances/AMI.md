n![[Screenshot from 2025-03-30 15-22-48.png]]
- one thing you need to rememver is - its regional based.
- Also, that it can be set to provate.
- Can get specific ami based on communitues.

#### Its lifecycle
![[Screenshot from 2025-03-30 15-25-33.png]]

- thst block device mappin is the only tricky question i can think of.
- basicaly the instance volumr as well as the ebs volumes can be mapped using clock device mapping config files while creating the image. the storsge gets saved to snapshots in S3 i guess, and since its regional , this ami, it all gets connected.
- When you lainch, you have the instance as well as the bolumes configured.

### Important tips:

![[Screenshot from 2025-03-30 15-26-57.png]]
- one region only. **Can it be migrated tho?** search up
- cant be edited. Versions? nope. update and make newer AMI.
- OH, CAN BE MIGRATED. using its snapshots.

