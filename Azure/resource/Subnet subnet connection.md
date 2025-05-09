
By default connection between subnets of a vpc is allowed.
To stop this, you can set up a deny 

![[Pasted image 20250417004904.png]]
Its this rule in nsg that allows it.

ALso, NSG is not the same as SG of AWS, NSG has explicit deny in it, meanwhile SG of AWS doesnt has it.


SO, to deny any subnet from connectingto another subnet, you need too put that rule in priority above than the one shown above, less priority one, ALso, you need to DENY that traffic from the specific CIDR of the subnet.


![[Pasted image 20250417005239.png]]


