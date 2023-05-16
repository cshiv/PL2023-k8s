# 1. Create a Service and a Headless Service

StatefulSet needs a headless service.
Let's start by creating a headless service
```
kubectl apply -f https://raw.githubusercontent.com/cshiv/PL2023-k8s/main/yaml/svc-headless.yaml
```
Notice the setting `spec.clusterIP` is `None`

Let's create a regular service with same label selectors. We have not mentioned `spec.clusterIP` in this yaml file
```
kubectl apply -f https://raw.githubusercontent.com/cshiv/PL2023-k8s/main/yaml/svc-regular.yaml
```
We will get back on why we created this later.

Check if the service is created
```
kubectl get service
```

Create a StatefulSet
```
kubectl apply -f https://raw.githubusercontent.com/cshiv/PL2023-k8s/main/yaml/stateful.yaml
```

Check the status of StatefulSet 
``` 
kubectl get statefulset
```

Check the pods associated with statefulset and wait till it changes to `Running` state
```
kubectl get po -owide
```

Delete any of the pod.
```
kubectl delete po mysql-0
```
Check for the newly created pod
```
kubectl get po
```
As you can see k8s automatically creates the pod and ensure replica of stateful set remains the same.

Run a mysql client pod to connect to DB
```
kubectl run client --image=percona:8.0 -ti -- bash
```

#### Comands inside the container

**Checking the Resolution** 

Check the file `/etc/resolv.conf`

```
cat /etc/resolv.conf
```
This entry is added by the kubelet based on the DNS settings
`search` entry has that can help in resolving service in the same namespace
Observe the entry `default.svc.cluster.local` 

```
getent hosts mysql-headless
```

Check the resolution with FQDN

```
getent hosts mysql-headless.default.svc.cluster.local
```
Observe the output of 2 IPs , which are pod IP

Try to check the resolution of individual pod
```
getent hosts mysql-0.mysql-headless.default.svc.cluster.local
```
```
getent hosts mysql-1.mysql-headless.default.svc.cluster.local
```

Connect to Mysql Pod
```
mysql -h mysql-1.mysql-headless -u root -ppassword
```
This works for other pod `mysql-0.mysql-headless` as well.
Observe that it's a standalone node, but not a part of cluster.
```
select * from performance_schema.replication_group_members;
```
Exit from the mysql prompt
```
exit
```

# 2. Difference between a clusterIP and a headless service

Ensure you have opened an interactive terminal to the bash pod.

Check the resolution of regular service
```
getent hosts mysql-regular
```
As you can observe only the IP of loadbalancer is provided, unlike all the pod IP in case of a headless service.

DNS entry for individual pod are not added in the clusterIP.
```
getent hosts mysql-0.mysql-headless
```

Now connect to the mysql using clusterIP service.
```
mysql -h mysql-regular -u root -ppassword
```
Check the hostname
```
select @@hostname;
```

Repeat the above 2 commands after exiting mysql prompt and observe a different host being hit.



