its a wrapper on the pod.
- provides autoscaling
- autohealing
![[Pasted image 20250506214201.png]]
it creates something like a replicaset to manage the autoscaling proerty.


replicaset is a kubenetes **controller**.

![[Pasted image 20250506214412.png]]
so how the autohealing wokrs is, you specified in your yaml file that you need a specified numebr of replicas, and the its the replicaset or the controller which makes sure those number of replicas are up and running


![[Pasted image 20250506214555.png]]

easy to change the number of replicas.


**so the dpeloyment makes replicasets which makes use of the controller to maintain the auto healing facilities of the deployment.**


---


![[Pasted image 20250506215322.png]]

 ![[Pasted image 20250506215540.png]]

---

- if you delete a pod, the deployment will use ReplicaSet to create a new pod in its place instanteously. The deletion of pod and the creating will take place at the same time. it hapened parallel. 