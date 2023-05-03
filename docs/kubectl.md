# Install kubectl on machine

### [Install on Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/)
### [Install on Mac](https://kubernetes.io/docs/tasks/tools/install-kubectl-macos/)
### [Install on Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/)

# Check the installation

```
$ kubectl version
Client Version: version.Info{Major:"1", Minor:"24", GitVersion:"v1.24.1", GitCommit:"3ddd0f45aa91e2f30c70734b175631bec5b5825a", GitTreeState:"clean", BuildDate:"2022-05-24T12:26:19Z", GoVersion:"go1.18.2", Compiler:"gc", Platform:"linux/amd64"}
Kustomize Version: v4.5.4
Server Version: version.Info{Major:"1", Minor:"25", GitVersion:"v1.25.7+k3s1", GitCommit:"f7c20e237d0ad0eae83c1ce60d490da70dbddc0e", GitTreeState:"clean", BuildDate:"2023-03-10T22:16:07Z", GoVersion:"go1.19.6", Compiler:"gc", Platform:"linux/amd64"}
```
Both client and server version should be visible when properly connected to k8s cluster.
