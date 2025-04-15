![[Screenshot from 2025-04-08 22-19-34.png]]
- so first we need to understand the 2 terminologies:
	- user pools- allows sign in/ups
	- identity pools- allows access to aws reosurces.
- what do we use just user resources for? it them authentication and a JWT token, which can be used by API gateways, which can use it on other resources of AWS. At the same time, authentication in itself is a crucial process in any social application. it also provides MFA, security features, etc.
- IMPORTANT!- Federated identities are those that are google, facebook, etc, and at the same time user pool can be configured as federated identity, we'll see later.

#### user pools:
![[Screenshot from 2025-04-08 22-35-17.png]]
- gets JWT tokens.

#### identity pools
![[Screenshot from 2025-04-08 22-53-07.png]]
- lets say you configured an identity pool for google related identities, in this way it will create a google token when signing and this google token will be given **role permissions**  to the services.
- important- each identity pool creates an authenticated and an unauthenticated role automatically, **which can be further editted**.
- the roles give them temporary credentials, which can be renewed by the pools.
- LIMITATIONS:
	- for each idp, you will have to configure different token config.
	- **instead pf that you can use uder pool for authentication or sign up using federation optioin, this way the different different idps, google facebook etc, will get converted to a single user pool identity. This user pool can be configured to gain access through a single token config inside the identity pool that you will create!**

##### Like this!!!!
![[Screenshot from 2025-04-08 22-55-19.png]]


--- 
Now, to see various workflows and understanding this cognito business:

