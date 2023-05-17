## 1. Creating a Deployment

Run a deployment (Location in Repo - yaml/deploy.yaml)
```
kubectl apply -f https://raw.githubusercontent.com/cshiv/PL2023-k8s/main/yaml/deploy.yaml
```

Check the deployment
```
kubectl get deployment
```

Check the pods associated with the specific deployment
```
kubectl get po -l app=busybox
```

Delete one of the pod of deployment
```
kubectl delete po <pod-name>
```
Observe a new pod is being created with a different hash

Scale deployment
```
kubectl scale deploy/deploy-busybox --replicas 3
```

Check the pods of the deployment and the replicas
```
kubectl get po -l app=busybox
```

Scale down by editing deployment object
```
kubectl edit deploy deploy-busybox
```
Set the value in `spec.replicas` to 2. Save the file and exit the editor.

Delete the deployment 
```
kubectl delete deploy deploy-busybox
```
