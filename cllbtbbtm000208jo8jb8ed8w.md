---
title: "How to setup Git and Github for you projects"
seoTitle: "Setup Git and GitHub"
seoDescription: "You can set up your get in your local system and GitHub for your projects."
datePublished: Tue Aug 15 2023 04:37:20 GMT+0000 (Coordinated Universal Time)
cuid: cllbtbbtm000208jo8jb8ed8w
slug: setup-gitgithub
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692027611750/729d4d53-91d6-452e-ae59-03edbe3e6ad9.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692074130963/808b4693-63a3-4ca8-9293-a602eca9b2bb.png
tags: github, git, gitlab, collaboration, wemakedevs

---

Hey everyone in our today's blog we will learn how we can set up Git and GitHub so that we can collaborate with our team meet and get our work done. So let's start

# Installation of git

So we will start with installing git in your local environment. So go to [https://git-scm.com/downloads](https://git-scm.com/downloads) and download it according to your operating system.

To check whether it is installed properly or not we can use the command `git --version` This will show you the git version and if not then try again to install.

As you can see my git version.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692014708069/2f599457-aa66-4495-8eeb-4f1e018521b9.png align="center")

# Let's Create a GitHub Repo

Now that we have installed the git we will create a GitHub repo where we will store our project and share our code with the whole world. I will assume you already have a GitHub account if not then [click here](https://github.com/) and go create a GitHub account.

Now go to github.com on the nav bar you will see a + icon and then click on that.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692015661003/32eb5bb9-0620-4052-8c34-4b4f2ddaaa4b.png align="center")

After you click that you will see these options select the `New Repository`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692015870933/4378b0fd-cbec-43ac-9fdf-a411f7db9f23.png align="center")

After clicking on that you will end up there where you have to enter your repo name which should be unique for your repository and then click on `create repository`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692016257390/0888836a-f6fd-4e02-9d39-4b0243cc62d4.png align="center")

Now your repo has created the repo you can push your code in there.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692016320798/a1deaf7e-ef58-49a2-9a8c-8b3d7bd18d54.png align="center")

# Let's commit some file

We will first create a folder and we will execute this command one-by-one.

we will create a readme file that we will push here is the command `echo "# Devops repo" >> README.md` then we will use the `git init` command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692018085461/6277fca5-a935-43d2-815e-67b79331b4ce.png align="center")

Now we will add the file with the command `git add README.md` this command will add the file in staging and after that, we will commit the file with some comments this command `git commit -m "first commit of this repo"`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692018312911/db85964a-7366-4c38-823a-aa8f4840946a.png align="center")

As you can see we have committed our file now it is time to give a branch name then we will add the remote access to the repo and then finally we will push the commit.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692018699998/b3dee7c9-b50d-4f6d-af1c-e028db9938d5.png align="center")

Yes, we push our changes. You can see your change by going to the repo

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692027439908/9243770a-8f3c-4b70-9ddd-acef6c8e3c33.png align="center")

# The End

That's all for today. We learn a lot see you in my next blog.