Whether it is docker or k8s the end goal is to deploy application in container.

Pod is the definition of how to run a container.

To run a container in docker you do
```
$docker run -d --name -p -v -network 
```
All above is done in command line.

But in k8s all above specification is written in pod.yml file

A pod can have single container or multiple container.

Only diiference is that you are putting everything in pod.yml file instead of command line.

Why you run things using yaml file?
```
Kubernetes is a enterprise level platform. It want to bring declarative capabilities. Everything is
written in yaml file you have to master yaml.
```

If you have two containers in one pod it will allow shared networking and storage. It means one container 

can talk to another container using localhost.

cluster IPs are generated for pods not for the containers.Kubeproxy generates cluster IPs.

Kubectl is command line for k8s like docker cli.

Steps to create pods:
```
-Install kubectl (check kubectl version)

-create k8s cluster using minikube(only for demo not for production)

-to install minikube and kubectl goto online documentation.

$ minikube start //will create k8s cluster

When you run minikube start, by default, Minikube creates a single-node Kubernetes cluster. This means it
starts with only one node, which acts as both the control plane (master) and the worker node.
If you need more nodes in your cluster, you can use the --nodes flag:

$ minikube start --nodes=<number_of_nodes> //not required for demo

$ kubectl get nodes

Now create pod:
goto pod documentation(don't mug up things)

$vim pod.yml //paste and save

$kubectl create -f pod.yml //creates pod

$kubectl get pods

$kubectl get pods -o wide // gives ip of pod

$minikube ssh //to login to cluster

$kubectl describe pod nginx //to debug, gives everything about pod

If you want to stop pod but want to keep deployment definition

$kubectl scale deployment <deployment-name> --replicas=0

```

Note: In yaml - hyphen indicates objects in a list.

kubectl cheatsheet - very good documentation for commands


Simple pod.yaml file
```
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx:1.14.2
    ports:
    - containerPort: 80

```


Use the following command to delete all resources (e.g., pods, services, deployments) in all namespaces in minikube
```
$ kubectl delete all --all --all-namespaces
```
