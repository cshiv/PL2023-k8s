# 1. Install k8s cluster on your local machine

## 1.1 Install pre-requisites

Install Docker Engine / Docker Desktop. 
Tools like minikube also support other container manager as listed here https://minikube.sigs.k8s.io/docs/start/#what-youll-need


####  Instructions for installing Docker Desktop

###### For Linux machines (Docker Engine)
$ curl -fsSL https://get.docker.com -o get-docker.sh
$ sh get-docker.sh

###### For Windows
Install Docker Desktop https://docs.docker.com/desktop/install/windows-install/

###### For MacOS
Install Docker Desktop https://docs.docker.com/desktop/install/mac-install/


## 2. Install minikube
Instructions here - https://minikube.sigs.k8s.io/docs/start/

Start the k8s cluster with following command

```minikube start```

If you want more nodes use option -n

```minikube start -n=3```

## 3. Install k3d on your machine

Windows is not a first class citizen for k3d.
https://k3d.io/v5.4.9/#installation

Start the k8s cluster with following command

```k3d cluster create```

If you want more nodes use option -s

```k3d cluster create -s=3```

