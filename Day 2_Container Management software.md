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

## 1. 🟢 Start Minikube

    minikube start

  What it does:
  
  Launches a local Kubernetes cluster using a virtual machine.
  
  Starts all master components (API server, controller, scheduler, etcd) and at least one node.

## 2. 🚀 Deploy an App

  kubectl create deployment demo-app --image=nginx
  
  What it does:
  
  Creates a Deployment named demo-app.
  
  Uses the nginx container image.
  
  Manages a ReplicaSet that maintains 1 Pod running the NGINX web server by default.

## 3. 📈 Scale the App

  kubectl scale deployment demo-app --replicas=3
  
  What it does:
  
  Tells the Deployment to maintain 3 Pods instead of 1.
  
  Kubernetes will automatically create 2 more Pods using the same image and configuration.

## 4. 🌐 Expose the App

    kubectl expose deployment demo-app --type=NodePort --port=80
    minikube service demo-app
    
  What it does:
  
  Creates a Service of type NodePort, exposing the app on a static port on the node.
  
  minikube service demo-app opens the service URL in your browser or returns the URL to access the app externally.

## Result: 🧭 View System Information

    kubectl get nodes
    
  Shows the node(s) in the cluster (just one node in Minikube).

    kubectl get services
    
  Lists services in the default namespace, including demo-app.

    kubectl get pods -n kube-system
    
  Shows system-level pods that run Kubernetes internals (DNS, dashboard, controller, etc).

    k9s
    
  Launches a terminal UI to visually monitor and interact with:
  
  Pods
  
  Services
  
  Deployments
  
  Logs
  
  And more

## Ingress Controller:-

An Ingress Controller is a Kubernetes resource that manages external access (usually HTTP/HTTPS) to services within a cluster. It routes incoming traffic to different backend services based on rules defined in Ingress resources.

