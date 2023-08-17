---
title: "Exploring the Heart of Computing: A Deep Dive into Operating System Architecture and Features"
seoTitle: "Operating System Architecture"
datePublished: Thu Aug 17 2023 19:31:37 GMT+0000 (Coordinated Universal Time)
cuid: cllfk533w000508mf2oijcgf7
slug: exploring-the-heart-of-computing-a-deep-dive-into-operating-system-architecture-and-features
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692274955729/60e3ea59-7894-47a2-859e-302a44125e08.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692300656826/a0e0d9af-2686-4eee-84b9-f4c9ae45e153.png
tags: operating-system, devops, os, wemakedevs, operatingsystems

---

Hey Everyone in this blog we are going to know about Operating Systems, Operating System Architecture and Operating system features. We will learn a lot today so let's start the blog.

# What is Operating System?

In the recent advancements in technology, where smart devices ha really change the world. Almost everyone has access to these devices be it mobile phones, tablets, laptops, smart watches or your personal computer and modern vehicles.

What all the above mentioned have in common is, they all use an operating system to enable their functionality for you to achieve a certain task. Despite all this amazing being owned by us, very few of us get to understand how the OS that makes it possible to achieve different tasks is structured.

**Operating System(*OS*) is software that manages computer hardware and software resources and provides common services for computer programs.**

In a simple way, we can say an OS is an interface between the user and the machine that makes it easy for the user to achieve different tasks with ease.

Now you have an understanding of what an OS is and also a slight idea of what it does.

# Operating System Architecture

The [OS](https://www.codingninjas.com/studio/library/introduction-to-operating-system) (Operating System) acts like a mediator between us and the computer hardware, providing us with an interface to execute programs quickly and efficiently.

n essential aspect of an operating system is its architecture, which refers to its different components' design and organization. These components include the CPU, memory management, file systems, device drivers, and user interface. The architecture determines how these components interact with each other and how they provide services to applications and users.

Before diving deep into the Operating System Architecture, let's get familiar with some Operating system terminologies

### Kernel

A kernel is a central component( core ) of the operating system. It plays a critical role in ensuring the stability and security of the system. The Kernel performs tasks like process and memory management, file systems, etc.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692274996082/1c1ea7d3-74e9-4436-83ce-f6ed17b5becb.png align="center")

### Shell

In an [operating system](https://www.codingninjas.com/studio/library/introduction-to-operating-system), a shell is a user interface( it can be a command line interface or graphical user interface ) that allows users to interact with the operating system by entering commands or running scripts. It acts like exposing the system services to the user and provides a more user-friendly interface.

### CPU

A CPU is the primary component of a computer that performs most of the processing and calculations. It is also known as the "brain" of the computer and is responsible for executing instructions of the computer program.

Memory in a computer refers to the hardware components that store data, instructions, and information for the computer to access quickly. There are several types of memory in a computer, including:

* RAM (Random Access Memory): It is the primary memory of a computer and is used to store data and instructions temporarily.
    
* ROM (Read-Only Memory): A non-volatile memory stores essential instructions and data that the computer needs to access during startup.
    
* Cache Memory: It is a type of high-speed memory that stores frequently accessed data and instructions to improve the computer's overall performance.
    
* Virtual Memory\*\*:\*\* It is a memory management technique that uses hard disk space to extend RAM to improve the computer's performance.
    

### **Inter-Process Communication**

The interaction of processes is referred to as interprocess communication. There are several threads in a process. Threads from any process interact with one another in the kernel space. Messages are sent and received via ports across threads. There are several ports at the kernel level, including process port, exceptional port, bootstrap port, and registered port. These ports all interact with user-space processes.

## **Different Types of Operating System Architecture**

Operating systems are the backbone of modern computing devices, from smartphones to servers. However, not all operating systems are created equal, and different architectures of the operating system can significantly impact system performance, flexibility, and security.

Here, we are not going to explore different operating system architectures and discuss each architecture because that will make the whole blog very long. So if you need more deep knowledge please let me. We will only discuss Monolithic Architecture because everyone is mostly familyer with this OS which is developed using Monolithic architecture.

These are the different types of Operating System

1. **Monolithic Architecture**
    
2. **Microkernel Architecture**
    
3. **Hybrid Architecture**
    
4. **Layered Architecture**
    
5. **Virtual Machine Architecture**
    

### Monolithic Architecture

A monolithic operating system architecture includes all system functionalities in a single module, with the kernel and device drivers as key components. In this architecture, the operating system as a whole is working in the kernel space. The kernel directly controls all the file, memory, device, and process management.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692275004011/b5c49bed-1d82-4d6a-aa00-912ac46aba36.png align="center")

#### **Advantages of Monolithic Architecture**

* **Fast:** Monolithic operating systems are fast. Thus, they provide better process scheduling, memory management, file management, etc.
    
* **Direct Interaction between Components:** All the components and the kernel can directly interact. It also helps in gaining a better speed.
    
* **Easy and Simple:** Its structure is easy and simple as all the components are located in the same address space.
    
* **Better for Smaller Tasks:** Monolithic OS works better for handling smaller tasks.
    

#### **Disadvantages of Monolithic Architecture**

* **Prone to Errors:** Monolithic OS can generate errors and bugs in the system. It is because user programs use the same address space as the kernel.
    
* **Difficult to Update:** In a monolithic OS, all the OS code is in a single big chunk; therefore, it is difficult to add or remove features in the OS.
    
* **Not Portable:** The code written in a monolithic OS is difficult to carry with or transfer to another system: this is because all the code works in a big chunk only, and you have to move it all.
    

#### **Examples of Monolithic-Based Operating Systems:**

* Windows
    
* Linux
    
* MacOS
    

# Operating System Features

Speaking of OS features, has it ever crossed your mind how the computer manages to handle different processes, how different tasks are managed or even implemented?

If these questions have ever crossed your mind, then in this section they will be answered, all these are functions that are being handled by the OS, Let's talk more about the same below:

1. **Memory Management**  
    It's the work of the OS to manage the computer's memory. With the help of the CPU the OS keeps track of the memory used by a particular program, It will be fair to mention that the OS ensures that each program is allocated enough memory to execute its process
    
2. **Process Management**  
    The OS is responsible for deciding the order in which processes will be executed, this act is known as process scheduling. Process management is made possible with the help of algorithms. Other responsibilities that lie under this category include: keeping the status of a process and ensuring each process receives enough time to execute.
    
3. **Device Management**  
    It monitors all devices connected to your device, both the input and output devices. It's main function is to ensure that all the connected devices are correctly allocated and functioning. It also decides which process gets access to a certain device and for how long.
    
4. **File Management**  
    As we all know a system does contain multiple and large amounts of data. It's the work of the OS to keep track of all this information including their location, accessibility rights, where they are stored, status of the file. It also manages the process of file deletion.
    
5. **Job Scheduling**  
    The operating system determines the jobs/tasks that need to be processed first and ensures that these tasks are completed. Usually, the one with the highest priority is executed first. It also keeps track of the time and resources used by various tasks and users.
    
6. **Error Detection & Response**  
    When a computer is running we are about to encounter a number of errors, by the computer being able to indicate or show you where this is made possible with the help of the OS. The OS offers help with a response that guides you on what to do next
    

# The End

That's all from my side hope you liked it and learned something from this blog.