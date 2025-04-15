
#### What are hosted zoned?
![[Screenshot from 2025-03-30 20-11-29.png]]
- stores the dns records, so its like a database
- globally resilient

## Public hosted zone
![[Screenshot from 2025-03-30 20-12-04.png]]
- externally registered domains can  point at public zones.
- its publically accessivle

![[Screenshot from 2025-03-30 20-14-44.png]]
- dns resolver uses the vpc+2 adress for resolving
- the records are publically accesible.
## private zone
![[Screenshot from 2025-03-30 20-15-30 1.png]]

- connected to specifc vpcs.
- can be used as overlapping accesibility

![[Screenshot from 2025-03-30 20-15-55.png]]


But overlapping is allowed like this:

![[Screenshot from 2025-03-30 20-16-29.png]]
- from inside the vpc attached, all resources are accebile
- outsife the internet, no private resources are acceible.

