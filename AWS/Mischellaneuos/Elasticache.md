- you cant just use the service you will be required to make changes to the application and allow it to make use of the caching features. It needs to have the corresponding code to work with cache.
![[Pasted image 20250411192408.png]]


- if the question says, no code or application chsnge, then Elasticache is not the service you wanna use.



![[Pasted image 20250411192530.png]]



![[Pasted image 20250411192543.png]]



![[Pasted image 20250411192601.png]]


- best use case: storing the session data!
- if bob connects to an isntance, that instance writes the session data too elasticache immediately, so evn if the session was distrupted or instance failed:
- ![[Pasted image 20250411192743.png]]
the elasticache will have the session data, the things that i was doing, safe inside of it.

![[Pasted image 20250411192820.png]]


thats it for high level view.

---
 we need to understnad the different caching engines now.


- memcached can support strings or basic structures.
- redis can support advance, like list, sets, datasets, hash, sortedsets etc, bitarrays etc

![[Pasted image 20250411193113.png]]

- in redis, more consistency requirement, if the transaction works or not. think of the ATOM of the database that we studied.



REMINDER:
ELASTICACHE is not used in S3.


