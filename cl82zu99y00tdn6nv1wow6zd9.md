## Getting started with Kubernetes in your local environment

In this blog, we will learn how to install Kubernetes in your local system and also get to know the tools that are being used in installing Kubernetes in the Production-ready environment.

# Kubernetes Installation with tools

We can Install Kubernetes in a different way or we can say we can install it as per your requirement. There are some different use cases that most used

- **All-in-One Single-Node Installation:-** In this setup, all the control plane and worker components are installed and running on a single node. While it is useful for learning, development, and testing, it is not recommended for production purposes.
- **Single-Control Plane and Multi-Worker Installation:-** In this setup, we have a single-control plane node running a stacked etcd instance. Multiple worker nodes can be managed by the control plane node.
- **Single-Control Plane with Single-Node etcd, and Multi-Worker Installation:-** In this setup, we have a single-control plane node with an external etcd instance. Multiple worker nodes can be managed by the control plane node.
- **Multi-Control Plane and Multi-Worker Installation:-** In this setup, we have multiple control plane nodes configured for High-Availability (HA), with each control plane node running a stacked etcd instance. The etcd instances are also configured in an HA etcd cluster and, multiple worker nodes can be managed by the HA control plane.
- **Multi-Control Plane with Multi-Node etcd, and Multi-Worker Installation:-** In this setup, we have multiple control plane nodes configured in HA mode, with each control plane node paired with an external etcd instance. The external etcd instances are also configured in an HA etcd cluster, and multiple worker nodes can be managed by the HA control plane. This is the most advanced cluster configuration recommended for production environments.

As the Kubernetes cluster's complexity grows, so do its hardware and resource requirements. While we can deploy Kubernetes on a single host for learning, development, and possibly testing purposes, the community recommends multi-host environments that support High-Availability control plane setups and multiple worker nodes for client workload.

Once we have decided what type of installation we need for our work. Next is the Infrastructure. Infrastructure is guided by the desired environment type, either a learning or production environment. 

For infrastructure, we need to decide on the following:

- Should we set up Kubernetes on bare metal, public cloud, private, or hybrid cloud?
- Which underlying OS should we use? Should we choose a Linux distribution - Red Hat-based or Debian-based, or Windows?
- Which networking solution (CNI) should we use?

## Installing Production Clusters with Deployment Tools

So when it comes to production-ready Kubernetes clusters, there are several recommended tools for Kubernetes cluster bootstrapping.

Let’s take a look at the most popular installation tools available:

### kubeadm
[kubeadm](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/) is a first-class citizen in the Kubernetes ecosystem. It is a secure and recommended method to bootstrap a multi-node production-ready Highly Available Kubernetes cluster, on-premises or in the cloud. kubeadm can also bootstrap a single-node cluster for learning. It has a set of building blocks to set up the cluster, but it is easily extendable to add more features. Please note that kubeadm does not support the provisioning of hosts - they should be provisioned separately with a tool of our choice.

![https://courses.edx.org/assets/courseware/v1/7b790492a514a8f271956c00064e3c90/asset-v1:LinuxFoundationX+LFS158x+1T2022+type@asset+block/logo-kubeadm.png](https://courses.edx.org/assets/courseware/v1/7b790492a514a8f271956c00064e3c90/asset-v1:LinuxFoundationX+LFS158x+1T2022+type@asset+block/logo-kubeadm.png)

### kubespray

[kubespray](https://kubernetes.io/docs/setup/production-environment/tools/kubespray/) (formerly known as kargo) allows us to install Highly Available production ready Kubernetes clusters on AWS, GCP, Azure, OpenStack, vSphere, or bare metal. kubespray is based on Ansible, and is available on most Linux distributions. It is a [Kubernetes Incubator](https://github.com/kubernetes-sigs/kubespray/) project.

![https://courses.edx.org/assets/courseware/v1/db16a195cf9eb7f4b0d3a3f19f2b09e1/asset-v1:LinuxFoundationX+LFS158x+1T2022+type@asset+block/kubespray-logo-text-clear.png](https://courses.edx.org/assets/courseware/v1/db16a195cf9eb7f4b0d3a3f19f2b09e1/asset-v1:LinuxFoundationX+LFS158x+1T2022+type@asset+block/kubespray-logo-text-clear.png)

### **kops**

[kops](https://kubernetes.io/docs/setup/production-environment/tools/kops/) enables us to create, upgrade, and maintain production-grade, Highly Available Kubernetes clusters from the command line. It can provision the required infrastructure as well. Currently, AWS is officially supported. Support for DigitalOcean and OpenStack is in beta, Azure and GCE is in alpha support, and other platforms are planned for the future. Explore the [kops project](https://github.com/kubernetes/kops/) for more details.

![https://courses.edx.org/assets/courseware/v1/25578d904e75c8bffd298a079b4a3e89/asset-v1:LinuxFoundationX+LFS158x+1T2022+type@asset+block/logo-kops.jpg](https://courses.edx.org/assets/courseware/v1/25578d904e75c8bffd298a079b4a3e89/asset-v1:LinuxFoundationX+LFS158x+1T2022+type@asset+block/logo-kops.jpg)

In addition, for a manual installation approach, the *[Kubernetes The Hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way)* GitHub project by [Kelsey Hightower](https://twitter.com/kelseyhightower) is an extremely helpful installation guide and resource. The project aims to teach all the detailed steps involved in the bootstrapping of a Kubernetes cluster, steps that are otherwise automated by various tools.

These are the most used tools to install Kubernetes in a cloud or bare metal. But there are also many cloud providers whose providers fully manage the provided software stack, while the user pays hosting and management charges. 

Popular vendors providing hosted solutions for Kubernetes are :-

- [Alibaba Cloud Container Service for Kubernetes](https://www.alibabacloud.com/product/kubernetes) (ACK)
- [Amazon Elastic Kubernetes Service](https://aws.amazon.com/eks/) (EKS)
- [Azure Kubernetes Service](https://azure.microsoft.com/en-us/services/kubernetes-service/) (AKS)
- [CIVO]([https://www.civo.com/](https://www.civo.com/))
- [DigitalOcean Kubernetes](https://www.digitalocean.com/products/kubernetes/)
- [Google Kubernetes Engine](https://cloud.google.com/kubernetes-engine/) (GKE)
- [IBM Cloud Kubernetes Service](https://www.ibm.com/cloud/kubernetes-service/)
- [Oracle Cloud Container Engine for Kubernetes](https://www.oracle.com/cloud-native/container-engine-kubernetes/) (OKE)
- [Platform9 Managed Kubernetes](https://platform9.com/managed-kubernetes/) (PMK)
- [Red Hat OpenShift](https://www.redhat.com/en/technologies/cloud-computing/openshift)
- [VMware Tanzu Kubernetes](https://tanzu.vmware.com/kubernetes-grid)

Whatever we have talked about till now it’s mostly for the production environment. So now let’s talk about what we are going to use to practice our k8s skills and for testing purposes. 

## Installing Local Learning Clusters

There are various installation tools allowing us to deploy single- or multi-node Kubernetes clusters on our workstations, for learning and development purposes. While not an exhaustive list, below we enumerate a few popular ones:

- [Minikube](https://minikube.sigs.k8s.io/docs/) Single- and multi-node local Kubernetes cluster, recommended for a learning environment deployed on a single host.
- [Kind](https://kind.sigs.k8s.io/docs/) Multi-node Kubernetes cluster deployed in Docker containers acting as Kubernetes nodes, recommended for a learning environment.
- [Docker Desktop](https://www.docker.com/products/docker-desktop) Including a local Kubernetes cluster for Docker users.
- [MicroK8s](https://microk8s.io/) Local and cloud Kubernetes cluster for developers and production, from Canonical.
- [K3S](https://k3s.io/) Lightweight Kubernetes cluster for local, cloud, edge, IoT deployments, originally from Rancher, currently a CNCF project.
- [K3d](https://k3d.io/v5.4.6/) k3d is a lightweight wrapper to run k3s (Rancher Lab’s minimal Kubernetes distribution) in docker. k3d makes it very easy to create single- and multi-node k3s clusters in docker, e.g. for local development on Kubernetes.

Minikube is an easy and flexible method to create a local Kubernetes setup. We will be using it extensively in this course to manage certain aspects of a Kubernetes cluster while taking advantage of several automated features designed to simplify the user interaction with the Kubernetes environment and the containerized applications deployed to the cluster.

We will be using minikube to install Kubernetes in our local system. You can use any of the above mention tools. 

## Minikube

[Minikube](https://minikube.sigs.k8s.io/) is one of the easiest, most flexible and most popular methods to run an all-in-one or a multi-node local Kubernetes cluster, isolated by Virtual Machines (VM) or Containers, run directly on our workstations. Minikube is the tool responsible for the installation of Kubernetes components, cluster bootstrapping, and cluster tear-down when no longer needed. Minikube can be installed on native macOS, Windows, and many Linux distributions.

However, in order to fully take advantage of all the features, Minikube has to offer, a [Type-2 Hypervisor](https://en.wikipedia.org/wiki/Hypervisor) or a Container Runtime should be installed on the local workstation, to run in conjunction with Minikube. 
Minikube is built on the capabilities of the [libmachine](https://github.com/docker/machine/tree/master/libmachine) the library originally designed by Docker to build [Virtual Machine container hosts](https://github.com/docker/machine) on any physical infrastructure. In time Minikube became very flexible, supporting several hypervisors and container runtimes, depending on the host workstation's native OS.

For a learning environment the recommendations are that a Kubernetes node has 2 CPU cores (or virtual CPUs) at a minimum, at least 2 GB of RAM memory (with 4 - 6 GB of RAM recommended for optimal usage), and 20+ GB of disk storage space.

### ****Requirements for Running Minikube****

- VT-x/AMD-v virtualization must be enabled on the local workstation, and/or verify if it is supported.
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) **kubectl** is a binary used to access and manage any Kubernetes cluster. It is installed through Minikube and accessed through the **minikube** command, or it can be installed separately and run as a standalone tool.
- Type-2 Hypervisor or Container RuntimeWithout a specified driver, Minikube will try to find an installed hypervisor or a runtime, in the following order of preference (on a Linux host): docker, kvm2, podman, vmware, and virtualbox. If multiple isolation software installations are found, such as docker and virtualbox, Minikube will pick docker over virtualbox if no desired driver is specified by the user.
- Internet connection on the first Minikube run - to download packages, dependencies, updates and pull images needed to initialize the Minikube Kubernetes cluster components. Subsequent runs will require an internet connection only when new container images need to be pulled from a public container registry or when deployed containerized applications need it for client accessibility. Once a container image has been pulled it can be reused from the local container runtime image cache without an internet connection.

Now let's go install the minikuber in your local system. I’m a Linux user but don’t worry you can visite the [minikube website](https://minikube.sigs.k8s.io/docs/start/) and flow the steps to download it.

### Installing Minikube on Linux

As of now you already know that minikube runs on Virtual Machines (VM) or Containers, run directly so make sure you have to install Docker or Virtualbox or another tool as per your like. I have already installed the docker in my system because minikube default is docker.

**Step 1** :- Install Minikube. We can download and install in a terminal the latest release or a specific release from the [Minikube release page](https://github.com/kubernetes/minikube/releases):
```
$ curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
```
```
$ sudo dpkg -i minikube_latest_amd64.deb
```
> ***NOTE**: Replacing **/latest/** with a particular version, such as **/v1.24.0/** will download that specified Minikube version.

**Step 2**:- Start Minikube. In a terminal, we can start Minikube with the **minikube start** command, which bootstraps a single-node cluster with the latest stable Kubernetes version release. For a specific Kubernetes version the **--Kubernetes-version** option can be used as such **minikube start --Kubernetes-version v1.22.0** (where **latest** is default and acceptable version value and **stable** is also acceptable). More advanced start options will be explored later in this chapter:
```
$ minikube start

😄  minikube v1.25.2 on Ubuntu 20.04
✨  Automatically selected the VirtualBox driver
💿  Downloading VM boot image ...    
               > minikube-v1.25.2.iso.sha256: 65 B / 65 B [-------------] 100.00% ? p/s 0s    
               > minikube-v1.25.2.iso: 237.06 MiB / 237.06 MiB [] 100.00% 9.11 MiB p/s 26s
👍  Starting control plane node minikube in cluster minikube
💾  Downloading Kubernetes v1.23.3 preload ...    
               > preloaded-images-k8s-v17-v1...: 505.68 MiB / 505.68 MiB  100.00% 8.52 MiB
🔥  Creating VirtualBox VM (CPUs=2, Memory=6000MB, Disk=20000MB) ...
🐳  Preparing Kubernetes v1.23.3 on Docker 20.10.12 ...    
               ▪ kubelet.housekeeping-interval=5m    
               ▪ Generating certificates and keys ...    
               ▪ Booting up the control plane ...    
               ▪ Configuring RBAC rules ...
🔎  Verifying Kubernetes components...    
               ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5
🌟  Enabled addons: default-storageclass, storage-provisioner
💡  kubectl not found. If you need it, try: 'minikube kubectl -- get pods -A'
🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
```

> ***NOTE**: An error message that reads "Unable to pick a default driver..." means that Minikube was not able to locate any one of the supported hypervisors or runtimes. The recommendation is to install or re-install the desired isolation tool and ensure its executable is found in the default **PATH** of your OS distribution.

### Some Command to use Minikube
#### minikube status 
Check the status, we can display the status of the Minikube cluster
```
$ minikube status

minikubetype: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured
```
#### minikube stop
To stop the minikube cluster 
```
$ minikube stop

✋  Stopping node "minikube"  ...🛑  1 node stopped
```
#### minikube version
To display the version of the current Minikube installation:
```
$ minikube version

minikube version: v1.25.2
commit: 362d5fdc0a3dbee389b3d3f1034e8023e72bd3a7
```
#### minikube IP addres
To display the cluster control plane node's IP address, or another node's IP with the **--node** or **-n** flags:
```
$ minikube IP

192.168.59.100
```
```
$ minikube -p minibox ip

192.168.59.101
```
```
$ minikube -p minibox ip -n minibox-m02

192.168.59.102
```
#### minikube delete
When a cluster configuration is no longer in use, the cluster's profile can be deleted. It is also a profile-aware command - it deletes the default **minikube** cluster if no profile is specified, or a custom cluster if its profile is specified:
```
$ minikube delete

🔥  Deleting "minikube" in VirtualBox ...
💀  Removed all traces of the "minikube" cluster.
```
```
$ minikube delete -p minibox

🔥  Deleting "minibox" in VirtualBox ...
🔥  Deleting "minibox-m02" in VirtualBox ...
🔥  Deleting "minibox-m03" in VirtualBox ...
💀  Removed all traces of the "minibox" cluster.
```

>That’s all you need to do to install the minikube in your local system. Now use the kubectl command to perform any task you like. if in some cases your kubectl is not installed you can install it just visit this [kubectl page](https://minikube.sigs.k8s.io/docs/handbook/kubectl/).

These are the basic command you will be used to very often. so get used to it.

That’s all for today I hope you liked it. If yes then please do share and stay tuned for my next blog which comes every Sunday and Thursday.

My upcoming blog is on minikube too we will go a little deep into minikube and learn how to use it like a pro.