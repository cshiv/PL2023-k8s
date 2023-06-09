## 1. Creating a Pod

#### 1.1 Run a Pod Imperatively

Run a Pod
```
kubectl run busybox --image=busybox:latest -- sleep 3600
```

Check if the Pod is Running 

```
kubectl get pods
```

Delete the Pod

```
kubectl delete pod busybox
```

#### 1.2 Run your Pod Declaratively

See the Yaml file by dry-run

```
kubectl run busybox --image=busybox:latest -oyaml --dry-run=client -- sleep 3600 > pod.yaml
```
Notice the extra flags `-oyaml` and `--dry-run=client`

Contents of pod.yaml
```
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: busybox
  name: busybox
spec:
  containers:
  - args:
    - sleep
    - "3600"
    image: busybox:latest
    name: busybox
    resources: {}
  dnsPolicy: ClusterFirst
  restartPolicy: Always
status: {}
```


``` 
kubectl apply -f pod.yaml
```
Check if the Pod is Running 
```
kubectl get pods
```

#### 1.3 Helper commands for more information

Check the details of fields
```
kubectl explain pod
```

Check a specific field
```
kubectl explain pod.spec
```

Get more details of the pod

Using `-owide` flag
```
kubectl get pod busybox -owide
```

Using `describe` (Human Friendly)
```
kubectl describe pod busybox
```

Check the different ways to check the k8s object
```
kubectl api-resources | grep pod
```
Output for pod will be this
```
NAME                              SHORTNAMES   APIVERSION                             NAMESPACED   KIND
pods                              po           v1                                     true         Pod
```
All of the below command provides same output.
```
kubectl get pods
kubectl get pod
kubectl get po
kubectl get Pod
```
#### 1.4 Some more operations

Execute a command in the container
```
kubectl exec busybox -- date
```

Create an interactive terminal to the container
```
kubectl exec busybox -ti -- sh
```
Exit from the interactive terminal
```
exit
```


Edit the Pod
```
kubectl edit po busybox
```
Change label of the pod, save the file and exit from the editor mode. Observe that fields can be changed
Now try to change the sleep interval from 3600 to 7200s. Observe that the spec is not changeable.Not all the fields can be modified.

Delete the pod with manifest created
```
kubectl delete -f pod.yaml
```

