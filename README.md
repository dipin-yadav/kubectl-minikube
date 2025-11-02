# Setting up kubectl and minikube on Windows Subsystem for Linux (WSL)

## Prerequisites
- Windows 10/11 with WSL2 enabled
- Ubuntu 20.04 or later on WSL
- At least 2 CPUs and 2GB of free memory
- Administrator access

## Install kubectl

### Download kubectl binary
```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```
### Verify checksum (Optional)
```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"

echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check
```
### Install kubectl binary
```bash
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

kubectl version --client
```
### Enable kubectl autocompletion
```bash
kubectl completion bash | sudo tee /etc/bash_completion.d/kubectl > /dev/null
sudo chmod a+r /etc/bash_completion.d/kubectl
source ~/.bashrc
```

## Install minikube

### Download and install minikube
```bash
curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
```

### Enable minikube autocompletion
```bash
minikube completion bash | sudo tee /etc/bash_completion.d/minikube > /dev/null
sudo chmod a+r /etc/bash_completion.d/minikube
source ~/.bashrc
```

## Start and verify installation

### Start minikube cluster
```bash
minikube start 
```

### Interact with your cluster
```bash
kubectl get po -A
```

### To view Dashboard
```bash
minikube dashboard
```

## Additional Resources
- [Kubectl Documentation](https://kubernetes.io/docs/reference/kubectl/)
- [Minikube Documentation](https://minikube.sigs.k8s.io/docs/)
- [WSL Documentation](https://docs.microsoft.com/en-us/windows/wsl/)
