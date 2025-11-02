# kubernetes-guide
kubernetes in detail
Kubernetes : -

** Kubernetes is Container Orchestration system
----------------------------------------------------------------
→ Using docker you could of Course create Containers on any Computer but  if you want to create multiple Containers on different Computers on different servers you Could get into the troubles.

* Kubernetes allows you to create Containers on different servers either physical or Virtual and all of that is done automatically without your intervention.

* You just tell kubernetes how many Containers you would like to create based on Specific image. 

** Kubernetes takes care of  :-
-----------------------------------------------------------------------

1. Automatic deployment of the Containerized. applications across different servers and those servers could be either bare metal on physical servers (or) Virtual, but nowadays no one is using bare metal.

*Virtual servers option is  more commonly used that could be located in different parts of the world.

2. Distribution of the load across multiple servers.
* This allows you to Use your resources efficiently and avoid underutilization (or) overutilization of resources.

3. Auto-scaling of deployed applications
→ In case you need to increase for example quantity of containers which have to be Created on different servers and all of that done automatically. you just tell when you want to scale up (or) down.


4. Monitoring and hatth checks of the containers.

5. In case some Containers fail for Some reasons kubernetes Could automatically replace failed Containers.
*Kubernetes deploys Containerized applications and therefore it has to use Specific Container runtime.

*Docker is just one of the possible options. Kubernetes nowadays supports such Container Runtime are Docker container runtime, CRI-O container runtime and Container D container runtime.

* Container runtime as Docker (or) CRI0 must be running on each of the servers which are included in Kubernetes cluster. And main outcome here is that Kubernetes Could be utilised without docker at all.

* it Supports other Container runtimes like CRIO
and Container D.
