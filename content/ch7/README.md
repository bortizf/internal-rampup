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