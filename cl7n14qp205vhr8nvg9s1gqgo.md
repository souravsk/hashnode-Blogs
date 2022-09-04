## Container Orchestrator

# Container Orchestrator

Container images allow us to confine the application code, its runtime, and all of its dependencies in a pre-defined format. The container runtimes like **runC**, **contained** or **cri-o**
 can use pre-packaged images as a source to create and run one or more containers. These runtimes are capable of running containers on a single host, however, in practice, we would like to have a fault-tolerant and scalable solution, achieved by building a single **controller**
/**management unit**, a collection of multiple hosts connected together. This controller/management  unit is generally referred to as a **container orchestrator**
.

# what are containers?

Before we dive into container orchestration, let's review first what containers are.

**Containers** are an application-centric method to deliver high-performing, scalable applications on any infrastructure of your choice. Containers are best suited to deliver microservices by providing portable, isolated virtual environments for applications to run without interference from other running applications.

# Container Deployment

**Microservices** are lightweight applications written in various modern programming languages, with specific dependencies, libraries and environmental requirements. To ensure that an application has everything it needs to run successfully it is packaged together with its dependencies.

Containers encapsulate microservices and their dependencies but do not run them directly. Containers run container images.

A **container image** bundles the application along with its runtime, libraries, and dependencies, and it represents the source of a container deployed to offer an isolated executable environment for the application. Containers can be deployed from a specific image on many platforms, such as workstations, Virtual Machines, public clouds, etc.

# What Is Container Orchestration?

In Development (Dev) environments, running containers on a single host for the development and testing of applications may be a suitable option.**Container orchestrators**
 are tools that group systems together to form clusters where containers' deployment and management are automated at scale while meeting the requirements mentioned

# Container Orchestrators

With enterprises containerizing their applications and moving them to the cloud, there is a growing demand for container orchestration solutions. While there are many solutions available, some are mere re-distributions of well-established container orchestration tools, enriched with features and, sometimes, with certain limitations in flexibility.

Although not exhaustive, the list below provides a few different container orchestration tools and services available today:

- **Amazon Elastic Container Service**[Amazon Elastic Container Service](https://aws.amazon.com/ecs/) (ECS) is a hosted service provided by [Amazon Web Services](https://aws.amazon.com/) (AWS) to run containers at scale on its infrastructure.
- **Azure Container Instances**[Azure Container Instance](https://azure.microsoft.com/en-us/services/container-instances/) (ACI) is a basic container orchestration service provided by [Microsoft Azure](https://azure.microsoft.com/en-us/).
- **Azure Service Fabric**[Azure Service Fabric](https://azure.microsoft.com/en-us/services/service-fabric/) is an open-source container orchestrator provided by [Microsoft Azure](https://azure.microsoft.com/en-us/).
- **Kubernetes**[Kubernetes](https://kubernetes.io/) is an open-source orchestration tool, originally started by Google, today part of the [Cloud Native Computing Foundation](https://www.cncf.io/) (CNCF) project.
- **Marathon**[Marathon](https://mesosphere.github.io/marathon/) is a framework to run containers at scale on [Apache Mesos](https://mesos.apache.org/) and [DC/OS](https://dcos.io/).
- **Nomad**[Nomad](https://www.nomadproject.io/) is the container and workload orchestrator provided by [HashiCorp](https://www.hashicorp.com/).
- **Docker Swarm**[Docker Swarm](https://docs.docker.com/engine/swarm/) is a container orchestrator provided by [Docker, Inc](https://www.docker.com/). It is part of [Docker Engine](https://docs.docker.com/engine/).

# ****Why Use Container Orchestrators?****

Although we can manually maintain a couple of containers or write scripts to manage the lifecycle of dozens of containers, orchestrators make things much easier for users especially when it comes to managing hundreds and thousands of containers running on a global infrastructure.

Most container orchestrators can:

- Group hosts together while creating a cluster
- Schedule containers to run on hosts in the cluster based on resources availability
- Enable containers in a cluster to communicate with each other regardless of the host they are deployed to in the cluster
- Bind containers and storage resources
- Group sets of similar containers and bind them to load-balancing constructs to simplify access to containerized applications by creating an interface, a level of abstraction between the containers and the client
- Manage and optimize resource usage
- Allow for implementation of policies to secure access to applications running inside containers.

With all these configurable yet flexible features, container orchestrators are an obvious choice when it comes to managing containerized applications at scale. In this course, we will explore **Kubernetes**, one of the most in-demand container orchestration tools available today.

# ****Where to Deploy Container Orchestrators?****

Most container orchestrators can be deployed on the infrastructure of our choice - on bare metal, Virtual Machines, on-premises, on public and hybrid cloud. Kubernetes, for example, can be deployed on a workstation, with or without an isolation layer such as a local hypervisor or container runtime, inside a company's data centre, in the cloud on AWS Elastic Compute Cloud (EC2) instances, Google Compute Engine (GCE) VMs, DigitalOcean Droplets, OpenStack, etc.

There are turnkey solutions which allow Kubernetes clusters to be installed, with only a few commands, on top of cloud Infrastructures-as-a-Service, such as GCE, AWS EC2, Docker Enterprise, IBM Cloud, Rancher, VMware Tanzu, and multi-cloud solutions through IBM Cloud Private or StackPointCloud.

Last but not least, there is the managed container orchestration as-a-Service, more specifically the managed Kubernetes as-a-Service solution, offered and hosted by the major cloud providers, such as:-

- [CIVO Cloud](https://www.civo.com/) (CIVO)

- [Amazon Elastic Kubernetes Service](https://aws.amazon.com/eks/) (Amazon EKS)

- [Azure Kubernetes Service](https://azure.microsoft.com/en-us/services/kubernetes-service/) (AKS)

- [DigitalOcean Kubernetes](https://www.digitalocean.com/products/kubernetes/)

- [Google Kubernetes Engine](https://cloud.google.com/kubernetes-engine/) (GKE)

- [IBM Cloud Kubernetes Service](https://www.ibm.com/cloud/kubernetes-service)

- [Oracle Container Engine for Kubernetes](https://www.oracle.com/cloud-native/container-engine-kubernetes/) 

- [VMware Tanzu Kubernetes Grid](https://tanzu.vmware.com/kubernetes-grid). 

# Conclusion
Container orchestration automates the provisioning, deployment, networking, scaling, availability, and lifecycle management of containers. Today, Kubernetes is the most popular container orchestration platform and most leading public cloud provider.

Kubernetes is the most popular container orchestration platform. Together with other tools in the container ecosystem, Kubernetes enables a company to deliver a highly productive platform-as-a-service (PaaS) that addresses many of the infrastructures- and operations-related tasks and issues around cloud-native application development, so that development teams can focus exclusively on coding and innovation.

Thank You for Reading my next blog is on Kubernetes so Say Tune in for that one.