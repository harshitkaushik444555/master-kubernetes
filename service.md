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
