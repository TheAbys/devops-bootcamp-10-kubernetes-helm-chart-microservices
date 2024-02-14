# 21 - Demo project: Deploy Microservices Application

We do not have to check the microservices codes. But the developers should provide us with information regarding which services their application is talking to and on what port their application is running.
This way we can configure everything like we did in the config.yaml file.

For redis we configured a empty directory volume which is basically just an in memory storage for the cart.

Some additional configuration information we required we could look up on the services documentation, like that the profiler must be disabled when we do not have a profiler service in our cluster.