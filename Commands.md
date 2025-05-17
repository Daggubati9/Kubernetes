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

## ✅ kubectl get pods --namespace kube-node-lease

Show me all the pods running in the kube-node-lease namespace.

## ✅ kubectl config set-context --current --namespace=default

This command ensures that all your future kubectl commands run in the default namespace without needing --namespace default every time.

## ✅ kubectl apply -f /Users/daggubati/Kubernetes

And the output confirms:

 service/web-service is created

 deployment.apps/web-app is created

## ✅ kubectl get pods

Your pod web-app-7f5c67d78d-nghtk is up and running

## ✅ kubectl get services

The name of the whole services

## ✅ kubectl get deployments

It looks like your Kubernetes deployment for the web-app is up and running, with one pod successfully deployed and available.

## ✅ kubectl get pods

Your web-app pod is running successfully, with both containers inside the pod (2/2 READY) and no restarts. The pod seems to be stable!

## ✅ kubectl logs -c apache web-app-7f5c67d78d-nghtk 

is used to view the logs of a specific container within a pod in your Kubernetes cluster.

## ✅ kubectl logs -c apache web-app-7f5c67d78d-nghtk -f 

streams the logs in real time from the apache container in the web-app-7f5c67d78d-nghtk pod.

## ✅ kubectl exec -it -c apache web-app-7f5c67d78d-nghtk -- bash

allows you to open an interactive shell (bash) inside the apache container of the web-app-7f5c67d78d-nghtk pod.

## ✅ docker volume ls

       Purpose: Lists all Docker volumes.
       
       Use Case: Check existing volumes used for persistent storage in containers.

## ✅ docker stack ls

       Purpose: Lists all the deployed stacks in Docker Swarm.
       
       Use Case: Useful to see which stack-based applications are currently running.

## ✅ docker service ls

       Purpose: Lists all the services running in Docker Swarm mode.
       
       Use Case: Shows you services under each stack (name, replicas, image, etc.).

## ✅ docker kill <container_id or name>

       Purpose: Forcefully stops and removes the specified container.
       
       Example: docker kill jenkins

## ✅ docker ps

       Purpose: Lists all the running containers.
       
       Use Case: To check the status, container IDs, names, images, etc.

## ✅ docker swarm init

       Purpose: Initializes the current Docker engine as a manager node in Swarm.
       
       Use Case: Step one for setting up Docker Swarm.

## ✅ docker swarm

       Purpose: Displays help and available subcommands for Docker Swarm.
       
       Use Case: To explore what can be done under Swarm mode.

## ✅ docker node ls

       Purpose: Lists all nodes in the Swarm (only visible from the manager node).
       
       Use Case: Helps monitor and manage the cluster.

## ✅ docker swarm join-token

       Purpose: Generates a command to join a new node to the Swarm.
       
       Example: docker swarm join-token worker or manager

## ✅ docker swarm join-token --help

       Purpose: Displays help for the join-token command.

## ✅ docker swarm join-token worker

       Purpose: Shows the token and command needed to join a node as a worker to the swarm.

## ✅ docker stack deploy -c <path> <stack_name>

       Purpose: Deploys a stack defined in a docker-compose.yml file to the Swarm.
       
       Example: docker stack deploy -c docker-compose.yml mystack
