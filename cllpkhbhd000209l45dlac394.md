---
title: "what are SSH and SCP?"
seoTitle: "What is SSH and SCP"
datePublished: Thu Aug 24 2023 19:38:49 GMT+0000 (Coordinated Universal Time)
cuid: cllpkhbhd000209l45dlac394
slug: ssh-scp
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692905801827/b890d26e-9e6b-4677-a54e-628d34f39f2c.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692905906628/7274c5a5-314b-4b94-8d8f-754ed22b2590.png
tags: devops, ssh, file-transfer, scp, wemakedevs

---

Heyevery on today's blog we will learn about SSH and SCP. What it is and why everyone needs to learn mostly if you want your career in cloud, DevOps, etc. For any server-related work, you will end up using these commands. So let's go and learn.

# What is SSH?

SSH, or Secure Shell, is like a secret tunnel for your computer. It lets you securely connect to another computer over the internet. It's often used to control remote computers or transfer files, and it keeps your communication private and safe from snooping.

# Why do we need SSH?

We need SSH to safely communicate and interact with computers or servers that are far away, like in a different location or even another country. It's important because it keeps the information you're sending and receiving, like passwords and data, encrypted and protected from hackers or unauthorized access. It's like having a locked and secure channel to talk to a distant computer without others being able to listen in or mess with your conversation.

### Let's try to Connect a VM

First, let's create a VM or in the case of GCP it will be VM instances. I'm using GCP to create the VM.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692891325804/9c8c4047-8f34-4afa-99d4-64607cd28ce7.png align="center")

Now that we have created the VM let's comment on that VM using the `SSH` Command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692891241977/ca4a41e3-7c3d-4bf4-9359-0829bc3a6ff3.png align="center")

As you can see I used ssh to connect to the remote server. Now let's just create a file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692891477897/e4408a60-ea62-43f6-8e7f-db7efb4e4b95.png align="center")

# What is SCP?

SCP stands for "Secure Copy Protocol." It's a command-line tool used to securely transfer files between a local and a remote computer, similar to how you might copy files using the regular "copy" or "cut and paste" commands on your computer's file system.

What makes SCP special is that it uses the SSH protocol for its communication. This means that just like SSH, SCP also provides encryption and security while transferring files. It's often used when you want to move files between your local computer and a remote server or between two remote servers, ensuring that the data remains confidential during the transfer.

# Why do we need SCP?

  
We need SCP (Secure Copy Protocol) for several reasons:

1. **Security:** Just like SSH, SCP uses encryption to protect the data being transferred. This is crucial when moving sensitive files or information between computers, especially over untrusted networks like the internet. It ensures that your data remains confidential and cannot be easily intercepted by malicious parties.
    
2. **Reliability:** SCP provides a reliable way to transfer files. It checks for errors during the transfer and can automatically resume if the connection is interrupted. This is important for transferring large files or in situations where the network might not be perfectly stable.
    
3. **Remote Management:** SCP is commonly used to manage and maintain remote servers or computers. It allows administrators to easily upload or download files, update configurations, and perform other tasks without physically being present at the remote location.
    
4. **Automation:** SCP can be integrated into scripts and automated processes. This is useful for tasks such as regular backups, data synchronization, or deploying files to multiple servers simultaneously.
    
5. **Cross-Platform:** SCP is supported on most Unix-like operating systems, including Linux and macOS. This makes it a convenient and consistent way to transfer files across different systems.
    
6. **Command-Line Interface:** SCP is operated from the command line, which can be especially efficient for advanced users who are comfortable with terminal commands. It allows for quick and precise file transfers without the need for a graphical user interface.
    

In summary, SCP is a secure and reliable method for transferring files between computers, particularly when security and privacy are paramount. It's widely used in system administration, development, and various other fields where safe and efficient file transfer is required.

### Let's try to transfer a file

So we will transfer a local text file to our GCP VM remote server using `SCP`.

SCP Syntax

```bash
scp [OPTIONS][ssh key] [[user@]src_host:]file1 [[user@]dest_host:]file2
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692892133272/b0044062-7e21-459b-99ba-558033abeff0.png align="center")

So we have transferred the file to the remove server. Let's check on the server side

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692897770621/98a0f62c-290b-4d05-80a6-cd83275dd2a9.png align="center")

Nice it's done. As you can see file name `fileOnLocal.txt` is a local file from my laptop.

# THE END

Thanks for reading this blog. If you like it please share it.