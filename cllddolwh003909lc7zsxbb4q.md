---
title: "Mastering the Essentials: A Beginner's Guide to Git Basic Commands"
seoTitle: "10 must know git command"
seoDescription: "As a developer, you must know these 10 basic git commands."
datePublished: Wed Aug 16 2023 06:55:18 GMT+0000 (Coordinated Universal Time)
cuid: cllddolwh003909lc7zsxbb4q
slug: mastering-the-essentials-a-beginners-guide-to-git-basic-commands
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692168749885/763dd956-e534-4c0f-9921-d1ecc02addf5.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692168800060/ee6f553f-0ced-41d4-b8ed-57b839247d2c.png
tags: github, git, learning, gitcommands, wemakedevs

---

In the vast world of software development, version control is like a guiding star that keeps your coding journey on track. Enter Git, your trusty intergalactic companion, here to make version control as simple as counting to three! 🌌🛸

So, git, which is used to track the changes in your code is as easy as sharing memes. So just knowing the basic command it will make your work easy. Let's learn some basic commands that will kick-start your git journey.

**1\. git init -** The git init command is the first command that you will run on Git. The git init command is used to create a new blank repository. It is used to make an existing project as a Git project. Several Git commands run inside the repository, but the init command can be run outside of the repository.

The git init command creates a `.git` subdirectory in the current working directory. This newly created subdirectory contains all of the necessary metadata. These metadata can be categorized into objects, refs, and temp files. It also initializes a HEAD pointer for the master branch of the repository.

Let's create a new folder and then use the git init command. `git init`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692095831136/8557626c-36fb-4a53-a742-7c591287e861.png align="center")

**2\. git add -** The git add command is used to add file contents to the [Index (Staging Area)](https://www.javatpoint.com/git-index). This command updates the current content of the working tree to the staging area. It also prepares the staged content for the next commit.

The git add command is a core part of Git technology. It typically adds one file at a time, but there some options are available that can add more than one file at once.

The git add command can be run many times before making a commit. These all add operations can be put under one commit. The add command adds the files that are specified on the command line.

Let's create a file and then try to add the file to the staging area.

`git add filename`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692096225955/f5302f9e-f700-4906-9b94-7cc9b26ac747.png align="center")

**3\. git status -** The git status command is used to display the state of the repository and staging area. It allows us to see the tracked, untracked files and changes. This command will not show any commit records or information.

Mostly, it is used to display the state between [**Git Add**](https://www.javatpoint.com/git-add) and [**Git commit**](https://www.javatpoint.com/git-commit) commands. We can check whether the changes and files are tracked or not.

`git status`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692096413089/fd72d100-4b2c-4696-8da8-b2d45c2b8a4b.png align="center")

As you can see we have added the file that is showing in green color. You can also see that it is showing `no commits yet`. So let's commit this with the commit command.

**4\. git commit -** It is used to record the changes in the repository. It is the next command after the [git add](https://www.javatpoint.com/git-add). Every commit contains the index data and the commit message. Every commit forms a parent-child relationship. When we add a file in Git, it will take place in the staging area. A commit command is used to fetch updates from the staging area to the repository.

Commits are the snapshots of the project. Every commit is recorded in the master branch of the repository. We can recall the commits or revert it to the older version. Two different commits will never overwrite because each commit has its commit-id.

let's commit to the changes. `git commit -m "commit"`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692097373001/cf121032-8e2f-432e-9f7e-47497f149445.png align="center")

As you can see we have created a new commit and it also shows the 1 file changed.

**5\. git log -** The advantage of a version control system is that it records changes. These records allow us to retrieve the data like commits, figuring out bugs, and updates. But, all of this history will be useless if we cannot navigate it. At this point, we need the git log command.

Git log is a utility tool to review and read the history of everything that happens to a repository. Multiple options can be used with a git log to make history more specific.

`git log`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692102168813/ee6a98a9-7515-4974-b95d-94c9d51a9817.png align="center")

**6\. git push** \- The push term refers to uploading local repository content to a remote repository. Pushing is an act of transferring commits from your local repository to a remote repository. Pushing is capable of overwriting changes; caution should be taken when pushing.

we can say the push updates the remote refs with local refs. Every time you push into the repository, it is updated with some interesting changes that you made. If we do not specify the location of a repository, then it will push to the default location at **origin main**.

`git push -u origin main`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692103183132/e8f9acd2-0b46-42c0-958d-42ebf5dd51e0.png align="center")

here I'm using another repo to show you how you can push our commits to a remote repo.

**7\. git branch -** The command git branch is used to check on which branch you are and it will also show you how main different branches are also available. It is used to list, rename, and delete branches within a Git repository

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692104293086/a9003740-a8f3-40f8-97cc-8120d483b7fc.png align="center")

I have just one branch which is the main so it is showing the main only.

**8\. git checkout** \- The `git checkout` command in Git is used to switch between different branches, commit points, or files in a Git repository. It's a versatile command that allows you to navigate through the history of your project and work on different branches or commit states.

To switch to an existing branch, you use the following syntax:

```bash
git checkout <branch_name>
```

**9\. git pull -** The `git pull` command in Git is used to fetch and integrate changes from a remote repository into your current local branch. It's essentially a combination of two other Git commands: `git fetch` and `git merge`.

When you run `git pull`, Git will first fetch any new changes from the remote repository that your local repository is tracking. This is done using the `git fetch` command.

```bash
git pull origin <branch_name>
```

Here, `<branch_name>` is the name of the branch on the remote repository that you want to pull changes from (often `main`, `master`, or a feature branch).

**10\. git merge -** The `git merge` command in Git is used to combine the changes from one branch into another. It's a crucial command for integrating code changes and creating a unified history in your Git repository.

To merge changes from one branch into another, follow this syntax:

```bash
git merge <source_branch>
```

Here, `<source_branch>` is the branch that contains the changes you want to merge into the current branch.

# The End

Thank you for taking the time to read my blog post. If you enjoyed what you read, don't forget to share it with others and subscribe to my blog newsletter for more insightful content in the future! Your support means the world to me.