# Virtualization

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

## Challenge
In this section you will have to create a complete virtual environment to run each microservice in different VMs. This should be done using a tool called Vagrant or any other tool to create VMs in a declarative way. Vagrant is a command-line utility for building and managing virtual environments. It creates, starts up, provisions, and destroys VMs easily. Each VM should be provision to execute the microservice you want to run in it. The provisioning should be done via scripting or tools like Ansible, Puppet, among others. You should use Git to track the changes on the infrastructure. While doing this challenge, try to answer these questions:
* What are the advantages of using a declarative tool to create the virtual environment?
* Are you scripts handling idempotence?
* Can you automate the process of provision and running each microservice? For example, that after the *vagrant up* command finishes all the application is running.

[Here](https://www.youtube.com/watch?v=sr9pUpSAexE) you can find a video tutorial that explains the basics of Vagrant. Also, the [getting started](https://learn.hashicorp.com/collections/vagrant/getting-started) documentation may help you.