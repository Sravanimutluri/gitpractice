## What is KUBERNETES?
* Kubernetes is a container management system developed in the google platform. The purpose of K8S is to manage a containerized application in various types of physical, virtual and cloud environments google K8S is a higly flexible container tool to deliver even complex applications.
* Kubernetes is an open source system to deploy, scale, and manage containerized applications anywhere.

* Autoscaling
* Containers don’t scale on their own.
* Scaling is of two types
    1. Vertical Scaling
        * Increase the size of the pod.
    2. Horizontal Scaling
        * Increase the no. of pods.
# TERMS

1. Distributed System
    * Master node will be distribute the work to worker nodes this system is called distributed system.
## 2. Node
    * Each of the server (VM) is called node.
## 3. Cluster
    * The combination of master node and worker node is called cluster.
## 4. State
    * State is a meaning full information of the application in the server.
## 5. Stateful Applications
    * data stored in somewhere in the local system 
## 6. Stateless Applications
    * data attached to a application in a external system
## 7. Monolith
    * Running whole application as it in huge server or running in one server.
## 8. Microservices
    * It is used to one whole application divided into small apps.
## 9. Desired State
    * The desired state is the state in which you want your application to be running.
## 10. Declarative vs Imperative
    * Declarative: What we have and trying to get what we want write in yaml file
    * Imperative: run the yaml file by using command lines interface (CLI)
    ![preview](./k8s1.png)
## 11. Pet Vs Cattle
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
    * Automated rollouts and rollbacks (version changes)
    * Automatic bin packing
    * Self-Healing (automatic restart)
    * Secret and configuration management
# Kubernetes Architectural Components
* When you deploy Kubernetes, you get a cluster.
* A Kubernetes cluster consists of a set of worker nods, called compute machines/nodes, that run containerized applications. The node(s) host the Pods that are the components of the application workload.
* The control plane manages the worker nodes and the Pods in the cluster.
![preview](./k8s3.png)
* Cluster ===> Nodes ===> Pods ===> Containers ===> Image
* The cluster is in above order.

# Control plane components
## API Server: 
    * The API server is the front end for the Kubernetes control plane.

## Scheduler: 
    * It is responsible for scheduling pods on specific nodes according to automated workflows and user defined conditions.

## Controller Manager:
    * The controller manager is responsible for several controllers that handle various automated activities at the cluster or pod level, including replication controller, namespace controller, service accounts controller, deployment, statefulset, and daemonset.

## ETCD:
    * Consistent and highly-available key value store used as Kubernetes’ backing store for all cluster data.

## Node components:
    * run on every node, maintaining running pods and providing the Kubernetes runtime environment.

## kubelet: 
    * An agent that runs on each node in the cluster. It makes sure that containers are running in a Pod.

## kube-Proxy:
    * It maintains network rules on nodes. These network rules allow network communication to your Pods from network sessions inside or outside of your cluster.

## Container Runtime:
    * The container runtime is the software that is responsible for running containers.

# What are the benefits of Kubernetes?
* Container orchestration savings
    * Orchestration is the automated configuration, management, and coordination of computer systems, applications, and services.
* Increased DevOps efficiency for microservices architecture
* Deploying workloads in multicloud environments
* More portability with less chance of vendor lock-in
* Automation of deployment and scalability
* App stability and availability in a cloud environment
* Open-source benefits of Kubernetes

# Kubernetes services
* Various vendors offer Kubernetes-based platforms (Managed Kubernetes Platform) or infrastructure as a service (IaaS) that deploy Kubernetes.
* Alibaba Cloud ACK (Alibaba Cloud Container Service for Kubernetes)
* Amazon EKS (Elastic Kubernetes Service)
* DigitalOcean managed Kubernetes Service
* Google GKE (Google Kubernetes Engine)
* IBM Cloud Kubernetes Services
* Microsoft AKS (Azure Kubernetes Services)
* Mirantis K0s
* Oracle Container Engine for Kubernetes
* Red Hat Openshift
* SUSE Rancher, Rancher Kubernetes Engine (RKE)
* VMware Tanzu

# What is k8s manifest
* This is a yaml file which describes the desired state of what you want in/using k8s cluster.

# CI/CD workflow
* step1: write a new code
* step2: build docker image with new tag
* step3: push the image to registry
* step4: deploy this in k8s cluster (environment)
* In which environment we use the pipeline will be changed by their environmently.
## K8s Installations
* Create two are more VM's with size 2vcpu's and 8Gb RAM. The following commands are enter into VM while we creating in advance
---
* #!/bin/sh
* curl -fsSL https://get.docker.com -o get-docker.sh
* sh get-docker.sh
* sudo usermod -aG docker azureuser
* sudo swapoff -a
---
![preview](./k8s4.png)
* After that creating VMs are connected to powershell and select one is the master node and other are worker nodes. then check the docker in it present or not. After that enter into root then follow the commands for installation kubernetes.
---
* wget https://storage.googleapis.com/golang/getgo/installer_linux
* chmod +x ./installer_linux
* ./installer_linux
* source /root/.bash_profile
* git clone https://github.com/Mirantis/cri-dockerd.git
* cd cri-dockerd
* mkdir bin
* go build -o bin/cri-dockerd
* mkdir -p /usr/local/bin
* install -o root -g root -m 0755 bin/cri-dockerd /usr/local/bin/cri-dockerd
* cp -a packaging/systemd/* /etc/systemd/system
* sed -i -e 's,/usr/bin/cri-dockerd,/usr/local/bin/cri-dockerd,' /etc/systemd/system/cri-docker.service
* systemctl daemon-reload
* systemctl enable cri-docker.service
* systemctl enable --now cri-docker.socket
* cd ~
* sudo curl -fsSLo /etc/apt/keyrings/kubernetes-archive-keyring.gpg https://dl.k8s.io/apt/doc/apt-key.gpg
* sudo apt-get update
* sudo apt-get install -y apt-transport-https ca-certificates curl
* echo "deb [signed-by=/etc/apt/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
* sudo apt-get update
* sudo apt-get install -y kubelet kubeadm kubectl
* sudo apt-mark hold kubelet kubeadm kubectl
---
![preview](./k8s5.png)
![preview](./k8s6.png)
![preview](./k8s7.png)
![preview](./k8s8.png)
* The above commands enter into all nodes and after that the following commands enter into only in masternode
---
* kubeadm --help
* kubeadm init --pod-network-cidr "10.244.0.0/16"
* kubeadm init --pod-network-cidr "10.244.0.0/16" --cri-socket "unix:///var/run/cri-dockerd.sock"
* exit
* mkdir -p $HOME/.kube
* sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
* sudo chown $(id -u):$(id -g) $HOME/.kube/config
* kubectl get nodes
* kubectl get nodes -w
---
![preview](./k8s9.png)
![preview](./k8s10.png)
![preview](./k8s11.png)
![preview](./k8s12.png)
* Now do the following commands in worker node to connect to master node
---
* kubeadm join 10.0.0.4:6443 --token chcin4.ra67s6dnd36ffkvn --cri-socket "unix:///var/run/cri-dockerd.sock" --discovery-token-ca-cert-hash sha256:523da7be52acf4951921693c0c454aab4d7031cb423da9273ad1d67b2c92e8a3 
---
* Now check the master node by using following commands
---
* kubectl get nodes
* kubectl get nodes -w
---
# How to Create Resources in K8s
We would be creating k8s manifests i.e yaml files
For this we need to understand
yaml
api versioning
Spec and Status
# K8s Workloads
## pod:
    * 
* Replica set
* Deploymet
* Statefulsets
* Jobs
* Cornjobs