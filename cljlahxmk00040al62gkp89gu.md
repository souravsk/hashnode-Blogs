---
title: "WebAssembly Beyond the Browser"
seoTitle: "The Future of WebAssembly into the cloud and Beyond"
seoDescription: "WebAssembly is a powerful new technology that is poised to revolutionize the cloud.This blog post explores the future of WebAssembly in the cloud and beyond"
datePublished: Sun Jul 02 2023 10:28:52 GMT+0000 (Coordinated Universal Time)
cuid: cljlahxmk00040al62gkp89gu
slug: wasm-in-cloud
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688293145755/bdb5f183-f490-4574-a25a-e4e43310f10a.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1688293434966/8350973e-eb62-4518-a81a-d2509a9dda2d.png
tags: javascript, webassembly, developer, devops, wemakedevs

---

Hey Everyone!! I hope you're all doing well. In my last blog post, we delved into the fascinating world of WebAssembly. We explored its origins, why it was developed, and how it became an essential part of web development. If you haven't had a chance to read that article yet, I highly recommend checking it out first. You can find it here: [Introduction to WebAssembly](https://souravk.hashnode.dev/intro-wasm)

Today, we're going to take things a step further and explore the incredible possibilities of WebAssembly beyond the confines of the browser. While WebAssembly was initially designed for browser-based applications, its adoption as a non-browser runtime has exceeded expectations, opening up a world of exciting opportunities.

<iframe src="https://giphy.com/embed/l3mZfxgPWhmuXa8Cc" width="480" height="480" class="giphy-embed"></iframe>

[via GIPHY](https://giphy.com/gifs/thegoodplace-season-2-nbc-l3mZfxgPWhmuXa8Cc)

# what's beyond the browser

So, I gonna talk about 4 different Domains where I think WebAssembly is going to flourish. I'm going to lean a little bit toward one because I'm particularly passionate about that one but I will cover all four and look like this

First browser of course the place it was born for and it really does have a lot to offer there, then the Internet of things, then Plugins and extensions, and then finally Cloud there I will spend more time explaining because I love it. Let's go

<iframe src="https://giphy.com/embed/JyQNXZ6IovFFhO4biU" width="480" height="270" class="giphy-embed"></iframe>

[via GIPHY](https://giphy.com/gifs/xbox-lego-xbox-series-x-star-wars-the-skywalker-saga-JyQNXZ6IovFFhO4biU)

### Browser

Again I would like to mention that I have already written a blog introducing the WASM and I have mostly talked about the browsers so if you haven't then please visit here. [Introduction to WebAssembly](https://souravk.hashnode.dev/intro-wasm)

Traditionally, web applications were written in JavaScript, which is a dynamic, interpreted language. While JavaScript is powerful, it may not always provide the level of performance needed for certain tasks, such as complex calculations or intensive graphics rendering.

WebAssembly bridges this performance gap by providing a low-level, efficient bytecode format that browsers can execute at near-native speeds. It serves as a compilation target for languages other than JavaScript, enabling developers to leverage the performance benefits of lower-level languages while still integrating seamlessly with existing web technologies.

With WebAssembly, developers can take their existing codebases, written in languages like C or C++, and compile them into WebAssembly modules. These modules can then be loaded and executed in the browser, alongside JavaScript code. This allows for performance-intensive applications, such as games, multimedia processing, or scientific simulations, to run smoothly within the browser environment.

The Best example if have to give to understand the power of WASM/WebAssembly is Figma. if you don't know figma is an online platform to create vector base designs. which was written in C++ and compiled into WebAssembly.

### IoT (**Internet of Things)**

WebAssembly is a great choice for IoT devices. It's lightweight, efficient, and works well with limited resources. Developers can write code in various languages and compile it into WebAssembly modules that run efficiently on IoT devices. It's flexible and allows them to optimize performance for resource-constrained devices. WebAssembly's sandboxed execution environment adds an extra layer of security, isolating applications and protecting sensitive data. It's ideal for sensor data processing, device control, and edge computing in IoT applications.

For example, BBC iPlayer can leverage WebAssembly to run smoothly on IoT devices, delivering a seamless user experience.

### Plugins

WebAssembly can also be used as a technology for creating plugins that can be integrated into existing software applications.

Traditionally, plugins are used to extend the functionality of an application by providing additional features or capabilities. In the past, plugins were often developed using platform-specific technologies and languages, which limited their portability and made them difficult to maintain.

WebAssembly changes this landscape by providing a portable and language-independent runtime environment. With WebAssembly, developers can compile their code into a binary format that can be executed across different platforms and architectures.

By leveraging WebAssembly, developers can create plugins that can seamlessly integrate into various software applications, regardless of the underlying platform. This language independence allows developers to choose the programming language that best suits their needs and expertise.

# Cloud

So for me, Cloud is the most exciting because if you have read my previous blog (which you haven't I know because I don't get many viewers) if you haven't then please go and check it out.

<iframe src="https://giphy.com/embed/xTk9ZZvJbApGt3vy3C" width="480" height="256" class="giphy-embed"></iframe>

[via GIPHY](https://giphy.com/gifs/tech-cloud-xTk9ZZvJbApGt3vy3C)

So first look at it from the start in cloud computing and what is the problem we are facing now. we are now looking at the world of cloud computing and going there are two big buckets into which cloud computing Falls right now

* **virtual machines -** Virtual machines (VMs) are powerful computing environments that run from the kernel and drivers all the way up to the application layer. They encompass a comprehensive stack of software, providing a complete and isolated execution environment for applications.
    
    While VMs offer immense capabilities and can handle a wide range of tasks, they do have some limitations. One of the key drawbacks is their startup time, which can take several minutes. This is because a VM needs to boot up the entire operating system and associated components before running the desired application.
    
* **Containers** - With containers, you can package your application and its dependencies into a self-contained unit that can be easily deployed and run consistently across different environments. Containers offer portability, enabling you to run them on any system that supports containerization.
    
    While virtual machines are designed for power and versatility, containers excel at handling long-running processes. They are well-suited for applications that need to run continuously for extended periods, ranging from days and months to even years.
    
* **Serverless -** Serverless is a relative newcomer, with a very simple promise - you relinquish control of everything to the cloud provider other than your application code itself. In other words, you deploy your code (functions) to the cloud and they take care of provisioning a suitable runtime.
    
    In order for a cloud provider to execute serverless functions, it still needs to provision hardware, operating systems and suitable runtime environments. As a result, there is some significant overhead to servicing requests. This provisioning time is visible to the consumer as a noticeable delay in response when additional resources are required to service a request - an effect known as a ‘cold start’.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688292358084/a1dfd5f2-84a6-4dcf-b9e5-415dde279fd7.png align="center")

So, my point is we have successfully reduced the time taken by a system to start and run your program but it's not enough we need something that doesn't have a cold start like serverless, **Secure sandboxing,** **near-native speed**, **small binaries** and can write it owns preferred language.

We started looking into different runtimes, and one technology that stood out was WebAssembly.

WebAssembly offers several advantages. First, it allows you to execute code within a secure sandbox, which ensures that your code is isolated and cannot interfere with other processes or compromise the system. Second, WebAssembly is highly portable, meaning it can run on different platforms, making it versatile for various use cases. Lastly, it provides excellent performance, which is essential when dealing with compute-intensive workloads.

So This is one of the use cases of WebAssembly in the cloud. and this runtime problem is already is solve by Fermyon with their open-source tool spin. I will explain the spin in my next blog.

Let's see how is this even possible and what makes WebAssebly a server site executable.

## What is WASI? and why do we need it?

WASI, which stands for WebAssembly System Interface, is a standardized interface for WebAssembly modules to interact with the underlying host system. It provides a secure and portable way for WebAssembly modules to access system resources, such as files, network connections, and environment variables.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688290693884/36e570b7-d5ce-45ec-ad2f-cf996917ef3f.png align="center")

With WASI, WebAssembly modules can be executed on different platforms without needing to modify or recompile the code. This portability allows modules to run consistently across diverse systems, making it easier to distribute and deploy applications.

WASI provides a set of standardized functions that allow WebAssembly modules to perform system-level operations. For example, it includes functions for opening and reading files, writing to the console, accessing command-line arguments, and interacting with the network.

Let's take a simple example to illustrate how WASI works. Suppose you have a WebAssembly module that needs to read a file and perform some calculations based on its contents. Without WASI, accessing the file system directly from within the module would be challenging.

However, by using WASI, you can utilize the standardized functions provided by the interface. The module can make a system call to open the file, read its contents using the appropriate functions, and then perform the necessary calculations. The results can be returned or further processed within the module.

The key benefit of WASI is that it allows WebAssembly modules to interact with the underlying system in a controlled and secure manner. It provides a standardized interface that abstracts the differences between operating systems and platforms, enabling seamless execution of WebAssembly code across a wide range of environments.

> **If you're interested in learning more about WASI, WASI runtime, how to use Docker to run your WebAssembly application, and WASM architecture, check out my blog post on What is WebAssembly? You'll learn all about it in detail.**

# what learn to do?

<iframe src="https://giphy.com/embed/Xe2vSY5Q42KbkSCkqZ" width="480" height="360" class="giphy-embed"></iframe>

[via GIPHY](https://giphy.com/gifs/eternalfamilytv-eternal-family-tv-Xe2vSY5Q42KbkSCkqZ)

* WebAssembly is a low-level, efficient bytecode format that can be executed in the browser or on the server.
    
* WebAssembly is portable, meaning it can run on different platforms and architectures.
    
* WebAssembly is secure, with a sandboxed execution environment that isolates code from the underlying system.
    
* WASI is a standardized interface that allows WebAssembly modules to interact with the underlying host system.
    

I think WebAssembly has the potential to revolutionize the way we build cloud applications. It is a powerful tool that can be used to improve performance, security, and portability. I am excited to see how it is used in the future.

# To Be Continues

**I'm excited to share that in my next blog post, I'll be using Spin to build a WebAssembly project and then deploying it to Fermyon Cloud. Stay tuned if you're interested in learning more!**