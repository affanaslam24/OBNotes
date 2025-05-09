can be confused with SSM paramater store

- it uses lambda to periodically update the secrets
- the updated secret gets integrated automatically with the services that was using it.
![[Pasted image 20250410112911.png]]

- product specifically designed for rotation and maintaining secrets, encrypt at rest.

![[Pasted image 20250410120809.png]]


- if its product integration then its parameter store, anythin else is secrets manager, and remember if its RDS.



---


**Store the patient credentials in AWS Secrets Manager. Use the GetSecretValue API to securely retrieve the credentials in the application at runtime:** This is correct because Secrets Manager is designed to securely store and retrieve credentials with minimal operational overhead. It also supports secret rotation and integrates with AWS services for secure runtime access.


This is incorrect because although Parameter Store can store credentials, it does not offer native secret rotation, which increases operational overhead.

**Store the patient credentials in an Amazon RDS database ta**


---


**Use AWS Secrets Manager to store the database credentials. Configure Secrets Manager to rotate the credentials automatically every 30 days. Update the game server application to retrieve credentials from Secrets Manager:** This is correct because AWS Secrets Manager integrates seamlessly with Aurora PostgreSQL, providing built-in credential rotation and secure storage. This minimizes operational overhead and meets the security requirements.

