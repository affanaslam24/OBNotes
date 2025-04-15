![[Pasted image 20250402173827.png]]

IT provides abstaction to the user, like the proxy fleet. it doesnt lets the user know about the scalability and everthing

ELBs can use not only compute services, but other services as well with ELBS

you cna chppse ipv4 or dual stack.

Should always be configured for the minimum if 2 or more azs with one subnet each,atleast.


Now, onto some curious things:
- its dns has an A record that transfers any incoming traffic to the nodes. Now what is an a record? its a record which is used to point to a static ip, or basically an adress link which is root. so an A record to the nnodes.
- next up, each subnet that is configured will have a node attached to it. and if the load balancer sees a higher load, it creates a new node in subnets. this node system is nice because without users interaction it can scale up and down based on the configuration involved.


# Internet facing and internal facing.
Internet facing - it can use both public and private instances. In internet facing, the nodes will have public and private ip addresses allocated to it, so that applications outside can acess them and the instances they are attached to. And in this way it can be attached to either private or public instances, but if the instances themselves dont allow it to get connected, then thats a different case.
we need to research if private instances connected to it can still be accessed by people outside? and what about if thw security groups dont allow instances to acees them?


Internal facing- only have private ips for their nodes, which is used for multi tier look. basically where you want only web to be accessed by the users and the application tier is hidden, and only web tier can access application tier.






![[Pasted image 20250402180432.png]]
both /27 and /28 are right answers, but /28 will only give 11 free ip adresses,  and thats too much of a close call for scaling up. thats why /27 is more accurate answer.



![[Pasted image 20250402211138.png]]

So, the keyword here is coupling and independant scaling.
Without the ELB the services are tightly coupled, meaning each web instance is connected to a specific app instance, but with ELB they are lloosly coupled, thatmeans, the WEB TIER is now connected to APP TIER, and all the instances can independently grow without the other tier being disrupted.


## Cross Zone LB
![[Pasted image 20250402211632.png]]
SO this is a feature that was not originally there in standard functions of ELB, but now its in the standard function of ELD, and you can guess with the picture to what imean. 
Uneven distribution of load can be managed through ELB.


Q. can one subnet have more than one node?
yes. by default it gives one node, but if the traffic is high, it can have more than one node, and since each node can now transfer load to another azs and subnets instances using crozz zone lb, we can rest assured that load are balanced approprieately.


### Key takeaways
![[Pasted image 20250402212201.png]]
the first one is the crucial one where it says it required 2 azs with one subnet each, having one node which can scale up on high load.

