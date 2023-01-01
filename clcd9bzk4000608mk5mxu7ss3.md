# How to use Minikube on GitHub Codespaces

Hey, Everyone So this blog is beneficial for everyone but it is very useful for Students like me who are using a decade-old laptop which has a very poor configuration like 4GB Ram with intel i3 Gen3 2 core. A system like this can and will create so many problems while your Learning journey and it will put you in a situation where you will start blaming your system and at a point, you will stop learning which is not good.

And I Know many of you will never face this problem but some of us face these problems mostly Students like me who don't have enough financial source to purchase a new machine.

And I also know many students say that it's enough system resources for their work or project but Students like me who want to pursue careers in DevOps, SRE, Platform Engineer, etc. So to make projects, test applications and create pipelines we use VM which takes so many resources. And Minikube is one of the software which uses VM to spin a Kubernetes Cluster in your local machine so that you can practice or test your applications.

So for those Students or anyone whose Machines don't have enough resources or who doesn't want to waste their time downloading minikube and Kubernetes now they can use GitHub Codespaces to spin up minikube clusters for their projects or practices. So Let's See How First What is GitHub Codespaces?

# What is GitHub Codespaces?

A codespace is a development environment that's hosted in the cloud. You can customize your project for GitHub Codespaces by committing [configuration files](https://docs.github.com/en/codespaces/setting-up-your-project-for-codespaces/introduction-to-dev-containers) to your repository (often known as Configuration-as-Code), which creates a repeatable codespace configuration for all users of your project.

Each codespace runs on a virtual machine hosted by GitHub. You can choose the type of machine you want to use, depending on the resources you need. Various types of machines are available, starting with a 2-core processor, 4 GB of RAM, and 32 GB of storage.

You can connect to your codespaces from your browser, from Visual Studio Code, from the JetBrains Gateway application, or by using GitHub CLI.

So it basically means that you can create your project just by using a browser you don't have to have a good machine with you to do so.

I hope you already know what is Minikube if In case you don't then don't worry I have already publicised blog on a Minikube to read that [Click Here](https://souravk.hashnode.dev/accessing-minikube-with-kubectl) and If want to deep dive into Kubernetes Then [Click Here](https://souravk.hashnode.dev/series/kubernetes) to go to the Kubernetes Series.

## Step 1:- Find the Codespaces

So Let's Start I hope you already have a GitHub Account if Not then Go to github.com and create a GitHub account and those who have an account already can just log in.

So when you log in you will be on your home page as you can see in this image below.

![GitHub HomePage](https://cdn.hashnode.com/res/hashnode/image/upload/v1672485162313/e6b81582-0bf0-4755-a131-47afc8c61a43.png align="center")

So this is what my GitHub Home page looks like. You can see the Navbar there are some menus the first one is the GitHub logo then a search bar and after that pull requests and after that Issues and just next to the issue that is **codespaces.** That's what we are focusing on in this blog. So let's click on that and what's in it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672485673977/fdb7e944-ddd0-42c6-9cdd-c4e66a2277d8.png align="center")

As you can see I have created two codespaces for my 2 repositories.

So I'm not doing to explain all the features that GitHub Codespaces provide otherwise it will be a long page and our main focus is to use minikube.

## Step 2:- Start a Codespace

You can create and use a codespace for any repository you can clone. You can also use a template to create codespaces that are not initially associated with a repository.

### Create a Codespace For any Repository

#### ***Create a codespace by going to the Repository Directly***

#### Step:- A

Open Your Repository for which you want to create the codespace for it. For me it's this one.

Click On the **Code** button

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672556486391/a3b2f3d8-b9b5-470f-960f-7afe639508f4.png align="center")

#### Step:- B

Click On the **Codespaces** Button

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672556517654/cafd1955-163f-44de-bf07-d0c8e654f4b8.png align="center")

#### Step:- C

Click On the Create **Codespace on main** (Main is my branch name. It will show you the branch name that you have selected. If you want to create a codespace for a different branch then change the branch first then start the codespaces)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672556543036/84bd7472-0656-4618-88cd-0d21ccaaff05.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672493718032/c3b50214-a4e9-49d7-bc1f-a85874decc56.png align="center")

WOW!! It's our vscode. Now you can work on your project without thinking about anything on any machine and without worrying about the system.

This is one way of creating a codespace but there is another way also let's just take a quick look at it.

#### ***Create a codespace by going to the Codespace Page***

#### Step:- A

Go to the Codespace by clicking on the codespace menu that is on the Navbar as we have seen earlier In **Step 1**

#### Step:- B

Click on the **New Codespace**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672556604859/463ccd00-3a59-4dfc-ad1b-8d2ae59f1c2a.png align="center")

#### Step:- C

Now You can see the option that is available to create a new codespace.

**Repository**:- In this section, you will select the repository for which you want to create the codespaces for it. (You have to have a repository created already because it won't let you create any new repository here)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672556646450/b9123227-6e3a-4654-afd6-2c512fd76373.png align="center")

**Brach**:- In the section, you will select the branch for that repository. In my case, this repository only has one branch.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672556668820/1c18fa49-3f97-46aa-b558-9fec4b038313.png align="center")

**Region**:- In this section, you will select the closest region available. I'm From India so I selected Southeast Asia. You can select your closest region.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672556703872/25290c38-1c1a-4d3a-aa89-f2a7a57c8376.png align="center")

**Machine Type**:- In this section, you will select the machine which is will be enough for your project. We going to use minikube so we will select the 4-core, 8GB RAM and 32GB Storage.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672556725853/107f50c4-f075-44e7-b032-e0e91cf302ea.png align="center")

#### Step:- C

Click on the **Create Codespace**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672556749801/3a629bc7-a473-4a8d-ba13-c5040e48654a.png align="center")

Now your Codespace is created

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672495812910/2fa00a08-c690-4b9f-a7d4-23054607c3c9.png align="center")

### Use a Template To Create Codespaces

If you're starting a new project, you can get started with development work quickly by creating a codespace from a template. You'll be able to work on your project in a cloud-based development environment, save your files in the cloud, and publish your work to a new remote repository that you can share with others or clone to your local machine.

You can start from a blank template, choose from templates maintained by GitHub for popular technologies such as React or Jupyter Notebook, or launch a codespace from any template repository on GitHub. With a blank template, you'll start with an empty directory, with access to cloud-based compute resources and the tools, languages, and runtime environments that come preinstalled with the default codespace image. With other templates, you'll get starter files for the technology you're working with, plus typically some extra files such as a README file, a `.gitignore` file, and dev container configuration files containing some custom environment configuration.

Let's Create a Black template

Click On **use this template** from the Black Card

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672556775709/85c3ca58-0711-4e73-85b6-a71b60abf37e.png align="center")

Just that it will create a codespace

## Step 3:- Start the Minikuber

Now we will start the minikube I'm going to use the codespace that we have created in Step 2

#### Step:- A

Open the Terminal by Right Clicking on the Explorer and then clicking on Open in Integrated Terminal OR You can press `Ctrl + ~` to Open The Terminal

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672497563356/887f45e4-5119-437b-91d7-46b92a94f3a8.png align="center")

#### Step:- B

Now type the command **minikube start** and press Enter

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1672497880715/4ee5a3ab-4b0b-4be7-a247-5e2ea0c870bf.png align="center")

And that's it we have started the Minikube and see that kubectl is also configured with Minikube which means you can start using the right way.

# THE END

That's all for today hope you learn something today please do share it with your friends so that they can also get to about the GitHub Codespace and use it as there need.

Thank You for reading and one more thing I'm looking for a job so if you know someone who is hiring or your company is hiring let me know.

Email:- souravk326@gmail.com