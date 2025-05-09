kubectl get pods
kubectl get pods -0 wide (for extra details on all the pods in default namespace)
kubectl logs name
kubectl describe pod name
kubectl get all (to list all pods, deployment, services, etc in default namespace)
kubectl get all -A(to list literally everything, all the details in various namespaces)
kubectll get pods -w (to see real time watching on whats happening to the pods)

how to mmaek chsnges to a service?
- chang ethe service.yaml file for that service, then reapply using kubectl apply -f ...
	- OR use ***kubectl edit svc nameoftheservice.***, this does the editing automatically without having to do 'apply' again.




minikube ssh

