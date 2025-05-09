![[Pasted image 20250507230939.png]]

adding the helm repo for prometheus.

Now install:
![[Pasted image 20250507231008.png]]

it downloades a couple of pods:
![[Pasted image 20250507231111.png]]

![[Pasted image 20250507231237.png]]
we need to expose the promethuis server from clusterip to nodeport.

---

Now grafana:
![[Pasted image 20250507231429.png]]

You need the password toy our grafana:
![[Pasted image 20250507231508.png]]

And similarly expose your granafa service:
![[Pasted image 20250507231533.png]]



Now, create promethius as a data soruce for your grafana, because grafana is your chart creation tool.

3662


---

to check for other metrics of the cluster:
![[Pasted image 20250507232004.png]]

like here, we are checking for state metric. So we are exposing it at port 8080(it was mentioned in the kubectl get svs tab)

So now itll have 2 metrics:
![[Pasted image 20250507232130.png]]
