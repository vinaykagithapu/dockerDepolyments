# Kubernetes Cluster on Docker - Kind 
This will guide you to setup kubernetes cluster on docker

## Kind
kind is a tool for running local Kubernetes clusters using Docker container “nodes”.
kind was primarily designed for testing Kubernetes itself, but may be used for local development or CI. 

## Requirements
1. Docker ([Docker Installation](https://github.com/vinaykagithapu/dockerSetUp-Ubuntu.git))
2. Install kubectl
```shell
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
mkdir -p ~/.local/bin
mv ./kubectl ~/.local/bin/kubectl
# and then append (or prepend) ~/.local/bin to $PATH
echo "export PATH=$PATH:$HOME/.local/bin" >> ~/.bashrc
```


# Getting Started

## Install Kind
1. Download kind binary and add to PATH.
```shell
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.15.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```


## Create a Basic Kubernetes Cluster
1. To create a simple single node kubernetes cluster.
```shell
kind create cluster
```

## Create Multi Node Kubernetes Cluster
1. We can change [kind-config.yaml](multiNodeCluster/kind-config.yaml) based on requirements
```shell
kind create cluster --name multi-node-cluster --config multiNodeCluster/kind-config.yaml
```

## Create Multiple Control-plane Nodes Cluster
1. We can change [kind-config.yaml](multiControlPlaneCluster/kind-config.yaml) based on requirements. 
```shell
kind create cluster --name multi-controlplane-cluster --config multiControlPlaneCluster/kind-config.yaml
```

## Verify
1. Get cluster
```shell
kind get clusters
```
2. Get nodes using kubectl
```shell
kubectl get nodes
```

# CleanUp
1. Destroy a simple kubernetes cluster
```shell
kind delete cluster
```
2. Destroy multi node cluster.
```shell
kind delete cluster --name multi-node-cluster
```
3. Destroy multi control plane cluster.
```shell
kind delete cluster --name multi-controlplane-cluster
```