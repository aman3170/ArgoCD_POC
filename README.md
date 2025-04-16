## ArgoCD_POC
Demonstrate GitOps deployment using ArgoCD by deploying a sample application on a Kubernetes cluster.

# Setup Environment (MacOS)

Commands:
```
brew install minikube
minikube start --driver=docker
```
(if you do not have docker installed, you might see the error)
error:
Exiting due to PROVIDER_DOCKER_NOT_FOUND: The 'docker' provider was not found: exec: "docker": executable file not found in $PATH

Install Docker
```
brew install --cask docker
```
Once Docker is installed and running:
```
minikube start --driver=docker
kubectl version --client
kubectl get nodes
brew install argocd
```
Install ArgoCD on the cluster
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
Expose ArgoCD API Server (for local access)
```
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

# Get initial password
```
kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d
argocd login localhost:8080
```

## Implementation

### 1. Clone this repo
```
git clone https://github.com/<your-username>/argocd-poc.git
cd argocd-poc
```
### 2. Deploy to your cluster
```
kubectl apply -f manifests/namespace.yaml
kubectl apply -f argo-app.yaml
```

### 3. Access the App
Check service IP:
```
kubectl get svc -n argocd-demo
```

### 4. Trigger GitOps

Push any changes to your manifests folder, and ArgoCD will sync them to the cluster automatically!


### UI 

<img width="1470" alt="image" src="https://github.com/user-attachments/assets/ab7949dc-1437-45d6-bca3-23c0b0f1013d" />





