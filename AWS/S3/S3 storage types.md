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