So what happens is: you had 3 pods and then they had spepcific ip adresses, and oyu were using these ip addresses for making use of them, but then suddenly one of t hem went down nand sicne oyu were using dpeloyment, the newer pod was up and running in no time, but what we see is that the developer wasnt able to make use of the pod. why?
- because the old pod had a speicific ip address to it. and when a new pod started running, it had a newer ip address.
And similarly, each new pod will have a different ip adress, to tackle this we need a way to work with this.

And thast where services come to play.


Services acts as a load balancer to shuffle between the various pods' ip addresses, thus it acts as an intermediatory to send these requests to the ip addresses of the pods, but at the same time, it also provdes a masking of the ip addresses. if there is any change to ip addresses, the user need not know, it will be the work of the service to connect to the required pod.

**For load balancing purpose, kube proxy is being used**
Internet
   ↓
Cloud Provider Load Balancer (public IP)
   ↓
K8s Service (LoadBalancer type)
   ↓
Kube-proxy → Routes to Pod IP (internal)
   ↓
Pod (10.244.1.10:8080)





 ![[Pasted image 20250506221901.png]]

---
Since, service acts an an intermediatory, how does it manages the same problem itslef? of ip adresses changing again and again?

![[Pasted image 20250506222826.png]]

it uses the concept of label and selectors.
Each pod will have a laber to it, and the service wull make use of these labels and sleectors to connect to the pods.


This is how labels look like:
![[Pasted image 20250506222941.png]]


### Service discorvery process
So the concept of service discover process is this exactly:
![[Pasted image 20250506223023.png]]
It connects based on labels and selectors.



---

functions of services:
![[Pasted image 20250506223357.png]]


---

 the exposing part:
 ![[Pasted image 20250506223525.png]]
so you cant ask people to come inside your kubernetes cluster and then access your pods, with whatever ip addresses they have. for this exposing of the pods to network, you need services to expose it, how does it do it?

- ![[Pasted image 20250506224143.png]]
lets talk about them in details here: [[exposing to net]]


---


![[Pasted image 20250506231400.png]]

this selector is your CONTAINERS label, not your deployment lable.
Also, the target port here was 8000, not 80. 8000 is the port that the container was ready to expose.

![[Pasted image 20250506231642.png]]
here, the 80:30007, means, the pod is available on **port 80 of the node**, and ouur cluster is mapping port 30007 with the port 80.
so we will get something on 30007.


![[Pasted image 20250506232513.png]]
the label for the container.


