This is a very niche topic, and is very necessary.

![[Screenshot from 2025-03-30 15-07-23.png]]
- provides the primary ipv4, but whats the secodnary ips ised for?
- zero or 1 public ip
- if ypu attacj one elactic ip, it gets attached to the private ip, and the public ip gets removed.
- IMPORTANT: Security froups are added to the eni --- how many security groups can be added to it?

### Some properties that we need to be aware of:
![[Screenshot from 2025-03-30 15-10-42.png]]


- Inside the vpc the Public Dns will configure eith the private ip and outside the vpc it eill show the public ip.

### The secondary ENI

Why do we need secondary ENI:
![[Screenshot from 2025-03-30 15-13-19.png]]
- for liscencing.

