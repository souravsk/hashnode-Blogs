---
title: "Mastering File Permissions: Exploring chmod, chown, and ACL Commands"
seoTitle: "Learn how to change file permission with the help of linux commands."
datePublished: Thu Aug 31 2023 09:34:55 GMT+0000 (Coordinated Universal Time)
cuid: cllyyznsi00050amkbggea53f
slug: chmod-chown-acl
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693474318260/7835e5f9-6bfb-4197-adee-8f3fb90754ed.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1693474477789/f313ab8a-3751-429e-af83-833abe69d732.png
tags: linux, linux-for-beginners, linux-basics, linux-commands, wemakedevs

---

Hey everyone

# Linux filesystem

The Linux filesystem gives us three types of permissions. Here is a simplified review:

* **U**ser (or user owner)
    
* **G**roup (or owner group)
    
* **O**ther (everyone else)
    

With these permissions, we can grant three (actually five, but we’ll get to that in a minute) types of access:

* **R**ead
    
* **W**rite
    
* e**X**ecute
    

These levels of access are often adequate in many cases.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693472610478/1bc36263-42a3-4b3a-8684-a09630f03272.png align="center")

# What is Chmod?

Imagine your computer's files and folders are like items in a room. Now, sometimes you want to control who can enter your room and what they can do with the items inside. That's where `chmod` comes in.

`chmod` stands for "change mode," and it's a command used in the command-line interface of computers, especially in Unix-like operating systems like Linux. It helps you set permissions for files and folders, just like deciding who can enter your room and whether they can read, write, or execute things inside.

There are three main types of permissions:

1. **Read (r):** This allows someone to open and view the content of a file, but they can't make any changes to it.
    
2. **Write (w):** This lets someone modify the content of a file. They can add, delete, or change things.
    
3. **Execute (x):** This permission is like allowing someone to use an item in your room. For files, it means running the file as a program. For folders, it allows someone to enter and access the contents inside.
    

## Why it is important

Using `chmod`, you can decide which of these permissions to grant to the owner of the file, the group of people it belongs to, and everyone else. You can choose to allow or deny each type of permission for these three categories.

We need `chmod` because it helps manage security and privacy. For example, you might have personal files you don't want anyone else to read or modify. By setting the right permissions with `chmod`, you can control who can do what with your files and folders. It's like putting locks on certain items in your room to keep them safe from unwanted changes.

### Let's see how it works.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693472179238/899303ab-032b-45cc-8329-c22dc25520bd.png align="center")

In this above example first, we have created a simple text file that has read and write permission only. So we want to add some permission to this file and for that, we can use chmod command.

For example, we have added execute permission. You can see in the example before using chmod command the file has only read and write permission to the user and group. Then we add execute permission to the user.

There are many other ways to change the mod of the file like using no.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693472730377/26b9f3d4-12fe-4371-a9c9-0df0fe1d8393.png align="center")

You can use this chart to add permission or remove it.

# What is chown?

`chown` stands for "change owner," and it is a command used in Unix-like operating systems to change the ownership of files and directories. Ownership in these systems refers to the user and group that have certain permissions and control over the files and directories.

The basic syntax of the `chown` The command is as follows:

```bash
chown [options] new_owner:new_group file(s)
```

Here, `new_owner` represents the new user who will become the owner of the specified file(s) or directory, and `new_group` represents the new group associated with the file(s). The command allows you to change either the owner, the group, or both.

For example, if you have a file named "example.txt" and you want to change its owner to a user named "newuser" and its group to a group named "newgroup," you would use the following command:

```bash
chown newuser:newgroup example.txt
```

Keep in mind that using the `chown` command usually requires administrative privileges (root or superuser access) to change ownership of files that you don't own. It's a powerful command that can be used to manage access and permissions on a Unix-like system.

### Let's try this command

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693473256369/5b4e4a05-ba52-4c71-a382-5822daac44c7.png align="center")

So I have created a new user name `ankit` as you can see now we have 3 different users.

So we are going to use the same file that we used in our chmod example that was created in the Sourav user account. so its owner is Sourav we will change that to Ankit with the user of the `chown` command.

So you can see that in our example we have changed the owner from Sourav to Ankit.

# What is ACL?

ACL stands for "Access Control List." It's a concept and a mechanism used in computer systems, including operating systems and network devices, to define and manage permissions for users and groups accessing files, directories, or other resources.

In a simple way, think of an ACL as a list of rules attached to a file or directory that specifies who can do what with that file or directory. These rules allow you to grant or restrict specific permissions to different users or groups beyond the traditional Unix-like permissions (read, write, execute) associated with the file's owner, group, and others.

For instance, with ACLs, you can grant read access to a specific user, even if they're not the owner of the file. Or you can give write access to a certain group while denying access to others. ACLs provide a finer level of control over access permissions, which can be especially useful in multi-user environments or when dealing with complex permission requirements.

### Let's take an example to understand

Let's say you have a file named "confidential.txt" and you want to control access to it using ACLs.

1. **Basic Unix-like Permissions:** By default, you might have these basic permissions:
    
    * Owner: Read, Write
        
    * Group: Read
        
    * Others: No access
        
2. **Adding ACLs:** Now, you want to grant an additional user named "Alice" the ability to read the file, even though she's not the owner and not in the group.
    
    ```bash
    $ setfacl -m u:Alice:read confidential.txt
    ```
    
    This command adds an ACL rule that gives "Alice" read access to the file "confidential.txt".
    
3. **Viewing ACLs:** You can then use the `getfacl` command to see the ACLs on the file:
    
    ```bash
    $ getfacl confidential.txt
    ```
    
    This will show you both the basic permissions and the added ACL rule.
    
4. **Removing ACLs:** If you later want to remove Alice's read access using ACLs:
    
    ```bash
    $ setfacl -x u:Alice confidential.txt
    ```
    
    This command removes the ACL rule that granted "Alice" access to the file.
    

The main point here is that ACLs allow you to give specific users or groups permissions that are different from the standard owner, group, and others categories. This gives you more flexibility in managing access to files and directories in complex scenarios.

# THE END

That's all for today hope you have learned and understood if not let me know.