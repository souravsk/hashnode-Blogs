## What are Containers?


# Containers
Containers are packages of software that contain all of the necessary elements to run in any environment. In this way, containers virtualize the operating system and run anywhere, from a private data center to the public cloud or even on a developer’s personal laptop. 

The advantage of these combiners.
- containers help Package all the dependencies within the container and isolate them.
- it is easy to manage the containers.
- The ability to move from one system to another.
- Containers help package the software and can easily ship it without any duplication effort.
- Containers an easily scalable.

Using a container you can scale independently container and use a load balancer or a service that helps Split the traffic and you can scale the applications horizontally container offers a lot of flexibility and ease.

## Why do we need a container?
Now let’s change the scenario upside down or the way it works in IT infrastructure, Which is moving the DEVELOPMENT website/application to UAT and PRODUCTION.

I have to do the same steps all over again in each environment, Including the Server provisioning steps like creating the Virtual machine, and installing the software.

I could make some mistakes while choosing the version of the software like installing the latest version of PHP when my site is far behind (or) do any manual errors in the way I configure (or) setup as I do every step manually from an environment to environment.

Therefore,  there is no guarantee that I would reach to my expected outcome which is having the fully functioning, same application setup across all the environments like DEV/UAT/PROD.

I may be able to achieve the expected outcome after so much manual effort and hiccups.

If you are working as a System Admin/Developer or tester. You might have heard this word somewhere around.

“It was working fine in my laptop or machine”

<iframe src="https://giphy.com/embed/zrdUjl6N99nLq" width="480" height="380" frameBorder="0" class="giphy-embed" allowFullScreen></iframe><p><a href="https://giphy.com/gifs/computer-angry-panda-zrdUjl6N99nLq">via GIPHY</a></p>

Henceforth, No one can say “It was working fine on my laptop.” Cause the setup they have in the LAPTOP/DEV, and the setup they are going to have in PROD will be precisely the same. Containers and container management systems make this happen.

Yes. It might have worked in the laptop (or) DEV, but that’s not enough for it to work in PROD or at least not the same way it’s working in DEV.

## What is inside a Container
As we said just before,  A Container is a Collection of the following elements

- Program Binaries/configuration
- Runtime libraries
- Dependency Products/tools
- A Piece of Kernal
- System Resources
- Hard Disk
- Memory
- I/O
- Network
- CPU

As we are isolating the program and dedicatedly providing its own system resources and runtime libraries. It can run alone as a Standalone application (or) infrastructure
This helps us achieve the Production level.

## Containers and Virtual Machines
Containers and virtual machines have similar resource isolation and allocation benefits but function differently because containers virtualize the operating system instead of the hardware. Containers are more portable and efficient.

![git (4).png](https://cdn.hashnode.com/res/hashnode/image/upload/v1660815597814/tYxaxuaUw.png align="left")

> Hypervisor: Hypervisor is used to create multiple machines on a host  OS and it manages virtual machines

As you can see in the virtual machines we have to install a new os every time whenever we need them to run an application init but in the case of containers we just have to install one os and we use any container manager to create as many as an application we want.

### Containers
Containers are an abstraction at the app layer that packages code and dependencies together. Multiple containers can run on the same machine and share the OS kernel with other containers, each running as isolated processes in user space. Containers take up less space than VMs (container images are typically tens of MBs in size), can handle more applications, and require fewer VMs and Operating systems.

### Virtual machines (VMs) 
Virtual machines (VMs) are an abstraction of physical hardware turning one server into many servers. The hypervisor allows multiple VMs to run on a single machine. Each VM includes a full copy of an operating system, the application, necessary binaries, and libraries – taking up tens of GBs. VMs can also be slow to boot.

## Conclusion
So we learn about the container and its benefit. Container/Containerization is not a new technology (or) approach introduced by docker. It was actually available in the market ever since 2008.
Docker is a container management system that helps us to efficiently manage Linux Containers (LXC) in a more comfortable and universal fashion.

MY next Blog is on Docker so stay tuned it will be available on 21/08/2022 on that blog we will use docker as our container manager to create a container.

