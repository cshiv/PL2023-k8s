# 1. Create a PersistentVolumeClaim

Create a Persistent Volume Claim by using the default Storage Class
```
kubectl apply -f https://raw.githubusercontent.com/cshiv/PL2023-k8s/main/yaml/pvc.yaml
```
If no StorageClass is specified, default storage class is used

Check the PVC Created
```
kubectl get pvc
```
Is your PVC status `Pending` or `Bound` ?

Provision of the volume depends on `volumeBindingMode` property in the StorageClass.
Possible values are `Immediate` or `WaitForFirstConsumer`.
`Immediate` provisions PersistentVolume immediately even without any pod actively present for using the PersistentVolumeClaim.
`WaitForFirstConsumer` will keep the PersistentVolumeClaim in Pending status and will create the PersistentVolume only after a Pod requests it.

Check the StorageClass present
```
kubectl get storageclass
```

Check details of specific storage class by `kubectl get storageclass <storage-class-name> -oyaml
Notice the annotation `storageclass.kubernetes.io/is-default-class: "true"`

# 2. Create a mysql pod to use the persistent volume claim

Create pod by name `mysql-1`
```
kubectl apply -f https://raw.githubusercontent.com/cshiv/PL2023-k8s/main/yaml/mysql-1.yaml
```

Check the status of the pod and wait till pod is in `Running` state
```
kubectl get po
```

Once the pod is in running state, exec into the container
```
kubectl exec -ti mysql-1 -- bash
```

##### Commands in mysql container

Login to the mysql server, use appropriate password.

```
mysql -u root -ppassword
```

Show the databases present
```
show databases;
```

Create a database by name `perconalive_2023`
```
create database perconalive_2023;
```

Validate the database creation
```
show databases;
```

Exit the mysql prompt and container by exit.

Kill the mysql pod !!!

```
 kubectl delete po mysql-1
```

Check the pods to see the mysql-1 pod is deleted.
```
kubectl get po
```

Notice the pvc is still present and bound
```
kubectl get pvc; kubectl get pv
```

# 3. Create a new mysql pod to retain the data

Create a new mysql pod to use the existing data
```
kubectl apply -f https://raw.githubusercontent.com/cshiv/PL2023-k8s/main/yaml/mysql-2.yaml
```

Check the status of the pod and wait till pod is in `Running` state
```
kubectl get po
```

Once the pod is in running state, exec into the container
```
kubectl exec -ti mysql-2 -- bash
```

##### Commands in mysql container
Login to the mysql server, use appropriate password.

```
mysql -u root -ppassword
```

Check if `perconalive_2023` database is present
```
show databases;
```

Observe the data is retained eventhough the initial pod was deleted.


Exit the mysql prompt and container by exit.

Kill the mysql pod !!!

```
 kubectl delete po mysql-2
```