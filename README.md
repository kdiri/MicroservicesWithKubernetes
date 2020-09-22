# MicroservicesWithKubernetes

The examples of the cours Scalabale Microservices with Kubernetes on Udacity. 


### Public Docker Image

It can be found on my [docker hub](https://hub.docker.com/repository/docker/kdiri/monolith).

### Some Useful K8s Commands
```
kubectl run nginx --image=nginx:1.10.0
kubectl get nodes
kubectl get pods
kubectl describe pods monolith
kubectl create deployment nginx --image=nginx:1.10.0
kubectl create deployment nginx --port 80 --type LoadBalancer
kubectl get service
kubectl config view
# Enter into container
kubectl exec monolith --stdin --tty -c monolith /bin/sh
```
https://kubernetes.io/docs/reference/kubectl/cheatsheet/
