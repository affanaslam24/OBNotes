![[Pasted image 20250412112020.png]]
- its the node that provides any resources to the pods, and the scheduler is designed to work with these nodes to assing pods to them.
- containerD or countere runtime i worker node is used for mainting the container.
- kubelet is what talks with the control plane.
- etcd
- ccm
- kube api server is used for handling api calls between the worker node and control plane
- kube controller works with various controllers. node controller, job, endpoint, service and tokens.
- kube proxy is required for network connection with outside world.

- a storage in kubernetes is ephemeral by default.
- basically, a pod works in a node, and node is nothing but a server, So if by chance the pod changes location and is started in a new node, the storage is lost
- But we canhave persistent storage:
![[Pasted image 20250412124200.png]]



