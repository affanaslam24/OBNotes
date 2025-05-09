![[Pasted image 20250506213300.png]]


check your **logs** or **desrcibe**

kubectl describe pod name
kubectl logs name 


---

difference between docker container and pods?
- pods give you a declarative way of making containers.
- instead of running your container in docker using imperative standard, like docker run -it or docker build -d..., you are now using a yaml file to create everything inside your yaml file and then running it using kubectl.
- benefits? you get to check latr on on what changes you made to your docker as well as, everything about your container is in one pllace.

you can also have multiupe containers isnide one pod-
why?
	you can share config files together, or oyu need 2 pods to have highly portable shared volume as well as share network capabilities.


---

- pods dont provide the auto healing feature by itself, you can delete a pod, and its done.