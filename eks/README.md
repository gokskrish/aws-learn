# Pre-Requisites 
* Install awscli
* Install kubectl
* Install eksctl

# Create Cluster
> eksctl create cluster --name my-cluster --fargate

# Delete Cluster
> eksctl delete cluster --name my-cluster

# Other Commands
## Download kube config of existing eks cluster to work with local kubectl 
>  aws eks update-kubeconfig --name sample-eks