![[Screenshot from 2025-04-09 11-16-07.png]]
- in the example, there is an alternative domain name gives, which uses a custom SSL certificate.
- But we need to notice the domain name provided by the cloudfront- *.cloudfront.net
- this will always remain the same.

IN the edit option we can see the custom ssl and everything fo rthis given example:
![[Screenshot from 2025-04-09 11-16-19.png]]

![[Screenshot from 2025-04-09 11-16-45.png]]
- the security (tls version) options.
- the default root object name selection, this is for S3 statci web hosting
- logging option

AND now we will see the behaviours section:

![[Screenshot from 2025-04-09 11-17-10.png]]
- you see there is a precedence order (0 for default, meaning anything created will be more priority than default)

![[Screenshot from 2025-04-09 11-17-15.png]]
- insid ehte behaviour:
	- we can select the origin or origin group
	- viewer policy: http, https settings
	- allowed http methods
	- cache request headers and stuff
	- headers and caching and whatnot we will read later.

![[Screenshot from 2025-04-09 11-18-11.png]]

- there is also maximum and nminimum ttl
- And the important section:
	- restrict viewer acess, which makes you use signed urls for accessing things
- ![[Screenshot from 2025-04-09 11-18-18.png]]
- you can then specify specific users to access it


So, we talked about TTL, to understand it, go to [[TTL and invalidations]]