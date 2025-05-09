All of these in worker nodes
- CNI= container network interface
- container runtime= CR
- DNS
- KUBEPROXY
In control plane/master nodes:

Master node has:
- ETCD
- Api Server
- scheduler
- cloud manager
- contorller manager
So, install or configure all of these in the master node, ALong with KUBEADM.


AND THEn, join the worker node with the master node.


OR alternatively, you can use KOPS, share your AWS credentials, and then it creates the required nubmer of master and worker nodes,
BUt the porblems with that is:
- one of the master node goes down
- certificate expires
- etcd is crashed
- api server goes down
- scheduler is not working
KOPS creates the k8s cluster for you, but at the end of the day, its you who manages the integral parts and maintance overhead still remains.


![[Pasted image 20250421203630.png]]


