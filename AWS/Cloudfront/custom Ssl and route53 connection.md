![[Screenshot from 2025-04-09 13-02-17.png]]
So, first here we are not using the Custom SSL. Here the cloudfront will provide a defult cert.
Then select the viewer policy etc.
- you can also user restrictvie user access with presigned urls and trusted signers:
![[Screenshot from 2025-04-09 13-05-02.png]]


![[Screenshot from 2025-04-09 13-05-19.png]]
- logging and cache policy setting. (we use cache policy instead of TTLs now)

The main section:
![[Screenshot from 2025-04-09 13-10-08.png]]

- the class selection.
- the alternative domain name, and the subsequent SSL selection secigon.
- The default root object needs to be written incase of Static hosting.


# Custom SSL creation and integration with Route53

- there are 3 things to consider: 
	- SSl creation based on the domain name you want in ACM, route a CNAME for this cert in the hosted file of this domain name
	- in cloudfront, add the custom SSL and the alternative domain with your personalised domain.
	- connect the alternative domain and the cloudfront default domain in hosted file of route 53.

Question:
why is a record from ACm needs to be added to hosted files
## ❓ Why does ACM ask you to add a record to your hosted zone?

Because it needs to **prove you own the domain** you're requesting a certificate for.

This is called **DNS Validation**, and it’s part of the standard security protocol for issuing SSL certificates.



what if i am usign external hosting and not route53?
![[Pasted image 20250409171842.png]]

- make sure you are using the name and the value pproerplry!!
- notice that the name should include the personala domain name at the end.
- this name and value will be provided by ACM. 





### Actual implementation:


![[Screenshot from 2025-04-09 13-28-40.png]]
- domain name was gives as merlin.animals4life.org
- the cname name
- the cname value.
- by clicking the route in route53, it crreates a route record automatically.
- And this route record is used for the validation of the certifcate, and after a while you will see the "Issued" tag, after a succesful propagation in route53.

![[Screenshot from 2025-04-09 13-28-11.png]]
record in route53.


Adding the cert in cloudfront:
![[Screenshot from 2025-04-09 13-29-47.png]]


Last step: adding record for connection of the domain namme to the cloudfront domain name-
![[Screenshot from 2025-04-09 13-31-30.png]]


And finally, its shown in the certificate what certificate has the dns or whatever
![[Screenshot from 2025-04-09 13-32-42.png]]


