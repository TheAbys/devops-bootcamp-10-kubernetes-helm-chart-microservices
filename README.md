# 21 - Demo project: Deploy Microservices Application

We do not have to check the microservices codes. But the developers should provide us with information regarding which services their application is talking to and on what port their application is running.
This way we can configure everything like we did in the config.yaml file.

For redis we configured a empty directory volume which is basically just an in memory storage for the cart.

Some additional configuration information we required we could look up on the services documentation, like that the profiler must be disabled when we do not have a profiler service in our cluster.

# 22 - Production & Security Best Practises

## livenessProbe

Does it while the application is running

Adding livenessProbe to each container gives kubernetes the possibility to check if the application inside the pod is still running and if not trigger a recreation.
It can be a interval query on different protocols and ports like grpc or https.

## readinessProbe

Does it while the application is still in startup

Checks if the application is already available, otherwise it would lead to possible errors if other services try to communicate with it.

It is also possible to set an initial delay when the application should be first probed.

## resources

For a container resources requests and limits should be set. 
Without this configuration it is possible that a container starves other containers.

Setting requests means basically the default requests required under normal load.
Setting limits means the container can't go beyond that and therefore not starve anyone.

The unit cpu: 100m or memory: 64Mi is millicore and Mebibyte.
1 CPU Core equals 1000m, this means this container with 100m takes just 10% of the CPU load. This topic is really complex, has something to do with the kernel and how it manages CPU time etc.

## NodePort is bad practise

Convert the service to a LoadBalancer service.

## Replicas

It is better to always have at least two replicas.

## Namespaces

Use namespaces to create privileges on them etc.

## Security Best Practises

Check images for vunerabilities

## No root access for containers

Container with root access can access host system

## Kubernetes version

Keep kubernetes up-to-date

Update node by node to not have a downtime