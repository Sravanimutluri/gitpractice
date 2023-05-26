# What is KUBERNETES?
* Kubernetes is a container management system developed in the google platform. The purpose of K8S is to manage a containerized application in various types of physical, virtual and cloud environments google K8S is a higly flexible container tool to deliver even complex applications.
* Kubernetes is an open source system to deploy, scale, and manage containerized applications anywhere.

* Autoscaling
* Containers don’t scale on their own.
* Scaling is of two types
    1. Vertical Scaling
        * Increase the size of the container
    2. Horizontal Scaling
        * Increase the no. of containers
# TERMS

1. Distributed System
    * Master node will be distribute the work to worker nodes this system is called distributed system.
2. Node
    * Each of the server (VM) is called node.
3. Cluster
    * The combination of master node and worker node is called cluster.
4. State
    * State is a meaning full information of the application in the server.
5. Stateful Applications
    * data stored in somewhere in the local system 
6. Stateless Applications
    * data attached to a application in a external system
7. Monolith
    * Running whole application as it in huge server or running in one server.
8. Microservices
    * It is used to one whole application divided into small apps.
9. Desired State
    * The desired state is the state in which you want your application to be running.
10. Declarative vs Imperative
    * Declarative: What we have and trying to get what we want write in yaml file
    * Imperative: run the yaml file by using command lines interface (CLI)
    ![preview](./k8s1.png)
11. Pet Vs Cattle
    * Pet: It is static infrastructure. If one pod is failed then we repaired and use here.
    * Cattle: It is elastic infrastructure. If one pod is failed then we left and replace with new pod.

# Why you need Kubernetes and what it can do
![preview](./k8s2.png)
* In above visuals, we can see how organizations ran applications on physical servers. Later virtualization allowed better utilization of resources in a physical server and allowed better scalability because an application can be added or updated easily, reduces hardware costs, and much more. In container deployment, containers are similar to VMs, but they have relaxed isolation properties to share the Operating System (OS) among the applications.

* Containers are a good way to bundle and run your applications. In a production environment, you need to manage the containers that run the applications and ensure that there is no downtime. For example, if a container goes down, another container needs to start. Wouldn’t it be easier if this behavior was handled by a system?

* Kubernetes provides you with a framework to run distributed systems resiliently. It takes care of scaling and failover for your application, provides deployment patterns, and more.
* Kubernetes provides you with the following 
    * Service discovery and load balancing
    * Storage orchestration
    * Automated rollouts and rollbacks
    * Automatic bin packing
    * Self-Healing
    * Secret and configuration management