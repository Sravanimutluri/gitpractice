## 1.What is docker?
* Docker (dock worker) is used to create containers which is standard way of packaging any application.
* Docker is a containerized technology it is used to build, run deploy and test.
* Docker is a containerized platform which packages with all its dependancies together in the form of container.
## 2.What is docker image?
* If the application can be developed in any sever by the  standard way of packaging.
(or)
* A docker image is a read only template that contains a set of instruction for creating a container that can run on the docker platform.
(or)
* Docker image is the source of Docker container. In other words, Docker images are used to create containers. When a user runs a Docker image, an instance of a container is created. These docker images can be deployed to any Docker environment.
## 3.What is Hypervisor?
* A Hypervisor is a software to create virtual machines. It divides the host system and allocates the resources to each divided virtual environment. You can basically have multiple OS on a single host system. There are two types of Hypervisors:
    * Type 1: It’s also called Native Hypervisor or Bare metal Hypervisor. It runs directly on the underlying host system. It has direct access to your host’s system hardware and hence does not require a base server operating system.
    * Type 2: This kind of hypervisor makes use of the underlying host operating system. It’s also called Hosted Hypervisor.
## 4.What is Docker Hub?
* Docker images create docker containers. There has to be a registry where these docker images live. This registry is Docker Hub. Users can pick up images from Docker Hub and use them to create customized images and containers. Currently, the Docker Hub is the world’s largest public repository of image containers.
## 5.What is a Dockerfile?
* Docker file is a simple text file that consist of instructions to build a docker image.
(or)
* Docker can build images automatically by reading the instructions from a file called Dockerfile. A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image. Using docker build, users can create an automated build that executes several command-line instructions in succession.
## 6.What is Namespace?
* Isolation's on the Linux machines are created using a Linux kernel feature called Namespaces.
    ### PID namespaces (process namespaces)
	    * It creates the isolated process tree inside the container.
    ### NET namespaces (NETWORK namespaces)
	    * It creates the isolated network for each container form network interfaces.
    ### MOUNT namespaces
	    * It allows each container to have their own file system view which starts from root.
    ### USER namespaces
	    * It allows to create whole new set of user and groups for the container.
## 7.What is the lifecycle of a Docker Container?
* Docker containers have the following lifecycle:
    * Create a container
    * Run the container
    * Pause the container(optional)
    * Un-pause the container(optional)
    * Start the container
    * Stop the container
    * Restart the container
    * Kill the container
    * Destroy the container
## 8.How to check for Docker Client and Docker Server version?
* The following command gives you information about Docker Client and Server versions:
* $ docker version
## 9.How do you get the number of containers running, paused and stopped?
* You can use the following command to get detailed information about the docker installed on your system.
* $ docker info
* You can get the number of containers running, paused, stopped, the number of images and a lot more.
## 10.How to login into docker repository?
* You can use the following command to login into hub.docker.com:
* $ docker login
## 11.How do you list all the running containers?
* The following command lists down all the running containers:
* $ docker ps
## 12.How do you access a running container?
* The following command lets us access a running container:
* $ docker exec -it <container id> bash
* The exec command lets you get inside a container and work with it.
## 13.When should I use Dockerfile?
* One should use a Dockerfile when there’s a need to distribute/collaborate on the app’s operating system with a team.
* Use Dockerfile as the version control system for the entire app’s OS.
* use Dockerfile to run the code to the laptop in the same environment as the server you are working on. 
## 14.Is Dockerfile a text file?
* Dockerfile is a text document containing all the commands the user requires to call on the command line to assemble an image. With the help of a Dockerfile, users can create an automated build that executes several command-line instructions in succession. 
## 15.How do I create a simple Dockerfile?
* To create a Dockerfile, set up Docker and Docker Hub. Create the original Docker container and then create a file on it. Make changes to the container, and finally, create a new image. 
## 16.What is Dockerfile language?
* Go language is used to write Docker. A Dockerfile is a text file that contains collections of instructions and commands that will be automatically executed in sequence in the docker environment for building a new docker image. 
## 17.What is Docker compose vs. Dockerfile?
* The key difference between Docker compose, and Docker is that the Docker contents describe how to create and build a Docker image, while Docker compose is a command that runs Docker containers based on settings described in a docker-composed.yaml file. 
## 18.What is a .dockerignore file?
* A .dockerignore file allows you to specify a list of files or directories that Docker is to ignore during the build process. It is similar to a .gitignore file, which is used when you build Git repositories. You can specify the list of files and directories inside the .dockerignore file. 
## 19.How do I commit a docker container?
* First, you need to pull a docker image. Then deploy the container, modify it and commit the changes to the image. When you commit to changes, you essentially create a new image with an additional layer that modifies the base image layer. 
## 20.What is docker context?
* With a docker context, importing and exporting context on different machines with the Docker installed gets easier. One can also use a docker context export command to export an existing context to a file, which can be imported to another machine with the docker client installed. 
## 21.What is the use of Docker in DevOps?
* A Docker container image in DevOps is a lightweight, executable, and standalone package of software that includes everything needed to run an app, runtime, system tools, settings, system libraries, and code. Containers simplify the build/test/deploy pipelines in DevOps.  
## 22.Is Dockerfile COPY recursive?
* COPY and ADD are the two commands that Docker provides for copying files from the host to the Docker image when building it. COPY command copies files recursively, given explicit source and destination directories or files. 
## 23.Is Dockerfile a Docker image?
* A Docker image is built automatically by reading the instructions from a Dockerfile, a text file containing all commands needed to build a given image. A Dockerfile adheres to a specific set of instructions and format, producing a Docker image when you build it. 
## 24.What is SWARM?
* Multi-host networking is created as part of docker orchestration called as SWARM.
## 25.What is overlay network?
* Docker has a network driver called as overlay network.
## 26.What is continuous deployment?
* Continuous deployment is basically when terms rely on fully-automated pipeline. This practice fully eliminates any manual steps and automates the entire process. Threrfore, countinuous deployment ensures that code is countinuously being pushed into production. 
## 27.What is continuous delivery?
* Continuous delivery is an ongoing DevOps practice of building, testing, and delivering improvements to software code and user environments with the help of automated tools.
## 28. What are different ways of building docker images?
* Creating a Docker Image for your Application
* Write a Dockerfile for your application.
* Build the image with docker build command.
* Host your Docker image on a registry.
* Pull and run the image on the target machine.
## 29. What is Dockerfile?
* Docker can build images automatically by reading the instructions from a file called Dockerfile. A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image. Using docker build, users can create an automated build that executes several command-line instructions in succession.
## 30. What is docker deamon?
* Docker deamon which is manage the docker image, container, volume, and network as per client request.
## 31. How is container different than VM?
* Containers are deployed applications bundled with all necessary dependencies and configuration files. All of the elements share the same OS kernel.
* Virtualization is the means of employing software (such as Hypervisor) to create a virtual version of a resource such as a server, data storage, or application.
* Virtualization is an abstract version of a physical machine, while containerization is the abstract version of an application.
## 32. Can you tell something about namespaces and how they are used in Docker?
* Docker uses a technology called namespaces to provide the isolated workspace called the container. Docker uses namespaces of various kinds to provide the isolation that containers need in order to remain portable and refrain from affecting the remainder of the host system.
## 33. What is difference between ADD and COPY Instruction?
* COPY instruction just copies the files from the local host machine to the container file system. ADD instruction potentially could retrieve files from remote URLs and perform operations such as unpacking.
## 34. Can you explain the concept of Layers in Docker Image?
* Docker layers are the fundamental building blocks for creating, deploying, and scaling systems. This technology significantly reduces inefficiencies in software development pertaining to application dependency management, versioning issues, and long-term maintenance efforts.
## 35. What is the purpose of EXPOSE and VOLUME instruction in Dockerfile?
* The EXPOSE instruction informs Docker that the container listens on the specified network ports at runtime.
* The Dockerfile VOLUME instruction creates a volume mount point at a specified container path. A volume will be mounted from your Docker host's filesystem each time a container starts.
## 36. What is your workflow for CI/CD with Docker Containers and where do you store images?
* An integration and test system that builds the docker image and runs a series of tests.
* The Docker Images and other objects are store inside the docker directory in the local machine. They are depending upon the default storage driver used by the machine.
* When we create Docker objects such as images, containers, volumes, etc. all these objects are store inside a directory in our local machine. By default, all the Docker objects are store in the following director.
## 37. What is Compose file?
* The Compose file is a YAML file defining services, networks, volumes, configs and secrets for a Docker application. The latest and recommended version of the Compose file format is defined by the Compose Specification. 
## 38. What are different ways of building docker images?
* Build Docker Image Using Dockerfile
Step 1: Create the required Files and folders.
Step 2: Create a sample HTML file & Config file.
Step 3: Choose a Base Image.
Step 3: Create the Dockerfile.
Step 4: Build your first Docker Image.
Step 5: Test the Docker Image.
## 39. How is container different than VM?
* A container is a software code package containing an application's code, its libraries, and other dependencies. Containerization makes your applications portable so that the same code can run on any device. A Virtual machine is a digital copy of a Physical machine.
## 40. What is difference between ADD and COPY Instruction?
* First, the ADD directive can accept a remote URL for its source argument. The COPY directive, on the other hand, can only accept local files. Note that using ADD to fetch remote files and copying is not typically ideal. This is because the file will increase the overall Docker image size.
## 41. Can you explain the concept of Layers in Docker Image?
* Layers are what make up an image. Each layer is a “diff” that contains the changes made to the image since the last one was added. When building an image, the platform creates a new layer for each instruction in the file. The container starts at the first instruction in the file and executes all instructions in order.
## 42. What is the purpose of EXPOSE and VOLUME instruction in Dockerfile?
* Basis for my last question: If anything, VOLUME and EXPOSE do serve as a sort of documentation. You can easily spot which aspects of the container's environment are relevant to the outside world. I suggest avoiding VOLUME , but the EXPOSE instruction is useful for documentation.
## 43. What is your workflow for CI/CD with Docker Containers and where do you store images?
* CI/CD Tool – An integration and test system that builds the docker image and runs a series of tests. It also pushes the built image to the Kubernetes cluster. Popular examples are Jenkins, Travis, or CircleCI. Kubernetes Cluster – Kubernetes deploy docker containers for the software build verified by the CI/CD tool.
## 44. What is docker engine?
* This is collection of multiple components
    * Orchestration
    * Docker daemon
    * Runtime
## 45. What is runtime?
* It is a low level operating system to create isolated environments in docker engine.
## 46. How many Docker components are there?
* There are three docker components, they are - Docker Client, Docker Host, and Docker Registry.
    ### Docker Client: 
        *This component performs “build” and “run” operations for the purpose of opening communication with the docker host.
    ### Docker Host:
        * This component has the main docker daemon and hosts containers and their associated images. The daemon establishes a connection with the docker registry.
    ### Docker Registry:
        * This component stores the docker images. There can be a public registry or a private one. The most famous public registries are Docker Hub and Docker Cloud.
## 47. What is Docker orchestration?
* Docker orchestration is a set of practices and technologies for managing Docker containers at large scale.
## 48. 