Why we need service?
```
You can not say to millions of users that some should access this IP and some should access that IP. So service solve this 
problem by load balancing.If pod gets killed and new pod comes then new pod will have new ip. Service acts as a load balancer.

Like there is an application 'payment'.
Instead of accessing payment using IPs, use a service name payment.default.svc.

Note: every pod has different ip in deployment.
```
What is service discovery mechanism of k8s?
```
A problem is here that service is just taking requests from users and forwarding them to the ips. But when new pod comes with new ip
then service itself faces same problem of not knowing new IP. So to solve this problem svc uses 'labels and selectors' instead of IPs.
svc  says that i won't be bother about the ips I will only watch for Labels which will be common to every pod.Because a pod can go down
100s time but when it comes up it will have same label due to replica set. Label is mentioned in yaml file.This is service discovery
mechanism of k8s.

So service provide load balancing capabilities while keeping track of newly created pod using service discovery mechanism.
```
![image](https://github.com/user-attachments/assets/8c66be08-c89f-4725-a587-483b4af815b8)


Advantages of service
```
Load balancing
Service discovery
Expose to world
```
What is NodePort type service?
```
NodePort is a type of service that exposes your application on a specific port of every node (server) in the cluster. This allows
external traffic to reach your application by accessing any node's IP address and the specified port.

How NodePort Works:
Cluster-Wide Exposure:
Kubernetes assigns a port (the NodePort) from a predefined range (30000–32767 by default) on every node in the cluster.

Routing Traffic:
Traffic sent to any node’s IP address on the assigned NodePort is forwarded to the corresponding service, which routes it to the
appropriate pod(s).

Service Hierarchy:
A NodePort Service is built on top of a ClusterIP Service, so it routes traffic internally within the cluster as well.
You can still access the service internally using its ClusterIP.
```
