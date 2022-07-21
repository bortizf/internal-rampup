# Networking and Operating System
As a Devops Engineer you need to know how data communication works at a high level. This will help you to debug network-related issues, such as connectivity between them, services, and more. Plus, you will build the foundation (along with Virtualization) of your understanding of Cloud Computing.  
On the other hand, you will frequently be in front of a terminal with Bash or Powershell, or in your Cloud's terminal. You will hear about standard input or output (I/O). You will also need to have a control of the processes running on your systems, and will eventually work with some form of virtualization. That is why we believe it is important for you to know the basic concepts of an operating system, what parts it is made up of, and how they are related.

## Networking
Networking structure is so complex that it is divided into multiple layers. Each layer has specific responsabilities and relies on lower layers to provide services. The definition of the layers is described by TCP/IP and OSI model. In this summary, we will try to keep things as simple as possible, so we will not go into details. If want to know more about network layers visit this website - [What is the OSI Model?](https://www.cloudflare.com/learning/ddos/glossary/open-systems-interconnection-model-osi/)

We are going to focus on practical tasks and concepts, so we will leave you lectures about topics you may need to know

* [What is a network?](https://www.cloudflare.com/learning/network-layer/what-is-the-network-layer/)
* [What is IP?](https://www.cloudflare.com/learning/dns/glossary/what-is-my-ip-address/)
* [What is a subnet?](https://www.cloudflare.com/learning/network-layer/what-is-a-subnet/)
* [What is TCP?](https://www.geeksforgeeks.org/what-is-transmission-control-protocol-tcp/)

Our work is mostly on layer 4 and 7 of OSI Model, so we will discuss concepts and protocols related to them.  
In order to allow and differentiate multiple connections open by proccesses the computer uses a port number. A port number is a virtual point where network connections start and end, they are software-based. Here is a list with popular ports and protocols:
* HTTP (Port 80): Hypertext Transfer Protocol. It allows the exchange of information on World Wide Web (WWW) using a client-server model. [Here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview) you can find more information about it.
* HTTPS (Port 443): HTTP Secure. It's the secure and encrypted version of HTTP. It uses an encryption protocol called Transport Layer Security (TLS). [Here](https://www.ssl.com/faqs/what-is-https/) you can find more information about it.
* SSH (Port 22): is a method for secure remote login from one computer to another. Also, it allows file transfers and issues remote commands. To learn more, visit [here](https://www.ssh.com/academy/ssh/protocol)
* FTP (Port 20 and 21): File Transfer Protocol. File transfers between client and server. Its communication is unencrypted. In [this video](https://www.youtube.com/watch?v=tOj8MSEIbfA) you can find information about it, and the encrypted version of it.
* DNS (Port 53): Essential procotol for the modern internet. It matches a domain name to an IP address so that we don't have to type the IP address everytime we need to consume a service on Internet. We will cover this in more detail later.
* SMTP (Port 25): Simple Mail Transfer Protocol. It's the industry standard protocol for email sending. It's an email delivery protocol, not email retrieval protocol. For email retrieval exists IMAP or POP3 protocols. [Here](https://www.cloudflare.com/learning/email-security/what-is-smtp/) is more information about it.
<p align="center">
<img style="width:300px; height:150px" src=imgs/SMTP-IMAP-1.png >
</p>

* DHCP (Port 67): Dynamic Host Configuration Protocol. It assigns IP addresses and other communication parameters (DNS Server, Gateway, Network Mask) to devices connected to the network. It uses a client-server model.

### Domain Name Server 
We access services on internet through domain names (www.google.com or www.perficient.com), however computers do not understand those names, but they do understand IP adressess. Therefore, there must be a translation mechanism between domains and IPs. This is the role of DNS. For example, DNS translates perficient.com into 130.250.210.219 IP so that the browser can make the request to the appropriate server. In [this video](https://www.youtube.com/watch?v=dl-C6cBoRg4) you can learn more about how DNS works.  

In addition to the IP, a DNS Server can provide other information such as an email server or an alias to a domain. This is accomplished via DNS Records. We will mention some of them:
* A record - holds the IP address associated with a domain. A request with an A record for google.com returns 142.250.78.78.
* CNAME record - returns a domain alias associated for another domain. A request with a CNAME record for google.com returns ns1.google.com.
* MX record - returns a mail server to redirects emails. a request with a MX record for google.com returns smtp.google.com.
* NS record - returns the authoritative DNS server for a domain.

If you want to play with DNS records and practice the concepts, this [interactive website](https://messwithdns.net/) will help you. 


## Operating System
An operating system acts as an intermediary between high-level programs (Firefox, Terminal, Spreadsheets, and so on) and your computer's hardware. It decides what process runs next, what part of the main memory allocates to a process, and what devices are compatible with the system.  
Processes are crucial because are the ones which tell to the computer what operations to perform. A *process* is a program running in main memory (RAM). The set of processes running on a system make up the *user space* - parts of the RAM that user processes can access. For example, a web server runs in the user space.  These processes are managed by the kernel. The kernel is the core of the operating system. It's the one which tells to the CPU where to look for its next task. The memory area that only the kernel can access is called *kernel space*. The kernel mainly has 4 functions:
* Process management: defines when a process is started, paused, resumed, scheduled, and terminated. They have more than two states (starting and terminating) because in practice a process uses the CPU for a small period of time (*time slice*), then it pauses and another process can start using the CPU, and so on. The act of pausing one process and starting (or resuming) another one is called a *context switch*. The kernel is responsible for context switching. This gives us the ilusion that multiple processes are running at the same time (*multitasking*)
* Memory management: modern CPUs include a memory management unit (MMU) that let us use a memory access scheme called *virtual memory*. In this scheme, a process does not directly access the physical memory location. The kernel sets up each process to act as if it had an entire machine to itself. The virtual addresses are mapped to translate to the physical ones. The kernel has to mantain and alter this memory address map.
* Device management: the kernel manages all hardware devices so that user processes can interact with them. A device a driver is a software that describes how to use and control a particular device. Those drivers are located in the kernel.
* System calls: in order to interact with the kernel, user processes have to use special functions called *system calls*. For example, through them processes can open (*open()*), read (*read()*), and write (*write()*) files. Processes are created through *fork()* and *exec()* system calls.

<p align="center">
<img src=imgs/fork-exec-exit-wait.png >
</p>