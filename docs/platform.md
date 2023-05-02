# Use free kubernetes cluster provided with Percona Portal 
Login to Percona Portal https://portal.percona.com/

### 1. Create a Percona Portal Account 
![image](https://user-images.githubusercontent.com/60964203/235717779-27d032cf-de81-4d8b-9118-dbc22a3830e5.png)

### 2. Enter details and create account
![image](https://user-images.githubusercontent.com/60964203/235716785-b6b444e0-0b13-424f-bad8-521f7693d4e3.png)

### 3. Activate account 
![image](https://user-images.githubusercontent.com/60964203/235717079-e2cfe9de-b14b-485a-a86f-57c3aad9fc30.png)

### 4. Login to the platform
https://portal.percona.com/login

![image](https://user-images.githubusercontent.com/60964203/235718520-ef3c2bfa-9f12-480f-8d8f-4b95d3afc6ba.png)

### 5. Create PMM Demo
![image](https://user-images.githubusercontent.com/60964203/235734150-1d12bea7-1be6-4022-973c-acb5e4d76c92.png)

### 6. Copy kubeconfig of the k8s cluster

![image](https://user-images.githubusercontent.com/60964203/235730457-a6bd56e2-3712-4fd6-9e07-4e5cba999cf6.png)

### 7. Save it in a file and set the environment variable KUBECONFIG to the location of file

**Linux Bash / Mac OS**
export KUBECONFIG=./config

**Windows**
set KUBECONFIG=%CD%\config.txt

### 8. Check cluster from kubectl client

```
$ kubectl version
Client Version: version.Info{Major:"1", Minor:"24", GitVersion:"v1.24.1", GitCommit:"3ddd0f45aa91e2f30c70734b175631bec5b5825a", GitTreeState:"clean", BuildDate:"2022-05-24T12:26:19Z", GoVersion:"go1.18.2", Compiler:"gc", Platform:"linux/amd64"}
Kustomize Version: v4.5.4
Server Version: version.Info{Major:"1", Minor:"23", GitVersion:"v1.23.6+k3s1", GitCommit:"418c3fa858b69b12b9cefbcff0526f666a6236b9", GitTreeState:"clean", BuildDate:"2022-04-28T22:16:18Z", GoVersion:"go1.17.5", Compiler:"gc", Platform:"linux/amd64"}
```



