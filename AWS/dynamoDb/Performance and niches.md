- youre paying more in on demand
- there is a way of getting cheaper reads
![[Pasted image 20250411134056.png]]
- per million billed.
- provisioned has RCU and WCU
- AT least 1RCU/WCU, each operation.




- one query operation can return a single item, multiple itemm, or no item
- but you always have to specify a single value for the **partition key**
- this doesnt means you are getting only single item, this just means, ONLY ONE PARTITION key value is accessible at one time.
- ![[Pasted image 20250411134752.png]]
- here, the partiton key of 1 will give you 2 items.

- its is more efficient to return multuple item in a single operation, so the above example is good.

![[Pasted image 20250411134944.png]]
notice the RCU consumption. no matter what you get in return, as long as its within 1rcu value, its 1 RCU.


- the operation of one primsry key can give you multiple items, as weve seen above.
- BUt you can also get a specific item using the sort key value, or you can use a range of sort key values as well based on your demand.
- even if we just wanted the yellow or pink attribute of the items, we will still be charged for thhe whole item fetch.

---

NOW scan is different from quesry.
Query means to query on one particular partition key, so you cant do a query to find "the best weather in all the weather stations.", for that we need scan.

- even if you use filters, its very inefficient in terms of costing because youre SCANNING all the ITEMS in that table, meaning you will be asked to pay for the scanning of going thorugh each data.

so it is like this:
![[Pasted image 20250411135812.png]]
- we wanted the sunny attribute (yellow) from all the weather stations, then we will use scan to scan all the items, all the partition keys, and that consumes all the items in the table.
And whenwe are returned the values, the items not havving the sunny attribute will be discarded, but we will still be billed.


--- 

### consistency model:

- eventually or strongly
- with dynamodb, each storage is replicated in multiple Azs, and each of these are called storage nodes.
- one is a leader.
- its chosen with election.
- leader node has the first write, and any corresponding changes to the item is reflected in it first
- and then replication ahppens
- THis, basically:
- ![[Pasted image 20250411165228.png]]
- but only on one AZ the replication happened.

- usually the replication happens inn al the storage nodes in miliseconds, but when youre doing eventual consistence read, there is a possiblity that you mihgt not get an accurate read.
- Strong consistent takes storage from the leader.
- Also, not all application supports eventual consistence reads.
![[Pasted image 20250411165554.png]]



---

![[Pasted image 20250411165752.png]]
- basically for 2.5k how many units of writes? 2.5/1=2.5, round up to 3.
- total 3 write units per seconds based on the size of the item.
- total items? 10.
- therefore multiply it with 3.
- 30, because each item will comsume 3 Units of write.

RCU
![[Pasted image 20250411170027.png]]


with eventual consistence:
![[Pasted image 20250411170040.png]]
