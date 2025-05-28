
region specific- like you are in india, then you will be routed to mumbai server. so region specific demand by the compnay is geolocation

geoproximity: region specific only, but can be delegated to a specific resource. like, you want users form india to connect to europe server. this is region rpecific demand. like the users from india specifically.

latency: means whichever server is providing better latency, get attached to it.


![](https://media.tutorialsdojo.com/how-route-53-routes-traffic.png)

this is propagation  model.


A company runs a messaging application in the `ap-northeast-1` and `ap-southeast-2` region. A Solutions Architect needs to create a routing policy wherein a larger portion of traffic from the Philippines and North India will be routed to the resource in the `ap-northeast-1` region.

Which Route 53 routing policy should the Solutions Architect use?

- geoproximity

