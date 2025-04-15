![[Pasted image 20250409193359.png]]
this is what we will implement.

- he used a one click deploy link to create a S3 bucket, an infrastructure of the above as werll as a private instance.
- Now to connect with the private instance we need to use **sessions manager**. becasue remember, it isnt with an IGW, so you cant use SSH for connection.
![[Pasted image 20250409193800.png]]
no public ipv4.

![[Pasted image 20250409193817.png]]
no connectivity with aws services as well


---
how to create endpoint?
![[Screenshot from 2025-04-09 19-38-55.png]]
Select the service
![[Screenshot from 2025-04-09 19-39-08.png]]
![[Screenshot from 2025-04-09 19-39-11.png]]

Now to add yhe prefix list to the route table, you need to select the route table properly, mailny to select the subnets that you want to access the S3 service.
![[Screenshot from 2025-04-09 19-39-43.png]]
here, its app A, B , C that we want to have acess.


![[Screenshot from 2025-04-09 19-39-48.png]]
Also make sure that they are main route table.


![[Screenshot from 2025-04-09 19-40-00.png]]
You can have specific policy as well, but for now we will allow all access.


The route tables after adding the prefix:
![[Screenshot from 2025-04-09 19-40-16.png]]
![[Screenshot from 2025-04-09 19-40-23.png]]
The prefix list
![[Screenshot from 2025-04-09 19-40-40.png]]
![[Screenshot from 2025-04-09 19-40-43.png]]

Inside the instance again:
![[Screenshot from 2025-04-09 19-41-02.png]]

![[Screenshot from 2025-04-09 19-41-13.png]]

![[Screenshot from 2025-04-09 19-41-46 1.png]]

see, we can now access!!!

