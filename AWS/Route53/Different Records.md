
![[Screenshot from 2025-03-29 03-40-01.png]]
A records points a name to the IP. basically host to ip. but many a times we use Alias to point A record to specific AWS s3 endpoint or ELB which dont give back a static ip but gives out dns names, but these dns records are basically static ip only.

![[Screenshot from 2025-03-29 03-40-27.png]]

Cname- 
this is used for host to host.
basically betabookmyshow.com is pointing to an ip adress, and then we use cname to point www.betabookyshow.com to the betabookmyshow.com.
IMP- canno be used for root domains, like, we cannot use betabookmyshow and point it to an S3 service dns endpoint usng this.
root domains are what domain name we bought.

![[Screenshot from 2025-03-29 03-43-48.png]]

We also need to understand the whole connundrum over authoratative, delegate, etc. **chech the quick notes.**
also talk about delegation, authorotative. and ofc, what are these different components.


Time to live is the total time this request can go around finding the requesr, and if it is not resolved yet, it will die. (do chatgpt on this one)

