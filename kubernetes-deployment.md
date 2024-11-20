Deployment
```
A deployment is used to maintain a desired state of an application.
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
