1. Standard class- 
![[Screenshot from 2025-03-29 17-29-27.png]]
Its replicated in 3 AZs, atleast. 
The pricing is for storage. And for the transfer of data in is free, but the data out is billed per GB. and i price would be asked over 1000 requests, for 1000 get and put request, i suppose.

No fee for retrieval fee, no minimum duration, no minimum size or storage. 

2. Standard Infrequent Access- 
![[Screenshot from 2025-03-29 17-30-47.png]]
It is same as standard, but less fee because it is infrequent access of data. the charges increases the more you acess it.
You have to store for minimum 30 days.
Even though it stores for less, the minimum billing features applies.

3. IA one zone-
![[Screenshot from 2025-03-29 17-31-39.png]]
It doesnt privides the 3 azs scheme, but still gives the same durability and availibility unless the Az it\self fails. More infrequent.
The pricing is less, but the rest charges are same.

4. Glacier Instant-
![[Screenshot from 2025-03-29 17-32-33.png]]
Long lived data, and minimum of 90 days charge. But retrieval is more expensive, longer minimum. And from what i can remember, it takes time to get the data from these S3 clases.

5. Glacier flexible-
![[Screenshot from 2025-03-29 17-34-09.png]]
Ok no, it was this one.
it cant be bmade publically accessible. Any access of data requires retireval process which takes time. Its the first one whose first byte latency is not in miliseconds. 

6. Glacier Deep Archive-
 ![[Screenshot from 2025-03-29 17-34-52.png]]
 its like an ice berg, it takes even longerthan glacier flexible.

7. the intelligent tirering-
Its not much a storage class but is something that is a combination of all the classes and works on the basis of popularity.
It costs the same as the other classes equivalents, and shoould be used when the pattern of obnject is unkown.
![[Screenshot from 2025-03-29 17-37-23.png]]
Archive instant is same as galcier instant with 90 days minimum.
Archive Access is same as glacier flexible but the days are between 90 to 270
IF object arent accessed within 180 to 730 days, its movwd to deep archive, which is the same as glacier deep archive.

Lets talk about ![[lifecycle]]

---


**Configure a DataSync task to transfer the files to S3 Standard-Infrequent Access (S3 Standard-IA). Use a lifecycle configuration to transition the files to S3 Deep Archive after 1 year with a retention period of 7 years:**

This is correct because S3 Standard-IA is cost-effective for infrequently accessed data. After 1 year, transitioning to S3 Deep Archive is the most cost-effective choice for long-term storage with infrequent access requirements.

**Use an archive tool to group the files into large objects. Use DataSync to migrate the objects. Store the objects in S3 Glacier Instant Retrieval for the first year. Use a lifecycle configuration to transition the files to S3 Glacier Deep Archive after 1 year with a retention period of 7 years:**

This is incorrect because grouping files into large objects increases operational overhead, and S3 Glacier Instant Retrieval is more expensive than S3 Standard-IA for the initial storage.

**Use an archive tool to group the files into large objects. Use DataSync to copy the objects to S3 Standard-Infrequent Access (S3 Standard-IA). Use a lifecycle configuration to transition the files to S3 Glacier Instant Retrieval after 1 year with a retention period of 7 years:**

This is incorrect because transitioning files to S3 Glacier Instant Retrieval is unnecessary and less cost-effective compared to S3 Deep Archive.

**Configure the destination storage class for the files as S3 Glacier Instant Retrieval. Use a lifecycle policy to transition the files to S3 Glacier Flexible Retrieval after 1 year with a retention period of 7 years:**

This is incorrect because S3 Glacier Instant Retrieval is not needed for the first year. S3 Standard-IA provides a more cost-effective solution for the use case.

