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


---

IMPORTANT!!
CLient side encryption


The requirement is that the objects must be encrypted before they are uploaded. The only option presented that meets this requirement is to use client-side encryption. You then have two options for the keys you use to perform the encryption:

• Use a customer master key (CMK) stored in AWS Key Management Service (AWS KMS).

• Use a master key that you store within your application.

In this case the correct answer is to use an AWS KMS key. Note that you cannot use client-side encryption with keys managed by Amazon S3.

![](https://img-c.udemycdn.com/redactor/raw/test_question_description/2021-02-25_12-00-48-9dad6f62c8e7c9414b51a788e346c78c.jpg)

**CORRECT:** "Use client-side encryption with a master key stored in AWS KMS" is the correct answer.

**INCORRECT:** "Use client-side encryption with Amazon S3 managed encryption keys" is incorrect. You cannot use S3 managed keys with client-side encryption.

**INCORRECT:** "Use server-side encryption with customer-provided encryption keys" is incorrect. With this option the encryption takes place after uploading to S3.

**INCORRECT:** "Use server-side encryption with keys stored in KMS" is incorrect. With this option the encryption takes place after uploading to S3.




