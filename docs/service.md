# 1. Create a Service

Create a nginx deployment with 3 Replicas
```
kubectl apply -f https://raw.githubusercontent.com/cshiv/PL2023-k8s/main/yaml/nginx-deploy.yaml
```

Check if all the pods are in Running state
```
kubectl get pods
```
Status should be `Running`

Create a Service
```
kubectl apply -f https://raw.githubusercontent.com/cshiv/PL2023-k8s/main/yaml/service.yaml
```

Check the Service created
```
kubectl get service
```
Use the IP of the services to reach <IP>:80
Is the IP reachable?

Check the command
```
kubectl port-forward --help
```

Port-forward to the service
```
kubectl port-forward service/service-nginx 8080:80
```
Using 8080 as port 80 will generally be bound

Open the nginx webpage by hitting the URL `127.0.0.1:8080` or `curl 127.0.0.1:8080`

NOTE: kubectl port-forward doesn't do loadbalancing unlike regular :(