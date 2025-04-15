![[Screenshot from 2025-03-29 17-07-27.png]]

![[Screenshot from 2025-03-29 17-09-04.png]]
Client side is encryption at rest (i think this is false), with the keys and encryption done at the client side itself.
The server side encryption in transit, and it has two clauses. One where the S3 does the encrytion, thus you have to provide keys to it. and the other is where you keep the..... i forgot.
**Do chatgpt**


## Different Types of encryption
![[Screenshot from 2025-03-29 17-14-16.png]]

The server side encryption has these 3:
![[Screenshot from 2025-03-29 17-14-56.png]]
![[Screenshot from 2025-03-29 17-17-09.png]]
the key and the data gets stored in transit. master key is used to encrypt the key. and the encrypted key is used to encrypt the data.

![[Screenshot from 2025-03-29 17-19-34.png]]

![[Screenshot from 2025-03-29 17-19-41.png]]
rotation control is what, can you explain. i cant seem to remember. and role seperation as wll.
MAybe watch the encryption videos.


By default servwr side encryption uses AES256, but you can change it to use the KMS one as well. Basically by defualt we have SSE-S3, but we can make it such that SSE-KMS.

![[Screenshot from 2025-03-29 17-20-30.png]]


