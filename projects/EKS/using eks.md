- with EC2, it can be highly available, but you have to configure the load balancer, you have to maintain the thershold scsling and everything
- With fargate, everything comes out of the box

![[Pasted image 20250421221925.png]]
- eks maintains the downloadingof dependencies inside the cluster, for worker nodes and master nodes.
- its a manged service
- it manages the limitations of: certificate failure, api servwr cradshing, etcd crashing adne tc that wwe saw in KOPS method of using kubeadm and configuring our own cloud cluster.
- other way of making a kubernete cluster is on premesis.

