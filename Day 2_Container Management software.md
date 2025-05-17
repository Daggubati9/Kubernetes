## 🚢 Container Management Software:

  Software that helps deploy, manage, scale, and monitor containers (e.g., Docker containers). Containers isolate applications for consistency and scalability.
  
  Example: Kubernetes is the most popular container orchestrator.

## 1. 📦 Pod

The smallest deployable unit in Kubernetes. A Pod can have one or more tightly coupled containers. Containers in a Pod share storage, network, and lifecycle.

  kubectl get pods
  kubectl describe pod <pod-name>
