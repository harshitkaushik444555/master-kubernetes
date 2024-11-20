What is Kubernetes?
```
Kubernetes is a container orchestration(automating many tasks together) platform.It automates tasks like deploying, managing,
and scaling containerized applications.
```

What are the problems with container?

Containers are ephemeral in nature it means they have short life and can die and revive anytime.

Problem 1: Single Host nature of docker container
```
Nature of docker is scoped to one single host. One container impact other containers. One container can exhaust all
the resoures while other don't have any any resource.Docker itself cannot natively run containers across multiple
hosts in a coordinated way. It is designed to run containers on a single host.
```
Problem 2: No auto-healing is available in container
```
Auto-healing is a behaviour where without human intervention container should start by itself after getting killed.But
it does not happen in container. After getting killed container will not be accessible.
```

Problem 3: No auto scaling in docker container
```
Auto scaling is a behaviour which says that as soon as load increases on one container then number of containers should
increase to balance the load.
```

Problem 4: No enterprise level support in docker container
```
Docker container is very minimalistic or simple. It means it does not have:
-Load Balancer
-Firewall
-Auto scale
-Auto Heal
-API Gateways
-Whitelisting
-Blacklisting
These are enterprise level standard suppot.
```

Who solve these problems?
```
Kubernetes solve all these 4 problems of containers i.e. single host, auto scaling, auto healing, enterprise-level support.
Thses 4 problems are also the difference between docker and kubernetes.
```

How kubernetes solves Single-Host nature  problem?
```
Kubernetes is a cluster it means it has group of nodes. Kubernetes is installed in master and worker node architecture in
production environment.
Example:
If there are two node N1 and N2. N1 is running container c1 and c2 and N2 is empty. If container c1 in N1 affect the
c2 container then Kubernetes cluster like architecture will move c2 into N2 node and now c2 will not be affected by the c1. 
```
