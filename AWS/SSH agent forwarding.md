![[Screenshot from 2025-03-30 02-29-16.png]]
- So from the public subnets instance, we cannot do "ssh ip-adress"  to the private subnets instance unless we also have the private key of the instance.
- The other thing to do is to use SSh agent forward.

![[Screenshot from 2025-03-30 02-30-16.png]]
using -A in the "ssh -i -A ".pem" ip-adress" you give away the privaste key to the pbulic subnets instance.


![[Screenshot from 2025-03-30 02-31-04.png]]
add using ssh-add -K ./pemfile

there are other ssh-add functionalities that lets you check which keys are used as agent forwarding, you can check online what these are.


