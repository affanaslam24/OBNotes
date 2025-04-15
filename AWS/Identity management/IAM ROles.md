![[Screenshot from 2025-03-29 04-57-30.png]]

More than one people can assume this role, at the same time iam roles dont have access and password requirements. It is attached to people. And for attachmnt purpose we need trust policy to be added to it. 

Q. who can access the role?
any anonymous user? nope. but external acess can be given, various services, and users.

Can users have roles attached to it? gotta find out this one.

![[Screenshot from 2025-03-29 05-01-06.png]]
Trust policy is also somewhere we can use principal feautre, i guess?

Permission policy is what allows or denies access to resoruces to the people trying to gain acess.

IAM role check both of these and grants a temporary security credentials to the identities that get attached to the roles.

NOTW: in EC2 as long as the role is attached to it and the instance is runnig, the instance can kkeep renewing its securirty credentials even after it expuires through the metadata.

STS:ASSUMEROLE is whats used to assume the role. this is te action in that gets configured.
BUT we need to check where this is exactly used at.

![[Screenshot from 2025-03-29 05-03-00.png]]

the role is attached to the lambda function, and given in the trust policy the lamba is allowed to gain access to this. The permission policy allows lambda to acess cloudwath or other services like s3.
It uses assumerole to have the credentials to access the services.

### To bypass the 5000 iam user limit
![[Screenshot from 2025-03-29 05-06-32.png]]


![[Screenshot from 2025-03-29 05-08-18.png]]

understand the benefits of IAM roles.
It doesnt requires you to create any newer identity inside aws. It uses the existing customer logins and lets then gain acess to the role.


PRACTISE using iam roles, please.


### can be used with different accoutn.
![[Screenshot from 2025-03-29 05-08-50.png]]

use the aws organisation project in the course for this, please. And document it as well.



