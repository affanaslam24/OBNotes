![[Screenshot from 2025-03-30 02-12-24.png]]

THIs is how it looks like:

![[Screenshot from 2025-03-30 02-15-02.png]]


- It resides in the public subnets, always.
- the private subnet has a route table associated with it that connects it to the nat gateway.
- idk but the route table in the public subnet will propogate the traffic from nat gateway to igw, ig. **Check online.**

An impportant difference:
![[Screenshot from 2025-03-30 02-17-27.png]]

![[Screenshot from 2025-03-30 02-17-41.png]]

- YOu notive that the source ip at first is the internal ip of the nat gateway, and then at the IGW level the public Ip of the nat gateway is attached.


### Key notes:
![[Screenshot from 2025-03-30 02-19-34.png]]

- By default its Az resilient, but to make it Region resilient, add nat gateway to each Az of that vpc.
- Q. can one nat gateway be used for all the subnets? will have to check.
- uses elastic IPs.

###### Difference between Nat instacne and gateway:
![[Screenshot from 2025-03-30 02-25-46.png]]

**important: security group cant be associated with nat gateways!! how does it makes a difference, i dont know. So we will check Chat gpt later on.**
Port forward is not supported.

What about IPv6?
![[Screenshot from 2025-03-30 02-27-08.png]]

