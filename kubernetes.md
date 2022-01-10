# Kubernetes

In dev - use minikube
- use 'minikube' for managing the VM itself
- use 'kubectl ' for managing the containers in the node


In prod: 
- AWS EKS
- Google GKE
- DIY

- Master node control worker/minion nodes
- 

Components:
- API server
- etcd -  k/v store 
- scheduler - distributing containers across nodes
- controller - brains behind orchestration. 
- container runtime - underlying software to run container (e.g. docker, rkt, cri-o)
- kubelet - agent that runs on each node in the cluster.

The following components are installed on a **'Master'** node:
- kube-apiserver
- etcd
- controller
- scheduler

The following components are installed on **'Worker'** nodes:
- kubelete
- container runtime


- `Minikube` contains all 6 services. Can use to run locally
- Can use `kubeadm` to test multi-node cluster locally
- Install `kubectl` before installing `minikube` to allow `minikube` to automatically configure `kubectl`.


- A Kb 'Pod' group of one or more containers.
- A Kb 'Deployment' checks on the health of your Pod and restarts the Pod's Container if it terminates. Deployments are the recommended way to manage the creation and scaling of Pods.

- Create a deployment:
 `kubectl create deployment hello-node --image=k8s.gcr.io/echoserver:1.4`
- View deployments:
`kubectl get deployments`
- View pods:
`kubectl get pods`
- View events:
`kubectl get events`


- Need to 'expose' service so that pod is accessible outside its internal IP with Kb cluster.
`kubectl expose deployment hello-node --type=LoadBalancer --port=8080`
- View services created:
`kubectl get services`
- Use minikube  to start service created
`minikube service <name-of-service>`

Teardown/Cleanup:
- delete service
`kubectl delete services hello-minikube`
`kubectl delete deployment hello-node`



Pods:
- Containers are encapsulated in pods, a single instance of an application.
- A pod is smallest object you can create in Kb
- When scaling, you don't increment container in pod, instead you spin up new pod.
- If node has no more capacity for more pods, then spin up new node.
- pod and container have 1:1 relationship if same type of container. BUT a 'helper container' can co-exist within the same pod.
-  For example `kubectl run nginx --image nginx` will deploy nginx inside a pod. `run <pod-name>`
- `kubectl get pods`
- `kubectl describe pod nginx`



Kubectl commands:
- `kubectl version` 
- `kubectl cluster-info`
- `kubectl run hello-minikube`
- `kubectl get nodes`

Minikube commands:

- `minikube status`
- `minikube start --vm-driver=<driver_name>`


References:
- https://kubernetes.io/docs/tutorials/_print/
