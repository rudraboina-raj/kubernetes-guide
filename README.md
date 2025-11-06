# kubernetes-guide
kubernetes in detail
Kubernetes : -

** Kubernetes is Container Orchestration system
----------------------------------------------------------------
* Using docker you could of Course create Containers on any Computer but  if you want to create multiple Containers on different Computers on different servers you Could get into the troubles.

* Kubernetes allows you to create Containers on different servers either physical or Virtual and all of that is done automatically without your intervention.

* You just tell kubernetes how many Containers you would like to create based on Specific image. 

**  Kubernetes takes care of  :-
-----------------------------------------------------------------------

1. Automatic deployment of the Containerized. applications across different servers and those servers could be either bare metal on physical servers (or) Virtual, but nowadays no one is using bare metal.

* Virtual servers option is  more commonly used that could be located in different parts of the world.

2. Distribution of the load across multiple servers.
* This allows you to Use your resources efficiently and avoid underutilization (or) overutilization of resources.

3. Auto-scaling of deployed applications
* In case you need to increase for example quantity of containers which have to be Created on different servers and all of that done automatically. you just tell when you want to scale up (or) down.


4. Monitoring and hatth checks of the containers.

5. In case some Containers fail for Some reasons kubernetes Could automatically replace failed Containers.
* Kubernetes deploys Containerized applications and therefore it has to use Specific Container runtime.

* Docker is just one of the possible options. Kubernetes nowadays supports such Container Runtime are Docker container runtime, CRI-O container runtime and Container D container runtime.

* Container runtime as Docker (or) CRI0 must be running on each of the servers which are included in Kubernetes cluster. And main outcome here is that Kubernetes Could be utilised without docker at all.

* it Supports other Container runtimes like CRIO
and Container D.

1.pod:
--------------------------------------------------------------------------
pod is the smallest unit in the Kubernetes world.

*  In Docker Container is the smallest unit.

* In Kubernetes pod is Smallest possible unit and Containers are created inside of pod. So pod anatomy is following. Inside of the pod there Could be Containers either one even Several Containers Also there are shared volumes and shared network resources for example shared IP address. This means that all Containers are inside the same pod share volume and Share ip address.

* Multiple Containers inside of the same pod. Most Common Scenario is to have just a single Container per pod,But sometimes when Containers have to be tightened together and they heavily depend on each other and they could exist in the Same namespace and it is possible Create Several Container in the Same pod.

* But one Container per pod is most Common Use Case.

* Also keep in mind that each pod must be located on Same Sever

2.Kubernetes Cluster : 
------------------------------------------------------------------------------
Kubernetes cluster consists of nodes,  Node is actually server either bare metal on virtual Server. And you could include multiple such servers into Kubernetes Cluster and they could be located in different data Centas in different parts of the world. But Usually nodes which belongs to the same kubernetes cluster are located close to each other in order to perform all jobs more efficiently.

* In the side of the node there are pods. The pod is again the Smallest possible unit in Kubernetes,And inside of each pod there are Containers, usually Single Container per pod. And such pods are Created on different nodes and all of that is done automatically for you.

* Kubernetes does this job, but of course your job is to create such nodes and create Cluster based on those nodes. Nodes will automatically form a cluster without your intervention.

* But after such initial Configuration everything will be automated and Kubernetes will automatically deploy on different nodes. 

Q.  how do those deploy pods nodes actually Communicate with each other and how they are managed?
-------------------------------------------------------------------------------------
* In Kubernetes cluster there is Master node and Other nodes in the cluster are called worker nodes and the master node actually manages worker nodes.

* Master node's job is to distribute for example load across other worker nodes and all pods which are related to your application are deployed on worker nodes.

* Master node run only system pods which are responsible for actual work of Kubernetes cluster in general.

* We Could also say that master node in the Kubernetes cluster is actually Control plane and it does not run your client applications.

Q. So which services actually run on different nodes?
-------------------------------------------------------------------------------------------
*  There are such Services as kubelet, kube-proxy and Container runtime And those Services are present on each node in kubernetes Cluster.

*  You already know what a Container runtime is. Container runtime runs actual Containers inside of each node. And these are such Container runtimes as docker, crio and Container D.

* There are also such containers Services as Kubelet and such Services on each worker node Communicates with API Server Sevice on master node. Api Server Service is the main point of communication between different nodes in Kubernetes world.

*  Kube- proxy which is present on each node as well is responsible for network communication inside of each node and between nodes. Also there are other services which are present on master node and they are Scheduler and such Service is responsible for planning and distribution of load between the different nodes in cluster.

* Also there is Kube-Controller manager and it is a single point which Controls everything actually in Kubernetes cluster and it Control actually what happens on each of node in cluster.

* Also there is Cloud Controller manager and its job is interaction with Cloud Service provider where you actually run your Kubernetes clusters. Because usually you don't create such a cluster yourself using  your own Services. Instead you could very easily run kubernetes cluster from one of the cloud providers which actually perform almost automated creation of all nodes and the Connections between such nodes and for that you have to run cloud Controller, it manages service on the master node.

* Also for example if you want to create deployment of your application inside of the Kubernetes cluster which will be opened to Outside world and allow Connections from outside you Could create a load balancer ip address and those load balancers Ip address are usually provided by specific cloud providers.

* Also on the master node there is such service as Etcd and this is a Service which actually stores all logs related to operation of entire Kubernetes cluster and such logs are stored there as key value pairs. 

* Also there are other services which are running on the master node for example a DNS Service which is responsible for names resolution in entire Kubernetes Cluster and for instance Using DNS service you could connect to Specific deployment by the name of the Corresponding deployment Service and in such way you could Connect different deployments with each other.

* There are different services which are running on different nodes in Kubernetes cluster.

*  Main service on Master node is API Server and by the way using this API Server Service you could actually manage entire kubernetes cluster.

Q. How is it done?
--------------------------------------------------------------------------
* It is done by using kubectl or kube-Control.

* Kube control is Separate Command line tool which allows you to connect specific Kubernetes cluster and manages it remotely and kubectl Could be running even on you local computer.

* Using such a kubectl tool you Could manage the remote Kubernetes cluster and using such tool you actually Connect using REST API to API Sever Service on Master node and such communications happen over HTTPS.

* By the way other nodes in the cluster I mean worker nodes Communicate with the master node in the same fashion. It means that using such kubectl tool you could manage any remote Kubernetes Cluster That's it Kubernetes architecture overview.

RBAC :
---------------------------------------------------------
The 3 high level things that's define RBAC in Kubernetes.

1. Service account /users

2. Roles / Cluster Role

3.  Role binding / Chester Rode binding.

* Kubernetes Says am  not going to manage the  users, I will off load the users management to identity providers.

Ex: White Once you install Something like Play store, firstly it Says login with Google.

* If we create a Role within a Specific namespace Called Role.

* If we create this Role in the Scope of cluster Called Cluster Role.

Kubernetes Custom resources :
-------------------------------------------------------------
Kubernetes allow you to extend the Capabilities to Kubernetes (or) extend the API of Kubernetes.

* Means you can add new API resources to Kubernetes, using this resource you can ask your Customers to create or you can extend the Kubernetes by deploying a few resources.

To extend
1. CRD
2. CR
3. Custom Controller

1.Custom Role Definition:

Defining a new type of API to Kubernetes by Custom resource definition.
*  crd is a yaml file which is used to introduce a new type of API to Kubernetes.
* User has created a Custom resource (User has Submitted a CR), validated against a crd.

Step-1
*  We have to deploy Custom resource definitions  to extend the Capabilities of Kubernetes cluster.

step-2 
* We have to deploy Custom Controller

Step-3
* user who wants to use this feature on their Kubernetes cluster, like they have 100 namespaces but only 20 namespaces might want to use this Feature so, whoever the namespaces that they use, they will deploy Custom resource.

ConfigMaps and Secrets:-
------------------------------------------------------------------------------
1. ConfigMaps:

ConfigMaps is used to store data and this data can be at later point of time used by your application (or) pod (or) deployment

2. Secrets:

Secrets in Kubernetes solve the same problem, but Secrets deal with Sensitive data, like DB password, DB Username

* In Kubernetes whenever you create a Resource what happens is this information gets Saved in Etcd. In Etcd the data is saved as objects.

* if any hacker tries to get access to Etcd they can retrieve the information, So if they are retrieving the information of your DB user and DB password that means your entire application (or) entire platform is compromised. get the details of database, that leads kubernetes doesn't have a proper Security.* To solve this Kubernetes says,

→ if you have non-sensitive data store it in Config Maps

→ Sensitive data store it in Secrets. In Secrets, it encrypt the data at the rest, that means to Say before the object is saved in Etcd, Kubernetes will encrypt it.

* By default Kubernetes used a basic encryption but what Kubernetes says we will also allow you to use your own encryption (or) Custom encryption Mechanism so, you can pass to your values to API Server whenever you are storing on Apps server is feeding Some formation to etcd you can use custom encryption, Even if the hacker is trying to access etcd because he does not know the decryption key.

* Hello can read all information from etcd, lets say he read the information about ConfigMap (or) pod (or) deployment but when it comes to secrets he is unable to read or retire a decrypted information.






