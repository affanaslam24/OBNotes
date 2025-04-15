bullshit thing.
Its basically caching
instead of the application making api calls to, first thhe cache and then incase of cache miss going to the Database, here there is only one api call. to the DAX. if there is a cache miss, the dax does the work of fetching the data.

its meant for using with dynamoBD, so its easier for ijmplementation.


![[Pasted image 20250411183023.png]]


I didnt study in depth:


![[Pasted image 20250411183142.png]]



- you can use write operatins using dax
- any application using dax needs to be deployed in the same vpc it is deployed to
![[Pasted image 20250411183258.png]]


 - it doesnt provdes strong consistecy!
 - if its write heavy application, dont use dax
 - for everything else, significnt boost in caching etc, choose dax.
