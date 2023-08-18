---
title: "How to Use Vim"
datePublished: Fri Aug 18 2023 18:49:00 GMT+0000 (Coordinated Universal Time)
cuid: cllgy259s000c09mtb6gsbnp6
slug: how-to-use-vim
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692299570067/3ebece94-2d9e-46dc-bdb7-1cc6d6fab337.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692384476548/f913ba82-5e32-43ce-9f07-34edff50f4cf.png
tags: vim, editors, devops, vim-linux

---

Hey, Everyone in our today's blog we will most important, most hated, most cool, etc code editor which is VIM. Many people don't like using Vim as a code editor but when you work with the server you have to use VIM or nano editor and today we are learning VIM because kind of like it because it makes me look cool.

# What is Vim

Vim is one of the most popular text editors among Linux users. Linux System Administrators especially often prefer it to other editors. It is a free and open-source cross-platform text editor.

## **How to Install Vim**

Vim runs across various platforms such as Windows, Linux, and Mac.

To install Vim on Windows, download the executable file from the [Vim site](https://www.vim.org/download.php) and run the file. Follow the instructions shown on the screen and you'll be good to go.

Vim comes pre-installed on most \*nix operating systems. But if it's installed on your system, you can install it with a package manager of your choice.

Here's the installation command for Debian-based operating systems:

```bash
sudo apt-get update
sudo apt-get install vim
```

Terminal commands to install Vim on Debian-based operating systems

> To ensure that it's installed properly, run `which vim` and you should get `/usr/bin/vim` in your output.

Now if everything is right you can use VIM. you can check by writing VIM on your terminal and it will show this

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692295775039/1e1c1353-d869-4a3a-8735-9afa13416e29.png align="center")

# VIM Modes

You should be aware of the most important concept in Vim before moving on: modes in Vim.

Everything in Vim is considered a mode. You can achieve whatever you want if you understand modes in Vim. There are many modes in Vim. But, we'll be looking at the 4 most important modes.

They are:

1. **Command Mode**
    
2. **Command-Line Mode**
    
3. **Insert Mode**
    
4. **Visual Mode**
    

Let's explore them one by one.

## **What is Command Mode?**

This is the default mode (also called Normal mode) in Vim. Whenever Vim starts, you'll be in this mode. You can switch to any mode from this mode. You can't do this in any other modes.

Basically, to switch from one mode to another, you have to come to Command Mode first and then navigate to the other mode. The commands that you run without any prefix (colon)(:) indicate that you're running the command in command mode.

## **What is Insert Mode?**

This mode is used to edit the contents of the file. You can switch to insert mode by pressing `i` from command mode. You can use the `Esc` key to switch back to command mode.

## **What is Command Line Mode?**

You can use this mode to play around with some commands. But the commands in this mode are prefixed with a colon (:). You can switch to this mode by pressing : (colon) in command mode.

## **What is Visual Mode?**

You use this mode to visually select some text and run commands over that section of code. You can switch to this mode by pressing `v` from the command mode.

The above 4 modes are enough to perform a basic set of file operations in Vim.

Ok, the theory is done. Let's explore Vim practically.

# Let's VIM

For this blog, we will keep it very simple. So let start

***Q*** **create a file and write some content on that file.**

To create a file I will use the `vim` command to create a file. let me show you how it looks.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692296938490/60028070-7a71-4503-a2b5-a9007de82841.png align="center")

so here vim created a file name `textfile.txt` Now it we will write some content on the file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692297503914/bf832bb1-adc0-4453-8bae-224efcdd8cbc.png align="center")

Now we have written some content on the file it time's to write the file or you can say that it's time to save the file to do so we have to first get into the command mode for that we will press `Ese` the key the we will write `:w` which will save the file

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692297762141/08c5937d-a4f6-43d6-8ac2-4f1b1a59e132.png align="center")

Now the file is saved we will exit from Vim and to do so we will use the command `:q` to exit.

Now if you want to check that your file has been saved properly or not so to check that we will use `cat` command to see inside the file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692297911222/3cb8715f-5649-4422-b528-f3edcfaadd6b.png align="center")

Nice all of our content is saved.

# The End

That's all for today there are many other commands you can explore so go ahead and try.