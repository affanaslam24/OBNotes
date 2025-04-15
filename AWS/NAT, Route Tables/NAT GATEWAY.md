So, nat gateways are used to translate private IPv4 to public.

now, you know the baics, so let us talk about the 3 kinds.

one is the static, where we make use of NAT table and a oerfect example would be igw.

the other is dynamic, where we have limited public ip adresses, so we make use of limited number of them to allocate during their time frame. and if the number of ips are all busy, then the private ip would need to wait.

and lastly we have the port adress translation, PAT. the concept which NAT gateways use, its where one single public ip would have more than one port exposed, and each private ip of an instance would get mapped to specific port of the public ip, in a table.


![[Screenshot from 2025-03-28 14-36-40.png]]Static NAT, where one specific private ip has a particular public ip mapped to it. In IGW, it has a table where all this mapping of private to public is already done. 

![[Screenshot from 2025-03-28 14-38-50.png]]
DYNAMIC nat

![[Screenshot from 2025-03-28 14-41-22.png]]NAT gateways.
many to one mapping. Look at how the dource ip and source port are changed at the nat gateway, giving them a source ip and new source port. Also notice how all the new soruce ips are same for each device, but its the new source port which is different. at the same time there is a table maintained which finds the specific devices.


### **How Many Devices Can One NAT Gateway Handle?**

- A **single IPv4 address has 65,536 ports** (`2^16`).
    
- If each device uses **one port per connection**, a single NAT **can theoretically serve 65,000+ devices**.
    
- In real-world usage, a single NAT Gateway can handle **tens of thousands of devices** before needing another public IP.

So NAT in itself solved the problem with billions of ipv4 gettingutilised properly. 

you can have multiple ipv4 private adresses and instances inside a vps, and they can communicatre with each other inside of it however they want, and when they need to access the internet, we use nat gateways and thse gateway terminiologies to make it efficient.