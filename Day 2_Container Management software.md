## 🚢 Container Management Software:

  Software that helps deploy, manage, scale, and monitor containers (e.g., Docker containers). Containers isolate applications for consistency and scalability.
  
  Example: Kubernetes is the most popular container orchestrator.

## 1. 📦 Pod

The smallest deployable unit in Kubernetes. A Pod can have one or more tightly coupled containers. Containers in a Pod share storage, network, and lifecycle.

    kubectl get pods
    
    kubectl describe pod <pod-name>

## 2. 🖥️ Node

A physical or virtual machine where Pods run. Nodes are the underlying compute resource.

  Master Node: Controls the cluster.
  
  Worker Node: Runs application Pods.

    kubectl get nodes
    
    kubectl describe node <node-name>
    
## 3. 🧱 Node Pool

A group of nodes with the same configuration (used mostly in cloud Kubernetes). Helps manage scaling and types of workloads.
Not directly visible in Minikube, but can be discussed theoretically.

## 4. 🌐 Cluster

A group of nodes managed by Kubernetes. One control plane (master), many worker nodes. Makes the deployment scalable, reliable, and manageable.

    kubectl cluster-info
    
## 5. 🧩 Kubernetes Components

## 🔧 Master Service Components:

    API Server: Front door of Kubernetes.
    
    Scheduler: Decides which node runs which Pod.
    
    Controller Manager: Watches and maintains cluster state.
    
    etcd: Key-value store for config and cluster data.

## ⚙️ Workload Components (on Worker Nodes):

    Kubelet: Talks to the API Server and runs containers.
    
    Kube-proxy: Handles networking.
    
    Container Runtime: Docker, containerd, etc.

    kubectl get pods -n kube-system
    
## 6. 🚀 Deployment

A Kubernetes object that manages Pods — ensuring the correct number of replicas and enabling rolling updates. Helps manage application versioning and scaling.

    kubectl create deployment nginx-deploy --image=nginx
    kubectl get deployments
    kubectl scale deployment nginx-deploy --replicas=3
    
## 7. 🌉 Service

A stable way to access a group of Pods. Pods have dynamic IPs; services provide stable access.

  ClusterIP: Internal.
  
  NodePort: Accessible via node’s IP and port.
  
  LoadBalancer: External traffic (cloud).

    kubectl expose deployment nginx-deploy --type=NodePort --port=80
    minikube service nginx-deploy
    
## 8. 🌐 Ingress

A controller that routes external traffic to services using HTTP/HTTPS paths. Reduces the need for many NodePorts or LoadBalancers.
Ingress requires setup a YAML file.

## 9. 📤 Egress

Outbound traffic from Pods (e.g., calling external APIs). Useful for internet access, security policies. Not a visible object like Service/Ingress.

## 10. 🗂️ Namespace

Logical separation in a Kubernetes cluster (like folders). Organizes and isolates resources.

  default
  
  kube-system
  
  dev, prod, etc.

  kubectl get namespaces
  kubectl get pods --namespace=kube-system
  
## 11. 📺 K9s

Terminal-based UI to view and manage Kubernetes clusters easily. Gives a real-time overview of pods, deployments, services, logs, etc.

    k9s
    
Example:

