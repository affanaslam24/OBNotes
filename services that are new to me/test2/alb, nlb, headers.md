If your application is composed of several individual services, an Application Load Balancer can route a request to a service based on the content of the request such as Host field, Path URL, HTTP header, HTTP method, Query string, or Source IP address.

![](https://media.tutorialsdojo.com/alb-grpc-support.jpg)

ALBs can also route and load balance gRPC traffic between microservices or between gRPC-enabled clients and services. This will allow customers to seamlessly introduce gRPC traffic management in their architectures without changing any of the underlying infrastructure on their clients or services.

Therefore, the correct answer is: **Configure an Application Load Balancer in front of the auto-scaling group. Select gRPC as the protocol version.**

The option that says: **Configure a Network Load Balancer in front of the auto-scaling group. Use a UDP listener for routing** is incorrect. Network Load Balancers do not support gRPC.

The option that says: **Configure a Gateway Load Balancer in front of the auto-scaling group. Ensure that the IP Listener Routing uses the GENEVE protocol on port 6081 to allow gRPC response traffic** is incorrect. A Gateway Load Balancer operates as a Layer 3 Gateway and a Layer 4 Load Balancing service. Do take note that the gRPC protocol is at Layer 7 of the OSI Model so this service is not appropriate for this scenario.