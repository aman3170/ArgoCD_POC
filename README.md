# ArgoCD_POC
Demonstrate GitOps deployment using ArgoCD by deploying a sample application on a Kubernetes cluster.


Commands:

brew install minikube
minikube start --driver=docker

error: 
Exiting due to PROVIDER_DOCKER_NOT_FOUND: The 'docker' provider was not found: exec: "docker": executable file not found in $PATH

brew install --cask docker

Once Docker is installed and running:

minikube start --driver=docker

kubectl version --client
kubectl get nodes

brew install argocd



