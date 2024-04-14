# [K3d - How to run Kubernetes cluster locally using Rancher k3s]

#########

# Setup

#########

# Install `k3d` CLI (https://k3d.io/#installation)

#################################

# Creating single-node clusters

#################################

export KUBECONFIG=$PWD/kubeconfig.yaml

k3d cluster create my-cluster

docker container ls

kubectl get pods -A

kubectl get nodes

################################

# Creating additional clusters

################################

k3d cluster create another-cluster \
 --image rancher/k3s:v1.20.4-k3s1

docker container ls

#####################

# Deleting clusters

#####################

k3d cluster delete my-cluster

k3d cluster delete another-cluster

#####################################

# Creating clusters through configs

#####################################

git clone https://github.com/kevAnto/k3d-demo.git

cd k3d-demo

cat k3d.yaml

k3d cluster create --config k3d.yaml

kubectl get nodes

kubectl apply --filename k8s/

# Open http://localhost in a browser

#####################

# Deleting clusters

#####################

k3d cluster delete my-cluster

###########################

# Speed test against kind

###########################

docker system prune -a -f --volumes

k3d cluster create my-cluster

k3d cluster delete my-cluster

#

kind create cluster --name my-cluster

kind delete cluster --name my-cluster
