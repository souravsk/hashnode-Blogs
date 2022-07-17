## KubeSphere for cloud-native Application Management

# In the Simplest way what is KubeSphere?
KubeSphere is a distributed operating system for cloud-native application management, using Kubernetes as its kernel. It provides a plug-and-play architecture, allowing third-party applications to be seamlessly integrated into its ecosystem.

So KubeSphere is an application which manages other cloud-native applications which makes your life as a DevOps extremely easy you don't have to hassle much with different other applications you just need one to manage and that is KubeShpere. It has a User-friendly UI for the developers helping enterprises to build out a robust and feature-rich platform.

KubeSphere also represents a multi-tenant enterprise-grade Kubernetes container platform with full-stack automated IT operations and streamlined DevOps workflows.


![kubesphere-ecosystem.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652788935705/05c4s8ZRZ.png align="left")

As you can see in the above picture the different services can be managed by KubeSphere. You can handle all these services in one place. you just in to have the basic hardware required so that it can be installed in your OS or in your cloud providers like CIVO, AWS, Google Cloud, etc.

# Features

As an open-source container platform, KubeSphere provides enterprises with a robust, secure and feature-rich platform, boasting the most common functionalities needed for enterprises adopting Kubernetes, such as multi-cluster deployment and management, network policy configuration, Service Mesh (Istio-based), DevOps projects (CI/CD), security management, Source-to-Image and Binary-to-Image, multi-tenant management, multi-dimensional monitoring, log query and collection, alerting and notification, auditing, application management, and image registry management.
With an easy-to-use web console in place, KubeSphere eases the learning curve for users and drives the adoption of Kubernetes.

![20200202153355.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652789452265/pFwj7AI0B.png align="left")

## Multi-cluster Management and Deployment
As in the world of cloud-native applications to deploy their clusters across locations, geographies, and clouds. KubeSphere has addressed the pressure on the user and introduced the multi-cluster feature.

Now KubeSphere, users can manage the infrastructure underneath, such as adding or deleting clusters.KubeSphere, users can manage the infrastructure underneath, such as adding or deleting clusters. clusters deployed on any infrastructure (for example, Amazon EKS and Google Kubernetes Engine) can be managed in a unified way. KubeSphere allows users to deploy applications across clusters. More importantly, an application can also be configured to run on a certain cluster.

## DevOps Support
KubeSphere provides a pluggable DevOps component based on popular CI/CD tools such as Jenkins. It features automated workflows and tools including binary-to-image (B2I) and source-to-image (S2I) to package source code or binary artefacts into ready-to-run container images.

![1_SM9eso5vp_9kxwezuYAYWQ.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652790750457/H-0LaKfgR.png align="left")

## Application Management and Orchestration
- **App Store:- **KubeSphere provides an app store based on OpenPitrix, an industry-leading open-source system for app management across the whole lifecycle, including release, removal, and distribution.
- **App repository:-**  In KubeSphere, users can create an app repository hosted either in object storage (such as QingStor or AWS S3) or in GitHub. App packages submitted to the app repository are composed of Helm Chart template files of the app.
- **App template:-**  With app templates, KubeSphere provides a visualized way for app deployment with just one click. Internally, app templates can help different teams in the enterprise to share middleware and business systems. Externally, they can serve as an industry standard for application delivery based on different scenarios and needs.

## Multiple Storage Solutions
- Open-source storage solutions are available such as GlusterFS, CephRBD, and NFS.
- NeonSAN CSI plugin connects to QingStor NeonSAN to meet core business requirements for low latency, high resilience, and high performance.
- QingCloud CSI plugin connects to various block storage services in the QingCloud platform.

## Multiple Network Solutions
Open source network solutions are available such as Calico and Flannel.

OpenELB, a load balancer developed for bare metal Kubernetes clusters, is designed by the KubeSphere development team. This CNCF-certified tool serves as an important solution for developers

# Architecture

KubeSphere separates the frontend from the backend, and it itself is a cloud-native application and provides open standard REST APIs for external systems to use. Please see the API documentation for details. The following figure is the system architecture. KubeSphere can run anywhere from an on-premise data centre to any cloud to edge. In addition, it can be deployed on any Kubernetes distribution.


![20190810073322.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652807605589/ubabvVr8s.png align="left")

# Installation


## KubeKey
KubeKey is developed by the team of KubeSphere for brand new installation. KubeKey will help enterprises quickly set up a Kubernetes cluster on public clouds or data centres. It provides users with different installation options such as all-in-one installation and multi-node installation. It is also an efficient tool to install cloud-native add-ons and upgrade and scale your Kubernetes cluster.


## Setp 1:- System requirements
To get started with an all-in-one installation, you only need to prepare one host according to the following requirements for hardware and operating system. 
### Hardware Requirements

Linux (any latest OS) - 	2 CPU cores, 4 GB memory, and 40 GB disk space

> You need to have these minimum system requirements so that you can run Kubesphere otherwise you won't able to run it.

### Container
Your cluster must have an available container runtime. If you use KubeKey to set up a cluster, KubeKey installs the latest version of Docker by default. Alternatively, you can manually install Docker or other container runtimes before you create a cluster

> To deploy KubeSphere in an offline environment, you must install a container runtime in advance.

### Dependency requirements
KubeKey can install Kubernetes and KubeSphere together. The dependency that needs to be installed may be different based on the Kubernetes version to be installed. So it is better to install with KubeKey it will install the all basic required software.

### Network and DNS requirements
- Make sure the DNS address in /etc/resolv.conf is available. Otherwise, it may cause some issues of DNS in the cluster.
- If your network configuration uses firewall rules or security groups, you must ensure infrastructure components can communicate with each other through specific ports. It is recommended that you turn off the firewall.
- Supported CNI plugins: Calico and Flannel. Others (such as Cilium and Kube-OVN) may also work but note that they have not been fully tested.

## Step 2:- Download KubeKey
Download KubeKey from its [GitHub Release Page](https://github.com/kubesphere/kubekey/releases) or run the following command:

```
curl -sfL https://get-kk.kubesphere.io | VERSION=v2.0.0 sh -

``` 
> Make sure your internet connection is good and the commands above download the latest release of KubeKey. You can change the version number in the command to download a specific version.

## Step 3: Get Started with Installation
You only need to run one command for all-in-one installation. The template is as follows:

```
./kk create cluster [--with-kubernetes version] [--with-kubesphere version]

``` 
To create a Kubernetes cluster with KubeSphere installed, refer to the following command as an example:

```
./kk create cluster --with-kubernetes v1.21.5 --with-kubesphere v3.2.1

``` 
After you run the command, you will see a table for environment check. Type yes to continue.

## Step 4: Verify the Installation
If the following information is displayed, Kubernetes and KubeSphere are successfully installed.

![Installation-complete.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652787874565/akzV1wuWx.png align="left")

Run the following command to check the result.

```
kubectl logs -n kubesphere-system $(kubectl get pod -n kubesphere-system -l app=ks-install -o jsonpath='{.items[0].metadata.name}') -f

``` 
The output displays the IP address and port number of the web console, which is exposed through NodePort 30880 by default. Now, you can access the console at <NodeIP>:30880 with the default account and password (admin/P@88w0rd).


```
#####################################################
###              Welcome to KubeSphere!           ###
#####################################################

Console: http://192.168.0.2:30880
Account: admin
Password: P@88w0rd

NOTES：
  1. After you log into the console, please check the
     monitoring status of service components in
     "Cluster Management". If any service is not
     ready, please wait patiently until all components 
     are up and running.
  2. Please change the default password after login in.

#####################################################
https://kubesphere.io             20xx-xx-xx xx:xx:xx
#####################################################

``` 
> You may need to configure port forwarding rules and open the port in your security group so that external users can access the console.

After logging in to the console, you can check the status of different components in System Components. You may need to wait for some components to be up and running if you want to use related services. You can also use *kubectl get pod --all-namespaces* to inspect the running status of KubeSphere workloads.

So in most real-life Projects, the KubeSphere is installed in a cloud provider like CIVO, AWS, Google Cloud, Azure, etc. 


Thank You for Reading. Please go and explore more about KubeSphere








