# Setup sample guestbook app
* based on https://github.com/kubernetes/examples/tree/master/guestbook

## Redis master
deploy the master Redis pod and a _service_ on top of it:
```
kubectl apply -f redis-master.yaml
watch -n 1 kubectl get pods --> in another putty window
watch -n 1 kubectl get services --> in another putty window
watch -n 1 kubectl get all -o wide --> in another putty window
```

## Redis slaves
deploy the Redis slave pods and a _service_ on top of it:
```
kubectl apply -f redis-slaves.yaml
watch -n 1 kubectl get pods --> in another putty window
watch -n 1 kubectl get services --> in another putty window
watch -n 1 kubectl get all -o wide --> in another putty window
```

## Frontend app
deploy the PHP Frontend pods and a _service_ of type **LoadBalancer** on top of it, to expose the loadbalanced service to the public via ELB:
```
kubectl apply -f frontend.yaml
```
some checks:
```
kubectl get pods
watch -n 1 kubectl get pods -l app=guestbook
watch -n 1 kubectl get pods -l app=guestbook -l tier=frontend
```
check AWS mgm console for the ELB which has been created !!!

## Access from outside the cluster
grab the public DNS of the frontend service LoadBalancer (ELB):
```
kubectl describe service frontend
```
copy the name and paste it into your browser !!!
