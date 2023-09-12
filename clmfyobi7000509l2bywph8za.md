---
title: "Minikube for Kubernetes"
seoTitle: "Minikuber for testing and learning Kubernetes."
datePublished: Tue Sep 12 2023 06:58:11 GMT+0000 (Coordinated Universal Time)
cuid: clmfyobi7000509l2bywph8za
slug: minikube-for-kubernetes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694501764357/2cf8141f-ed78-4a32-b719-3b0550e65f99.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1694501824130/f787532d-180f-49d4-926e-e2771b992087.png
tags: docker, kubernetes, containers, k8s, minikube

---

Hey Everyone in today's blog we are going to set up our Kubernetes cluster in your local machine so that we can test our application before deploying it directly to production.

# What is Minikube?

Minikube is like a tiny playground for practicing and learning about a bigger thing called Kubernetes.

Imagine Kubernetes as a super-smart manager for running and managing lots of software programs (we call them "containers") on a bunch of computers. It's like a traffic police for these containers, ensuring they run smoothly and don't crash into each other.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694493612333/8cf8ac50-dfe4-46e8-a62d-2272ef83e030.png align="center")

Now, Minikube is a mini-version of this Kubernetes manager that you can run on your own computer. It's like having a small-scale model of a big city's traffic system on your desk. You can experiment with it, test things out, and get comfortable with how Kubernetes works without needing a whole cluster of computers.

So, in very simple terms, Minikube is a tool that lets you practice and learn Kubernetes on your own computer, like a training wheels version before you tackle the real deal.

# How Minikube Works

Minikube is a tool that allows you to run Kubernetes on your local machine. It creates a single-node cluster in a virtual machine (VM). This cluster allows you to demonstrate Kubernetes operations without having to install the full K8s.

Minikube works by taking a Docker image and running it using Kubectl. Kubectl is a command line interface for running commands against Kubernetes clusters.

Minikube uses the docker-machine to manage the Kubernetes VM. It embeds VirtualBox and VMware Fusion drivers so there are no additional steps to use them.

Minikube can create a one-node cluster by default, but you can also create a multi-node cluster.

# Now Setup Minikube

So we are using Docker to run our cluster so if you haven't downloaded the Docker then [click here](https://www.docker.com/products/docker-desktop/) to download it and install it. After that download the Minikube by [clicking here](https://minikube.sigs.k8s.io/docs/start/) and installing it. Installation instructions will be available on that page.

Now Open your terminal and run `minikube status` This will show you the status of Minikube and it will also confirm that you have successfully installed the Minikube. If you have messed up the configuration you can use \`**minikube delete --purge --all\`** command to delete Minikube and reinstall it.

if `minikube status` shows this

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694496454621/3ef7ab54-bf6f-4191-9858-dac3cb61ad31.png align="center")

Then it's installed nicely we will run the `minikube start` to start Minikube.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694496640497/ef986972-3eb6-4ecb-ae92-2ba3252dba78.png align="center")

Now the Minikube has started it pulls the images and runs on the docker. You can run the command `minikube status` to see the status.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694497020143/c6a5778d-22bb-4997-b077-c5f249fd5bc7.png align="center")

Let's check the docker container with `docker ps` command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694497166256/7ec1a4ad-ac06-4e28-992a-f8bdd8396e29.png align="center")

As you can see it is running. That means we have set up Minikube.

# Basic Commads to use Minikube

Now we will see some basic commands to use Minikube that we will need while using Minikube.

**Start a cluster by running:**

```shell
minikube start
```

**Access the Kubernetes dashboard running within the minikube cluster:**

```shell
minikube dashboard
```

**Once started, you can interact with your cluster using** `kubectl`**, just like any other Kubernetes cluster. For instance, starting a server:**

```shell
kubectl create deployment hello-minikube --image=kicbase/echo-server:1.0
```

**Exposing a service as a NodePort**

```shell
kubectl expose deployment hello-minikube --type=NodePort --port=8080
```

**minikube makes it easy to open this exposed endpoint in your browser:**

```shell
minikube service hello-minikube
```

**Upgrade your cluster:**

```shell
minikube start --kubernetes-version=latest
```

**Start a second local cluster (*note: This will not work if minikube is using the bare-metal/none driver*):**

```shell
minikube start -p cluster2
```

**Stop your local cluster:**

```shell
minikube stop
```

**Delete your local cluster:**

```shell
minikube delete
```

**Delete all local clusters and profiles**

```shell
minikube delete --all
```

# THE END

That's all for today I hope you learn a lot. Start testing your application and learning Kubernetes.