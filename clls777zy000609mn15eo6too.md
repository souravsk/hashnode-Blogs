---
title: "Create User In Ubuntu"
seoTitle: "Create a user in Ubuntu"
datePublished: Sat Aug 26 2023 15:50:22 GMT+0000 (Coordinated Universal Time)
cuid: clls777zy000609mn15eo6too
slug: create-user-in-ubuntu
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693064429435/1e17d3c4-d1a1-4b1a-87a2-9b9e132ff7c7.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1693064586197/89e70aee-cf7c-4c81-b16f-5da60b676c8f.png
tags: ubuntu, linux, command-line, linux-for-beginners, wemakedevs

---

Hey everyone, in today's blog, we will launch an EC2, create a new user, and perform some other operation. Let's go

## Create an EC2 Instance

First, we will create an ec2 instance and then ssh into that instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692970506469/119bf96c-d1da-4d72-93a0-a3faedd3dad2.png align="center")

Now SSH into that instance with the SSH command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693035429894/d2a8cb87-cc3d-43ed-afa2-d37e7e01da78.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693038200518/7c46dc57-9d39-4587-9668-34a59f19d6b5.png align="center")

# To Add

### Create a new user

Now we are connected to the Server. Let's create new users name `sourav`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693038686018/b3d55d32-3de8-4019-b370-302dbec8691f.png align="center")

## Switch to the other user

Let's switch the user `sourav` but before we do that let's check the current user name.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693039494110/270d8045-f203-40a2-87d7-217ed4a11b30.png align="center")

# To Modify

These are the commands used to modify your user settings.

To modify the username of a user:

```bash
usermod -l new_username old_username
```

To change the password for a user:

```bash
sudo passwd username
```

To change the shell for a user:

```bash
sudo chsh username
```

To change the details for a user (for example real name):

```bash
sudo chfn username
```

To add a user to the `sudo` group:

```bash
adduser username sudo
```

or

```bash
usermod -aG sudo username
```

And, of course, see also: `man adduser`, `man useradd`, `man userdel`... and so on.

# To Delete

To remove/delete a user, first you can use:

```bash
sudo userdel username
```

Then you may want to delete the home directory for the deleted user account :

```bash
sudo rm -r /home/username
```