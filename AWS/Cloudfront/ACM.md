What is ACm?
![[Screenshot from 2025-04-09 11-30-25.png]]
- ACM is a trusted authority which is public for people to make use of.
- But only sipported by few AWS services like Cloudfront and ALBS, not EC2 or on prem insances.


SO, why do need ACM certification?
![[Screenshot from 2025-04-09 11-32-41.png]]
- usually in the context of edge locations, it requires https requests on both sides, and from both sides i mean, from client to edge location there is a HTTps request, and this dns name is on the certifcate for HTTPs connection to be made.
- And in the origin connection side as well, ti requires an HTTPs request, and this certificate needs to  be by a trusted authority, **not self signed**. And this certificate needs to be added in the distribution unit of the cloudfront, so that the same DNS name as on the certificate gets validated when the client asks from the client side HTTPs config.


## SSl by cloudfront

![[Screenshot from 2025-04-09 11-59-59.png]]

- by default the domain name that the cloudfront provides is configured and supported by cloudfront.net certificste.
- **But if you want an alternative domain name to be configured for your cloudfront location, then you will be asked to provide a custom SSL**
- IMPORTANT!!!!- the certificate is generated and stored or improted in ACm in US-east-1, always.
- There are 3 policies- http, https and both, look at the diagram.
- Like i said prviously, there are 2 SSL connections, and both need valid PUBLIC certs.



### old config
![[Screenshot from 2025-04-09 12-03-15.png]]
- its self explanatory.

![[Screenshot from 2025-04-09 12-08-27.png]]
- whats importent here is, if you are using old browser then you need to use a dedicated ip, which will cost you more.
- For viewer protocol side cets, it requires a public trusted cert, which should match the DNS name.
- For S3, origin (only bucket and objects, not hosting) it doesnt requires external SSL certificate, it can be done natively.
- for application load balancer you can use ACM.
- for EC2 o on prem, you cant use ACM.


## a very important distinction:
- S3 website is a custom origin
- and for this, there is no ACM configuration.
- Infact for S3 endpoint, there is no HTTPS connection.
- But we can set up a **viewer to cloudfront https connection**, and for the cloudfront to the origin side encryption, we cannot do it.
- THis is important to understand.
- because S3 static website endpoint cant be HTTPS. But we can still secure this connection using OAI.


## Here's the direct answer:

### 🔸 When you use **S3 Static Website Hosting** as the origin in CloudFront:

- That origin endpoint is something like:  
    `http://your-bucket.s3-website-us-east-1.amazonaws.com`
    
- This endpoint **only supports HTTP** — **not HTTPS**.
    

### 🔒 So, **CloudFront → S3 static website endpoint = HTTP only** (unencrypted).

- There is **no option** to enable HTTPS between CloudFront and that type of S3 origin.
    
- You **cannot use ACM** to encrypt this connection.
    
- CloudFront will warn you if you try to use HTTPS with this kind of endpoint.



## BUT: It's still secure overall (in most cases)

Even though CloudFront → S3 is HTTP:

- **Viewer → CloudFront** is fully HTTPS (secured by your ACM cert).
    
- CloudFront caches the files at edge locations — so requests rarely hit S3.
    
- The connection between AWS services (CloudFront & S3) is **within AWS’s private network**, which is trusted and secure (but technically not encrypted unless HTTPS is used).


### remeber, we use OAI for secure connection between S3 to cloudfront.
