There is master node and worker node in kubernetes. Master node works as control plane and worker node works as data plane.

There are 3 components in worker node of kubernetes- Kubeproxy, kubelet, container runtime. Worker node or data plane is responsible

for running your application. Using 3 components of worker node you have technically everything to run your application.

1.In docker the simplest thing is container

2.In kubernetes the simplest thing is pod.

Pod
```
A Pod is the smallest and simplest unit of deployment in Kubernetes. It serves as a wrapper around one or more containers.
containers are the fundamental building blocks, while pods are the operational units in Kubernetes that manage and group containers.
```

Following are Worker Node components:

Kubelet
```
It is responsible for running the pod. If pod is not running kubelet inform to kubernetes.
The kubelet is an essential component of a Kubernetes cluster. It runs on every node (worker or master) and acts as the
node agent that ensures containers are running as expected according to the cluster's desired state.
How Kubelet Works:
The kubelet listens to the Kubernetes API Server for PodSpecs (pod specifications).
It pulls the required container images, starts the containers, and manages their state using the configured container runtime.
If a pod fails or doesn't meet its health checks, the kubelet attempts to restart it.
```

Kubeproxy
```
It provides networking to the pod.Every pod should be allocated with ip address and it should have load balancing capabilities.
```

Container-runtime
```
To run a container you need container runtime this is called dockershim. We have container runtime because there is container 
inside pod.
```

Following are master node components:

API Server:
```
API server is a component that exposes your kubernetes to external world. API server is heart of kubernetes it takes all the
requests from external world.
API server does the following thing
-Multiple users trying to access kubernetes cluster
-SSO
-Identity related configuration
-Security settings
```

Scheduler:
```

The scheduler in Kubernetes is a core component of the control plane responsible for deciding which node will run a new pod.
It ensures that pods are assigned to nodes based on resource requirements, constraints, and policies, keeping the cluster
balanced and efficient.
```

etcd
```
It is the backup service for kubernetes. etcd is a distributed key-value store used by Kubernetes to store all cluster data.
It is a critical component of the Kubernetes control plane, providing a reliable and consistent datastore for the cluster's state.
```

Controller Manager
```
To do auto scaling there is Replica set controller. Who controls these controllers is controller manager.
```

CCM(cloud controller manager)
```
The Cloud Controller Manager (CCM) in Kubernetes is a component that integrates the cluster with a cloud provider.
It helps Kubernetes interact with cloud-specific resources like load balancers, storage volumes, and networking.
Example:
For new cloud provider like new-cloud, the cloud provider should write a logic and should submit it on CCM.
```



