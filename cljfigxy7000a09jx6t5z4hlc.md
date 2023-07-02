---
title: "Introduction to WebAssembly aka WASM"
seoTitle: "New tech WebAssembly"
seoDescription: "WebAssembly is a new technology that allows us to run code written in other languages on the web, at near-native speed."
datePublished: Wed Jun 28 2023 09:25:26 GMT+0000 (Coordinated Universal Time)
cuid: cljfigxy7000a09jx6t5z4hlc
slug: intro-wasm
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688295151151/39eb5440-f972-4108-9498-2423040dc752.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1688295098322/9a688c68-ca01-4ac8-9ffb-217259872045.png
tags: javascript, webassembly, devops, wasm, wemakedevs

---

Hey Everyone today in this blog we are going to learn about what is WebAssebley is and why everyone is talking about it.

WebAssembly is the latest technology to be added to the web toolkit (alongside HTML, JavaScript and CSS), but why was it invented? And what purpose does it serve? This blog will answer these questions, and more, by taking a brief look at the history of the web. We’ll review the tools and technologies, both past and present, that are used to deliver interactive, app-like experiences. Finally, we’ll see how the experimental and successful asm.js project resulted in the formation of WebAssembly.

<iframe src="https://giphy.com/embed/j32JzYzucBtkUZb1Rr" width="480" height="270" class="giphy-embed"></iframe>

[via GIPHY](https://giphy.com/gifs/HBOMax-girl-power-wonder-woman-hbo-max-j32JzYzucBtkUZb1Rr)

# Web History

The web has evolved from being a static platform to a dynamic one. In the early days, plugins were used to create interactive web pages. However, plugins have some problems, such as being slow, difficult to install, and a security risk.

In recent years, JavaScript has become the go-to language for creating interactive web pages. JavaScript is fast, easy to use, and secure. It is also built into the browser, so there is no need to install any plugins.

HTML5 is another important technology that has enabled the web to become more interactive. HTML5 added new features to HTML that make it possible to create interactive web applications without the need for plugins.

The JavaScript engines that run in browsers have also gotten much faster in recent years. This means that web applications can now be as fast as native applications.

Overall, the web is in a much better place today than it was when plugins were the dominant technology. We now have the tools and technologies to create powerful and interactive web applications that can compete with desktop applications.

## why do we need WebAssembly?

WebAssembly is a new technology that allows us to run code written in other languages on the web, at near-native speed. This means that we can create web applications that are more powerful and interactive than ever before.

Here are some of the reasons why we need WebAssembly:

* **Performance:** Web assembly code can be executed much faster than JavaScript code. This is because WebAssembly is compiled to native machine code, while JavaScript is interpreted by the browser.
    
* **Security:** WebAssembly is a secure technology. It is sandboxed from the rest of the web application, so it cannot access the user's computer or the internet without permission.
    
* **Flexibility:** WebAssembly can be used to run code written in a variety of languages, including C, C++, Rust, and Go. This means that developers can use the language that they are most comfortable with, and they can reuse existing code libraries.
    

In simple terms, WebAssembly allows us to run code on the web that is just as fast and secure as code that is running on our computers. This opens up a whole new world of possibilities for web applications.

So from where it all started?

# **The asm.js Project**

**asm.js** was a project by Mozilla that created a subset of JavaScript that was designed to be more efficient than regular JavaScript. It did this by removing garbage collection and allowing for other runtime optimizations. This made it possible to create web applications that were much faster than what was possible with regular JavaScript.

asm.js was a success, and it helped to pave the way for the development of WebAssembly. WebAssembly is a newer technology that is even more efficient than asm.js. It is a binary format that can be executed by the browser, and it can be used to run code written in a variety of languages, including C, C++, Rust, and Go.

The asm.js project was a valuable experiment, and it helped to show that it was possible to create high-performance web applications using a subset of JavaScript. The lessons learned from asm.js were incorporated into WebAssembly, and as a result, WebAssembly is now the most efficient way to run code on the web.

So Now we know why need and how it is been created. Let's try to execute some program to understand even better how this work.

# Try WSAM/WebAssembly

I want you to also try to execute the program with me don't just read it will help to understand how it works and it creates different questions when you will try to do it by yourself.

### Step 1

First, go to google.com and search web assembly studio or click [here](https://webassembly-studio.kamenokosoft.com). Then we have to select any of the projects that they have and then click on the create button.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687865883536/dd053904-dce0-4ebe-b0f8-eb22c6e1d3ab.png align="center")

The newly created project has a number of different files, we’ll ignore the files within the root folder of the project, these are part of the build process and are not relevant for now learning objectives.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687865996905/ce30efdd-7cac-4ca7-a762-582f2d44bbef.png align="center")

The **src** folder contains three files:

* * `main.cpp` - Imports `SDL2/SDL.h` and draws a blue rectangle using `SDL_RenderFillRect`.
        
        \* `main.html` - For canvas to be rendered.
        

the project has simple SDL2 code for the WebGL app. This project owes to [emscripten compiler backend](https://github.com/nokotan/emscripten-compiler).

### step 2

Now we have to first compile the project then we can run the project the C++ file needs to be compiled into WebAssembly. Simply click the ‘Build’ option in the toolbar to kick off the compilation process. The output window should display the task build completed.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687866129596/de205be8-449a-4f04-91c7-83423ec1a4e5.png align="center")

you’ll notice that a new file, **main.wasm** has appeared in the project folder structure. So as aspected, then it gives as the .wasm file. and it has also created main.js file.

### Step 3

Now let's run the code Finally click the ‘Run’ option in the toolbar, and you should see a big red rectangle and a smell blue rectangle which is moving to the right side. If you are executing this program with me you will be able to see it by now.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687866416198/f4ee8bf6-96da-452f-8c85-610e262e708c.png align="center")

This might not look all that exciting or significant, but it is! That’s C++ code, running natively in your web browser, thanks to WebAssembly.

We’ll dig into this example in a bit more detail to gain a better understanding of WebAssembly

### **Review the wasm File in Binary**

This time we’re going to take a closer look at the compiled output. Right-click the generated wasm file and select the ‘View as Binary’ option:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687866621884/7b6136fe-dc22-4cda-aebf-3bde21505fe7.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687868197397/0525b348-d11a-4e92-9f00-3aa112a296dc.png align="center")

WebAssembly code is distributed as binary modules, making them both compact and efficient (fast to download, and fast to parse). However, this doesn’t make them very readable.

WebAssembly modules cannot be loaded and executed by the browser directly (e.g. via **script** elements), they must be downloaded, compiled and instantiated via JavaScript. The WebAssembly specification defines the concept of a ‘host’, which in this case is the browser’s JavaScript engine. A module cannot perform any useful functions without interoperating with the host, most notably WebAssembly modules cannot directly perform any I/O (e.g. they cannot open sockets, access the DOM, write to filesystems, etc). Also, WebAssembly functions are invoked synchronously, the JavaScript host ‘yields’ to the module function, waiting until it returns before resuming.

That's all for the test let's understand the design goals while creating the web assembly.

# WebAssembly design goals

<iframe src="https://giphy.com/embed/3o7TKGMZHi73yzCumQ" width="480" height="480" class="giphy-embed"></iframe>

[via GIPHY](https://giphy.com/gifs/nightcap-poptv-pop-tv-3o7TKGMZHi73yzCumQ)

* **Minimum Viable Product (MVP)**: WebAssembly was designed to be a small, focused technology that could be released quickly. This meant that some features were not included in the initial release, but they can be added later. For example, the initial release did not include support for threads or floating point numbers.
    
* **Security:** WebAssembly is designed to be secure, running in a sandbox that is isolated from the host environment. This means that malicious WebAssembly modules cannot access the user's computer or the internet.
    
* **Portability:** WebAssembly modules are designed to be portable, executing in the same way regardless of the browser or operating system they are running on. This means that WebAssembly modules can be developed once and then deployed to any platform that supports WebAssembly.
    
* **Performance:** WebAssembly is designed to be fast, executing at near-native speed. This is because WebAssembly modules are compiled into native machine code, which is then executed by the browser's JavaScript engine.
    
* **Efficiency:** WebAssembly modules are designed to be efficient, using as little memory and CPU as possible. This is because WebAssembly modules are compiled to a low-level bytecode format that is optimized for performance.
    

These design goals have made WebAssembly a powerful tool for developing high-performance, secure, and portable web applications.

# So what did we learn today?

<iframe src="https://giphy.com/embed/31st0ztjKBnkS5eDhs" width="480" height="254" class="giphy-embed"></iframe>

[via GIPHY](https://giphy.com/gifs/SERVPROIndustries-sarcastic-sarcasm-learn-31st0ztjKBnkS5eDhs)

WebAssembly is a new technology that allows us to run code written in other languages on the web, at near-native speed. This means that we can create web applications that are more powerful and interactive than ever before.

WebAssembly is designed to be secure, portable, and efficient. It is a powerful tool for developing high-performance, secure, and portable web applications.

So far, we have learned about what WebAssembly can do on the browser. This is already pretty awesome, but if you have read my previous blogs, you know that I am passionate about cloud and cloud-native technologies.

In my next blog, I will explain how WebAssembly is being used in cloud-native and other technologies, and why I am super excited about the potential of "WASM on Cloud."

# To Be Continued

<iframe src="https://giphy.com/embed/l1J3IHzSUmCpXThqo" width="480" height="320" class="giphy-embed"></iframe>

[via GIPHY](https://giphy.com/gifs/thebachelorau-bachelor-bachelorau-l1J3IHzSUmCpXThqo)

Please do follow me anywhere you like I'm everywhere if you are interested in WebAssembly or Cloud then stay tuned for my next blog and upcoming blogs because most of them are about WebAssembly.