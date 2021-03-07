# kubernetes commands

kubectl get nodes
kubectl get pods --all-namespaces
kubectl get namespace
kubectl get nodes -o=wide
kubectl get pods

# Installing minikube on mac

## Check to see if virtualization is supported
sysctl -a | grep -E --color 'machdep.cpu.features|VMX'

## Install Virtualbox with Brew (info at brew.sh)
brew cask install virtualbox
 
## Install Minikube with Brew
 brew cask install minikube

## Install Kubectl
brew install kubernetes-cli

## Install the Docker Client
brew install docker

## Start Minikube
minikube start

## Configure the Docker Client
minikube docker-env

# Running your first container

kubectl create deployment --image nginxdemos/hello web1

kubectl describe deploy web1

kubectl get pods

kubectl get deployment

kubectl scale deployment --replicas 20 web1

kubectl get pods -w

kubectl expose deployment web1 --port=80 --type=LoadBalancer

kubectl get services

minikube service web1

kubectl get deploy web1 -o=yaml
kubectl delete deployment web1
### Imperative vs Declarative
In the imperative model we tell the api what we want it to do using kubectl
command. Like run nginx.

kubectl run nginx --image=nginx
### Declarative model is where we specify exactly what needs to be done using a
manifest file. i.e. Ensure that this gorup of 5 web servers and 2 db servers are
running at all times with X exposed ports and these resources allocations. If
they aren't, restart them.

kubectl apply -f 
## Monitoring application
alias k=kubectl
kubectl api-resources

# Get pods 
kubectl get pod

# Get deployments
kubectl get deployment

# Describe pods 
kubectl describe pod

# Describe deployment 
kubectl describe deploy

# View logs
kubectl logs <podname>

# Scale 
kubectl scale deploy <deployment-name> --replicas=20

# Autoscaling is possible with the autoscale command
kubectl autoscale deployment <deployment-name> --min=2 --max=10

