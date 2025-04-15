![[Pasted image 20250331020427.png]]
how is aurora nnettwe?
it provides both the readreplica and multiaz benefits with that cluster option,

![[Pasted image 20250331020850.png]]


there are 6 storage node across all azs. (research more on this one pleasse)//.
in the example, only 3 azs are used, but its not necesaarirly the case.
we can have upto 15 replicas to choose from as opposed to the one standby option that thre regular rds provides.

the data is the one that gets synchronous persistend, that means the storage only. the instances have no use in this case, unlike how the regular rds uses the instance to first syncronise and then write it to the storgae, aurora doesnt needs the instances.

its the storage that gets syncronised.
and before the need to use restore point in time or snapshots, aurora keeps a check if the storage is in consistent state or not.
if one storage fails, it back it up or fixes it immediately. (idk how it does that)

also, only the primary instance can write to the storage, other storage only have read propoperties.



![[Pasted image 20250331021557.png]]

its highest cpacity is 125 tb, but you paty for what oyu use.

![[Pasted image 20250331021700.png]]


![[Pasted image 20250331021752.png]]


![[Pasted image 20250331021914.png]]

backtrack is when you need to go to a specific time frame or when you want to go to before a corruption happened.

i dnt know what this fast clone feature is.



# how to use snapshots to make aurora?

we use migrate snapshot option istead of restore snapshot for aurora


![[Pasted image 20250331022542.png]]

For the steps on how to initialise the databse using aurora, its pretty much the same, check out [[steps to configure]]. 
make note that it is not free tier invlived.
**Also, even though aurora uses cluster mode, it still requires a subnet group to know where to deploy the rds instance.**
you can also chooose to have replica options or disable it, making it a single instance rds with both read and write capabilities, but with the benefit of felixble storage option.


check out later on how does kms work in aurora?



