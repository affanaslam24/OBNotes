![[Screenshot from 2025-03-25 21-22-23.png]]

so this is how a router makes network transmitiobn possible.
At the same time, notice how newer frames are being made at each route hop, thats because each frame will have the Newer MAC adress of the destination device. Arp is used to find the MAC at each hop asd well. Here the overlaying devices are the routers in between.

**Packet itself remains unchanged throughout the whole transmision**

![[Screenshot from 2025-03-25 21-30-35.png]]
So this is the conclusion of Layer 3.
Also, each packet can only have a packet that has Source IP and Destination IP, so only one stream of data between 2 applications, and thats a limitation.


# Layer 4- Transport layer
So, to tackle layer 3 problems we have layer 4.
As we have discussed, in layer 3 we didnt know the order of the packets, and we didnt know which packets were going for which application ibnside hte system.

Thhis was all tackled by layer 4, tcp udp for ordering and ports segmentations for port maping or something.

So, from now on whenever you think of layer 4 and below, think of this--

![[Screenshot from 2025-03-25 21-41-34.png]]
Layer 1 for direct connections and hubs.
layer 2 for switches and connection between devices. Frames
Arp in between Layer 2 and 3
Layer 3 for IP adress mapping,, routing. Packets.

And Layer 4 for tcp, udp and port mapping.


![[Screenshot from 2025-03-25 21-51-40.png]]
This is the 3 way handshake to make a connection between 2 devices, and through this we can have a sequencing and order maintained between 2 devices.


![[Screenshot from 2025-03-25 21-53-52.png]]
And now we have the [[stateful and stateless]]states.
Just remember the ephemeral ports and the well known port you want to reach, and the rest in inbouhnd and outbound traffic.

As the figure shows, in stateful firewalls the outbound implicitly allows(automatically) inbound **Responses**.
But in statelss firewalls, both the request and responses are seen as seperate things, outbound and oinbound.



NOTE: there are frames in layer 2, then there is packets in layer 3, and in layer 4 we have segments.