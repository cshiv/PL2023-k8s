# Instructions for using the environment

1. Copy the private key from the Github Gist into a file by name `key`
2. Change the permissions of the private key `chmod 600 key`
3. Using the IP provided, login to the machine with ssh by `ssh -i key ubuntu@<IP>`
4. Once you are logged into the machine, create and start the k8s cluster by running the command `k3d cluster create mycluster`. This might take 30 seconds 
5. Check if the cluster is up by running the following commands `kubectl version` , `kubectl get po -A`. There should be no errors or warnings if cluster is up and running.