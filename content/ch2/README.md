# Networking and Operating System
As a Devops Engineer you need to know how data communication works at a high level. This will help you to debug network-related issues, such as connectivity between them, services, and more. Plus, you will build the foundation (along with Virtualization) of your understanding of Cloud Computing.  
On the other hand, you will frequently be in front of a terminal with Bash or Powershell, or in your Cloud's terminal. You will hear about standard input or output (I/O). You will also need to have a control of the processes running on your systems, and will eventually work with some form of virtualization. That is why we believe it is important for you to know the basic concepts of an operating system, what parts it is made up of, and how they are related.

## Networking
Networking structure is so complex that it is divided into multiple layers. Each layer has specific responsabilities and relies on lower layers to provide services. The definition of the layers is described by TCP/IP and OSI model. We will use the TCP/IP Model.
* Application layer: contains high-level protocols that applications and servers use to communicate. For example, Hypertext Transfer Protocol (HTTP) or Transport Layer Security (TLS). 
* Transport layer: includes specifications on how the data will be break into packets, and how these packets will be reassembly. Also, it performs data integrity checking. Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) are the most common protocols in this layer. 
* Internet or network layer: once the packets are ready to be sent, this layer defines how to move those packets from a source to a destination host. The Internet Protocol (IP) is used to perform this task.
* Link layer: defines how to send data across a wired or wireless link. For example, Ethernet or 802.11 (WiFi).
## Operating System