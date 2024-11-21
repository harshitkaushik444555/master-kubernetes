Why we need service?
```
You can not say to millions of users that some should access this IP and some should access that IP. So service solve this 
problem by load balancing.If pod gets killed and new pod comes then new pod will have new ip. Service acts as a load balancer.

Like there is an application 'payment'.
Instead of accessing payment using IPs, use a service name payment.default.svc.

Note: every pod has different ip in deployment.
```
Service Discovery
```
A problem is here that service is just taking requests from users and forwarding them to the ips. But when new pod comes with new ip
then service itself faces same problem of not knowing new IP. So to solve this problem svc uses 'labels and selectors' instead of IPs.
svc  says that i won't be bother about the ips I will only watch for Labels which will be common to every pod.Because a pod can go down
100s time but when it comes up it will have same label due to replica set. Label is mentioned in yaml file.This is service discovery
mechanism of k8s.

So service provide load balancing capabilities while keeping track of newly created pod using service discovery mechanism.
```

![image](https://github.com/user-attachments/assets/8c66be08-c89f-4725-a587-483b4af815b8)


Expose to the world
```
1. You can not say to your customer to ssh my pod ip to access my application.So a service can expose your application to outside world.
   It means service can allow your application to be accessible from outside the k8s cluster.

2. when you write yaml file then you have option to write a service of three types: Cluster IP, NodePort, Load Balancer.

3. If you choose cluster ip then your application will only be accessible inside the k8s cluster(i.e. ssh to minikube).You get only two
   benefits from this load balancing and  service discovery.If you can login to k8s cluster and has access to container network then
   only you can access application.

4. If you choose NodePort then anyone in your organisation can access the application. whoever has access to the node ips he can access.
   Like if worker node is ec2 then anyone who has access to ec2 ip can access application

5. If you choose load balancer service type, it will expose your application to external world.This will only work on cloud provider not
   on minikube or your machine. If anyone who has access to internet can access application if svc type is Load Balancer
```

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

HANDS ON PRACTICAL OF SERVICE
```
-Label field in template section of deployment should have same name as selector in service.
-container port in deployment.yml should be same as port in docker file.
$ kubectl get deploy
$ kubectl get pods -v 7//to get everything what is happening behind the command.( 9 is maximum)
$minikube ssh
$curl -L http://172.17.0.5:8000/demo //pod ip is given.it is done inside cluster after minikube ssh

-If you are doing above thing it means first you are going inside minikube cluster and accessinf app.
-If you directly use curl you will not access pod bc you are outside the cluster and bc a pod is bydefault attached to
 cluster network.

-If you use NodePort then you expose your application on worker node ip address.
-NodePort can be anything in service.yml file.
-Target port can only be on which your app is running.
-metadata field name can be anything in service.yaml

$vim service.yaml

$ kubectl apply -f service.yaml

$kubectl get svc // here you get port mapping.Yhis means clusterIP:80 port is mapped with Node IPaddress and 3007 port number.

Now to access app you have 2 options:
1. minikube ssh
  curl http://10.101.63.207:80/demo -L // cluster ip is given
2. without doing minikube ssh

$minikube ip //give node ip if it is ec2 instance
$curl -L http://192.168.64.10:3007/demo

-now you can also access it using your browser.Only who has access to node ip can access app.

To edit svc
$kubectl edit svc python-django-sample-app //this is service name

-To access from outside world edit your service from type:NodePort To Load Balancer But it won't work in minikube.

Till now Expose to world demo is done.
Now How service discovery work?

You can also edit your service using service.yaml file but if you do so then you must use kubectl app command.
$kubectl apply -f service.yaml//use this mostly

To see how service discovery works:
-change selector in service.yaml & save (any letter)
-now try to access from browse or cli you won't be able to access
-bcz selector and labels should have same name.
-now change back to correct it will work.

Now test Load Balancing:
-If you create deployment you dont get load balancing but svc provide.

-Install kubeshark to see load balancing
-use kubeshark tap -A//for all namespaces
-access kubeshark in browser localhost:8899

run curl command without -L in cli 6 times to see load balancing.


```
