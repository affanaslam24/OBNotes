Role based access control:
- how you manage different users access to your cluster.
- how you manage your services to have access to other services, are they allowed to access other pods or service, are they allowed to send traffic, are they allowed to access the secret or confug map etc, is the service trying to disturb your cluster by deletign the files on etcd or api server etc.
So managing the access of user on your cluster, and access of services inside oyurt cluster on your cluster.


Three things in rbas:
![[Pasted image 20250507223916.png]]

- service account can be easily created, but users are something that is being made usuing identity management providers, like google, iam, etc.
Maybe youre using eks or aks as your cluster, then they have their IAM to create users and offload this user management rbac to them.


![[Pasted image 20250507224408.png]]


so its the api server which user a certain ***flag***, this flag is basically oauth service flag or sommething, and when a user tries to access the cluster, they need to provide the iam oauth privder which matches with the flag of the api server.


![[Pasted image 20250507224556.png]]

you can also use eks with keycloak, and then integrate it with github, so in this way you can share the cluster with contributors to a specific repo.


---

Service accounts are created jjusst like your pods.
### service account


- **interestingly, a pod always creates a service account for itself. This SA is how the api server talks with your pod.** 
- you can create your custom SA, but if you dont create one, a default one is attached to your pod.
---


What are role and role bindings?
![[Pasted image 20250507224905.png]]

so the SA you created, or the user that you have, they will need to have access management done. But how to work with this? you make use of roles and BIND these roles to these users or SA.

**Roles:**
Think of them as policies in IAM. You write down what can a user or service account has access toor can do, like config maps access, secrets, pod restrictions etc. 
![[Pasted image 20250507225532.png]]

**Role Binding:**
is where you bind these roles to a specific entity.

---

![[Pasted image 20250507225720.png]]

