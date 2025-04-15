![[Pasted image 20250411173227.png]]


- cannot add LSi after creation of table
- alt sort key but same partition key
- if your table is using provisioned capacity then same RCU and WCU values
![[Pasted image 20250411173400.png]]

- lsi gives us alternative Sort key to allow us to view the data in the base table in a different way.
- That are used with the base table.
![[Pasted image 20250411175124.png]]
- the oartition keys are the same, its the SK that are changed.



GSI
![[Pasted image 20250411175320.png]]


- can change the pk, adn then have a range or a specific SK for selection purpose.
![[Pasted image 20250411175558.png]]

- they are also sparse:
![[Pasted image 20250411175641.png]]
- eventual consistency and can be created anytime 

![[Pasted image 20250411175810.png]]

- we use indexes to see the data in different perspective