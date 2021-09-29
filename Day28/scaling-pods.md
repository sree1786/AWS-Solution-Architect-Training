## kubectl cmds for scaling pods
scaling a deployment:
```
kubectl scale --replicas <number-of-replicas> deployment <name-of-deployment>
```
e.g. set no of replicas for _frontend_ service to _5_ :
```
kubectl scale --replicas 5 deployment frontend
```

## commands to check state
* get all pods incl additional info like e.g. k8s worker node the pod is running on

--> in another putty window

```
watch -n 1 kubectl get pods 
```
* state of service(s)
```
watch -n 1 kubectl get services 
```
details of a particular service:
```
kubectl describe service <servicename>
```
