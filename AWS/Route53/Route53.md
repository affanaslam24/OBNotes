## Basics
![[AWS/Route53/photos/Screenshot from 2025-03-29 03-17-34.png]]
you need to be able to explain what these various terms are, alright.

Nameservers are where the zonefiles are present. What are zonefiles? a physical database which contains records. And zone is a part of the dns database which uses records to resolve the requests made by dns client.
**this is a bad explanation, find better.**


### DNS Root
![[AWS/Route53/photos/Screenshot from 2025-03-29 03-21-27.png]]

this is the root traversal of domain.

I dont understand much of this, but root hints is a config that points to the root servers and ips, and from there we find the root zone of our TLD, from there we go to the specific zone of our root domain name, and then that points to our nameservers. Something like that, so we need to understand this btter.
![[Screenshot from 2025-03-29 03-23-49 (copy).png]]

root zone of all the TLD, then to the .com zone to find the domain name we have, and then nameservers that have our hosted zonefiles. this is accurate.
![[AWS/Route53/photos/Screenshot from 2025-03-29 03-26-12.png]]


## what are hosted zones?

![[Screenshot from 2025-03-29 03-36-30.png]]
zone files are what stored our records (A, AAAA, cname etc) in itself, and then these zonefiles are hosted on nameservers that gets pointed to by the root zone of the TLD we bought.

think of nameservers as our database that carries our data.


something like thia:
![[Screenshot from 2025-03-29 03-39-24.png]]

