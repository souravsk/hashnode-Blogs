---
title: "Unlocking Creativity and Collaboration: The Power of Git Branches"
seoTitle: "The Power of git branches"
seoDescription: "Git Branches make collaboration so much easier."
datePublished: Thu Aug 17 2023 10:42:56 GMT+0000 (Coordinated Universal Time)
cuid: cllf19791000k0aldbnn4c4q6
slug: git-branch
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692178007350/4bf05936-a26d-42bd-bc50-4fa5fa261d20.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692268917692/47e73ee5-91ac-41bb-aa18-bf41fd40626e.png
tags: github, git, devops, gitlab, gitcommands

---

Hey everyone in this blog we will learn what git branches are and why it is one of the most important features of git that make developers like them so much. So let start

# what are Git Branches?

In Git, branches are a part of your everyday development process. When you want to add a new feature or fix a bug—no matter how big or how small—you create a new branch to encapsulate your changes. This makes it harder for unstable code to get merged into the main code base, and it gives you the chance to clean up your code before merging it into the main branch.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692177674584/0e550752-0104-4d69-81ff-6bbf5cb895bd.png align="center")

In this diagram, as you can see the visualizes a repository the center line is the main branch line and the other two are features branches. By developing them in branches, it’s not only possible to work on both of them in parallel, but it also keeps the `main` branch free from questionable code.

The implementation behind Git branches is much more lightweight than other version control system models. Instead of copying files from directory to directory, Git stores a branch as a reference to a commit. In this sense, a branch represents the tip of a series of commits—it's not a container for commits. The history of a branch is extrapolated through the commit relationships.

# How it works

A branch represents an independent line of development. Branches serve as an abstraction for the edit/stage/commit process. You can think of them as a way to request a brand new working directory, staging area, and project history. New commits are recorded in the history for the current branch, which results in a fork in the history of the project.

The `git branch` command lets you create, list, rename, and delete branches. It doesn’t let you switch between branches or put a forked history back together again. For this reason, `git branch` is tightly integrated with the `git checkout` and `git merge` commands.

List all of the branches in your repository.

```bash
git branch
```

Create a new branch called `＜branch＞`. This does *not* check out the new branch.

```bash
git branch <branch>
```

Delete the specified branch. This is a “safe” operation in that Git prevents you from deleting the branch if it has unmerged changes.

```bash
git branch -d <branch>
```

Rename the current branch to `＜branch＞`.

```bash
git branch -m <branch>
```

List all remote branches. 

```bash
git branch -a
```

# Creating Branches

It's important to understand that branches are just pointers to commits. When you create a branch, all Git needs to do is create a new pointer, it doesn’t change the repository in any other way.

If you start with a repository that looks like this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692177687618/7ccb08a4-7acb-4f92-bbb4-5199cd4bcfe6.png align="center")

let's create a branch using the following command:

```bash
git branch bugfix
```

The repository history remains unchanged. All you get is a new pointer to the current commit:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692177701805/6b6cd34f-3eec-49ef-a4b6-f9cbc49e291c.png align="center")

Note that this only *creates* a new branch. To start adding commits to it, you need to select it with `git checkout`, and then use the standard `git add` and `git commit` commands. 

Let's add some files and then we will commit it with this command:

```bash
git checkout bugfix
git add <filename>
git commit -m <messages>
```

After that, it will look like this.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692177981676/757b7b7b-1897-40a5-aebd-36bd6f29da73.png align="center")

# Deleting Branches

Once you’ve finished working on a branch and have merged it into the main code base, you’re free to delete the branch without losing any history:

```bash
git branch -d bugfix
```

However, if the branch hasn’t been merged, the above command will output an error message:

```bash
error: The branch 'crazy-experiment' is not fully merged. If you are sure you want to delete it, run 'git branch -D crazy-experiment'.
```

This protects you from losing access to that entire line of development. If you really want to delete the branch (e.g., it’s a failed experiment), you can use the capital `-D` flag:

```bash
git branch -D crazy-experiment
```

This deletes the branch regardless of its status and without warnings, so use it judiciously.

# Summary

The `git branch` commands primary functions are to create, list, rename and delete branches. To operate further on the resulting branches the command is commonly used with other commands like `git checkout`