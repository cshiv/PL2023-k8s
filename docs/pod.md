## 1. Pod

Run a Pod Imperatively

```kubectl run busybox --image=busybox:latest -- sleep 3600```

Check if the Pod is Running 

```kubectl get pods```

Execute a command in the container

```kubectl exec busybox -- date```

Create an interactive terminal to the container

```kubectl exec busybox -ti -- sh```

Delete the Pod

```kubectl delete po busybox```