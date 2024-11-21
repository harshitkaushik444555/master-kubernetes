

Deployment
```
A deployment is used to maintain a desired state of an application. Deployment create replica set and replica set create pods.
```

What is the difference between container, pod and deployment?
```
container:
container writes specifications related to container in command line.

Pod:
-It defines everything in yaml file.
-In a pod you can create single or multiple container.
-Pod is somewhere similiar to container which is just providing specifications in yaml file.
-It does not have autoscaling and autohealing capabilities.

Deployment:
Deployment provide auto-healing and auto-scaling capabilities.

```

Kubernetes suggests that do not ctrate pod directly create pod in deployment.
```
-Deployment is again a yaml file.
-In deployment you can say that how many number of replicas of your pod you required.
-Replica set is a controller.It ia an intermediate resource.Replica set will roll-out your pod.
Deployment --> Replica Set --> Pods
```
Example of auto healing nature of K8s:
```
-Mention how many replica you want in deploymnet.yaml file.
-If you say 2 replica and you deletes 1 accidently then don't worry kubernetes will again automatically create that pod
using deployment.yaml file bcz you have submitted yaml file with the requirement of 2 replicas.This is Auto Healing nature of
kubernetes.
```
What is the role of replica set?
```
When you create deployment.yaml file and run it then this deployment create a replica set. And replica set will create pods.
Replica set always ensures that there are same numbers of replicas of your pods which you have mentioned in yaml file.If user
delete any pod then RS will create automatically. Replica set is the kubernetes controller which ensures that desired state is
always present.
```

Interview Questions
```
What is the difference between container, pod and deployment?
container:
container writes specifications related to container in command line.

Pod:
-It defines everything in yaml file.
-In a pod you can create single or multiple container.
-Pod is somewhere similiar to container which is just providing specifications in yaml file.
-It does not have autoscaling and autohealing capabilities.

Deployment:
Deployment provide auto-healing and auto-scaling capabilities.


What is zero time deployment in kubernetes?
Parallel deletion and creation of pod is called zero time deployment. RS create new pod before getting killed of old pod.
```

Deployment commands:
```
$ kubectl get all -A //will give all namespaces, all applications in your cluster.

$ minikube ssh //it will login to your minikube cluster.

$ curl 172.17.0.3 //your ruuing application will be seen. After deleting pod if you curl then you won't be able to

see your application.

Now write a deployment.yml file.

$ kubectl get deploy

$ kubectl get rs

$ kubectl get pod

$ kubectl delete pod <pod-name>

before enter open new terminal and type:

$ kubectl get pod -w // you now watch pod and what is happening with pod.

Now increase replica set to 3 and save.

$kubectl apply -f deployment.yaml //to save changes to deployment

```

Additionally you can search for k8s deployment ecample on github.
