![[Screenshot from 2025-04-09 13-35-58.png]]
- any user can connect with the origin in this way, and we want to deny this access.


### OAI
![[Screenshot from 2025-04-09 14-00-09.png]]

![[Screenshot from 2025-04-09 14-01-34.png]]
- so what exactly happens is: we create an OAI and then attach that identity to the distribution.
- In the policicy of the bucket of the firewall of the custom origin, we tell that no onne but the identity can access this service or resource. In thiis mannerism, we block any external request apart from cloudfront.


Q. can one OAI be connected to multiple cloudfront distribution? yes.


## important! there are 2 ways of securing the connection from Cloudfront to the origin;
And this we talked previously as well, when we said that S3 website static hosting cant have HTTPs so how to secure it? well, using the OAI.

The 2 ways are:
- use encryption or header of the certificate or something.
-![[Screenshot from 2025-04-09 14-03-06.png]]
- use OAi for including this Identity in firewalls of the orgins.
-![[Screenshot from 2025-04-09 14-03-32.png]]


![[Screenshot from 2025-04-09 14-03-36.png]]






---- 
### How to update OAI in existing distribution?


![[Screenshot from 2025-04-09 14-18-57.png]]
![[Screenshot from 2025-04-09 14-19-12.png]]
creare a new oai if not created yet
![[Screenshot from 2025-04-09 14-19-22.png]]
add it to the policy
![[Screenshot from 2025-04-09 14-19-33.png]]


Now the bucket policy will have a new config, but you have to edit the old policy: 
![[Screenshot from 2025-04-09 14-19-49.png]]
because deny allow deny. And right now both are allowed.
![[Screenshot from 2025-04-09 14-20-01.png]]
![[Screenshot from 2025-04-09 14-20-09.png]]

Done.


Now, no one but the cloudfront can access the origin bucket.



