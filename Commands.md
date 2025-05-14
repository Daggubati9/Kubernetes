## ✅ kubectl config get-contexts

CURRENT   NAME       CLUSTER    AUTHINFO   NAMESPACE
*         minikube   minikube   minikube   default

This is showing your Kubernetes configuration contexts, meaning where kubectl is pointing to (which cluster you're interacting with).

| Column      | Meaning                                                                         |
| ----------- | ------------------------------------------------------------------------------- |
| `CURRENT`   | A `*` means this is the **currently active context**.                           |
| `NAME`      | The name of the context (`minikube` in your case).                              |
| `CLUSTER`   | The Kubernetes cluster name you're connected to (also `minikube`).              |
| `AUTHINFO`  | The credentials you're using to authenticate with the cluster.                  |
| `NAMESPACE` | The default namespace used when running `kubectl` commands (usually `default`). |

## ✅ kubectl config use-context minikube

You're telling kubectl to use the context named minikube, which means:

You're now connected to your local Kubernetes cluster (Minikube).

All your future kubectl commands will talk to this Minikube cluster.

The default namespace is also set (usually default).

## ✅ kubectl get ns

       It shows the namespaces available in your Kubernetes cluster.

## kubectl get pods --namespace kube-node-lease

Show me all the pods running in the kube-node-lease namespace.

## kubectl config set-context --current --namespace=default

This command ensures that all your future kubectl commands run in the default namespace without needing --namespace default every time.

## kubectl apply -f /Users/daggubati/Kubernetes

And the output confirms:

✅ service/web-service is created

✅ deployment.apps/web-app is created

## kubectl get pods

Your pod web-app-7f5c67d78d-nghtk is up and running

## kubectl get services

The name of the whole services

## kubectl get deployments

It looks like your Kubernetes deployment for the web-app is up and running, with one pod successfully deployed and available.

## kubectl get pods

Your web-app pod is running successfully, with both containers inside the pod (2/2 READY) and no restarts. The pod seems to be stable!

## kubectl logs -c apache web-app-7f5c67d78d-nghtk 

is used to view the logs of a specific container within a pod in your Kubernetes cluster.

## kubectl logs -c apache web-app-7f5c67d78d-nghtk -f 

streams the logs in real time from the apache container in the web-app-7f5c67d78d-nghtk pod.

## kubectl exec -it -c apache web-app-7f5c67d78d-nghtk -- bash

allows you to open an interactive shell (bash) inside the apache container of the web-app-7f5c67d78d-nghtk pod.

