![[Pasted image 20250506224209.png]]
1. clusterIp, is where your ip is shared only isnide your cluster.
2. nodeport is where it can be accesed insidb eoyur organisation, basically who ever has access to your worker node.
3. and then we use load balancing, this type only works with eks or other facilities which provides integration with load balancers.


So, if you want the whole world to access your pods, use load balancing.
If you want only peopole who have access to your cluster, ;llike the vpc or the worker nodes, then use nodeport mode.
If you want only the devops guy or people specifically making changes or usingthe cluster, then use ClusterIp, basically where the ip is shared inside your cluster.


 ![[Pasted image 20250506224905.png]]
