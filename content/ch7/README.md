# Virtualization and Containerization

In this section we will see what is virtualization, what are its advantages, what's a hypervisor, and what are the types of virtualization. This topic is the basis to what we know today as Cloud Computing. 

## What's virtualization?

Virtualization is a process that allows for more efficent utilization of physical computer hardware. One common use case of this are virtual machines (VMs). A virtual machine is a virtual computer that is running on top of a physical hardware. Each VM behaves like an independent computer (with its own devices, CPU or RAM), even they are sharing the same physical resources. 


## Benefits of virtualization

- **Resource efficiency**: before virtualization, each application server required its own dedicated physical CPU, RAM, and devices. Virtualization lets you run several applications on a single physical computer.
- **Easier management**: the sofware-defined VMs can be control via a central place. Also you can define templates for VMs, so that you can install services repeatedly and consistently. 
- **Minimal downtime**: if something goes down, admins can run multiple redundant VMs and failover between them. Doing this with physical servers is more expensive.
- **Faster provisioning**: buying, installing, and configuring hardware for each application is time-consuming. Provisioning virtual machines to run all your applications is significantly faster.

## What are hypervisors?
A hypervisor is a software that separates the physical resources from the virtual environments. There are two types of hypervisors:
* **Type 1 hypervisors** interact with the underlying physical resources, replacing the traditional operating system altogether. They most commonly appear in virtual server scenarios. For example, KVM, XEN or Hyper V.
* **Type 2 hypervisors** run as an application on an existing OS. For example, VirtualBox or VMWare Workstation.

## Types of virtualization
There are many type of virtualization, we will discuss the most common ones: 
* **Desktop virtualization** lets you run multiple desktop operating systems, each in its own VM on the same computer. There are two types of desktop virtualization: *Virtual desktop infrastructure (VDI)* and *local desktop virtualization*. 
* **Network virtualization** abstracts hardware elements and functions (e.g., connections, switches, routers, etc.) and abstracts them into software running on a hypervisor. Types of network virtualization includes *software-define networking (SDN)* and *network function virtualization (NFV)*
* **Storage virtualization** enables all the storage devices on the network to be accessed and managed as a single storage device called shared pools.

## Virtualization Challenge
In this section you will have to create a complete virtual environment to run each microservice in different VMs. This should be done using a tool called Vagrant or any other tool to create VMs in a declarative way. Vagrant is a command-line utility for building and managing virtual environments. It creates, starts up, provisions, and destroys VMs easily. Each VM should be provision to execute the microservice you want to run in it. The provisioning should be done via scripting or tools like Ansible, Puppet, among others. You should use Git to track the changes on the infrastructure. While doing this challenge, try to answer these questions:
* What are the advantages of using a declarative tool to create the virtual environment?
* Are you scripts handling idempotence?
* Can you automate the process of provision and running each microservice? For example, that after the *vagrant up* command finishes all the application is running.

[Here](https://www.youtube.com/watch?v=sr9pUpSAexE) you can find a video tutorial that explains the basics of Vagrant. Also, the [getting started](https://learn.hashicorp.com/collections/vagrant/getting-started) documentation may help you.

##  What's containerization?
Containerization is a type of virtualization. In particular, it focus on OS-level virtualization. Containerization is the packaging together of software code with all it’s necessary components like libraries, frameworks, and other dependencies so that they are isolated in their own. Usually, people confuse containers with VMs, however their underlying infrastructure is very different:
![](./imgs/virtualization-vs-containers.png)

Containerization technology shares most of the benefits of VMs, with the difference being scalability. Containers are lightweight virtualization, so creating or destroy them has little overhead.

## Docker
Docker is a set of platform as a service (PaaS) products that use OS-level virtualization to deliver software in packages called containers. Docker has an easy interface to manage Docker containers. Let's discuss some of the main Docker concepts.

### Image
Containers are instances of a particular image. A Docker image is a file that contains the instructions you need for your container. It is a template. Docker images are built from an instructional file named **Dockerfile** that is parsed by Docker runtime. This is an example of a Dockerfile: 
```Docker
FROM <image>:<tag>

RUN <install some dependencies>

CMD <command that is executed on `docker container run`>
```

You can list all the installed images in your host with `docker images ls`

### Container
Containers only contain that which is required to execute an application; and you can start, stop and interact with them. They are isolated environments in the host machine with the ability to interact with each other and the host machine itself via defined methods.

To see all you running containers, type `docker container ls`. You can add the `-a` flag to list the stopped ones too.

## Most used Docker commands

| Command | Explanation | Shortcut |
| ------- | ----------- | ---------|
|docker image ls|	Lists all images|	docker images|
|docker image rm <image>|	Removes an image	| docker rmi |
|docker image pull <image>| Pulls image from a docker registry |	docker pull|
|docker container ls -a| Lists all containers |	docker ps -a |
|docker container run <image>| Runs a container from an image|	docker run |
|docker container rm <container>|	Removes a container|	docker rm|
|docker container stop <container>|	Stops a container|	docker stop|
|docker container exec <container>|	Executes a command inside the container |	docker exec|

## Container challenges

* Run the "Hello, World" Docker container. Make sure you understand the concepts of Container Registry, pulling and pushing an image to a Registry.
* Run a program that you want from a Docker container. It can be a web server, a database or even a programming language. 
* Run a container based on this image *devopsdockeruh/simple-web-service:ubuntu*. The image creates a container that outputs logs into a file. Go inside the container and use `tail -f` command to follow the logs. What's the secret message it outputs?
* Given the following script, create an image from it. 
```bash
#!/bin/sh

echo "Hello, Perficient!"
```
* When you pass the *server* command to the *devopsdockeruh/simple-web-service* image, it will create a container with a web service running on port 8080. Access it from your localhost address. You will get a message like this: "{ message: "You connected to the following path: ..."
* Make sure you understand the **docker-compose** command. How to install it and what do we need it. [Here](https://www.baeldung.com/ops/docker-compose) you can find information about it.
* Create a Dockerfile per each microservice in [our microservice application](https://github.com/bortizf/microservice-app-example). After that, run each microservice separately.
* Finally, create a docker-compose file to run all the microservices at once.