can be confused with SSM paramater store

- it uses lambda to periodically update the secrets
- the updated secret gets integrated automatically with the services that was using it.
![[Pasted image 20250410112911.png]]

- product specifically designed for rotation and maintaining secrets, encrypt at rest.

![[Pasted image 20250410120809.png]]


- if its product integration then its parameter store, anythin else is secrets manager, and remember if its RDS.
