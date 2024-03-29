## Kubernetes Introduction

In this Bolg, we describe **Kubernetes**, its features, and the reasons why you should use it. We will explore the evolution of Kubernetes.

We will also learn about the **Cloud Native Computing Foundation (CNCF)**, which currently hosts the Kubernetes project, along with other popular cloud-native projects, such as Prometheus, Fluentd, cri-o, containerd, Helm, Envoy, and Contour, just to name a few.

# ****What Is Kubernetes?****

According to the [Kubernetes](https://kubernetes.io/) website,

> *"Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications"*.

**Kubernetes** comes from the Greek word **κυβερνήτης**, which means *helmsman* or *ship pilot*. With this analogy in mind, we can think of Kubernetes as the pilot on a ship of containers.


![image.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1662622031464/MhB5tm0Z-.jpg align="left")

Kubernetes is also referred to as **k8s** (pronounced Kate's), as there are 8 characters between *k* and *s*.

Kubernetes is highly inspired by the Google Borg system, a container and workload orchestrator for its global operations for more than a decade. It is an open-source project written in the Go language and licensed under the [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0).

Kubernetes was started by Google and, with its v1.0 release in July 2015, Google donated it to the [Cloud Native Computing Foundation](https://www.cncf.io/) (CNCF), one of the largest sub-foundations of the [Linux Foundation](https://linuxfoundation.org/).

# ****From Borg to Kubernetes****

According to the abstract of Google's [Borg paper](https://research.google.com/pubs/pub43438.html), published in 2015,

> *"Google's Borg system is a cluster manager that runs hundreds of thousands of jobs, from many thousands of different applications, across a number of clusters each with up to tens of thousands of machines".*

For more than a decade, Borg has been Google's secret, running its worldwide containerized workloads in production. Services we use from Google, such as Gmail, Drive, Maps, Docs, etc., are all serviced using Borg.

Among the initial authors of Kubernetes were Google employees who have used Borg and developed it in the past. They poured in their valuable knowledge and experience while designing Kubernetes. Several features/objects of Kubernetes that can be traced back to Borg, or to lessons learned from it, are:

- API servers
- Pods
- IP-per-Pod
- Services
- Labels.

# ****Kubernetes Features****

Kubernetes offers a very rich set of features for container orchestration. Some of its fully supported features are:

- **Automatic bin packing**Kubernetes automatically schedules containers based on resource needs and constraints, to maximize utilization without sacrificing availability.
- **Designed for extensibility**A Kubernetes cluster can be extended with new custom features without modifying the upstream source code.
- **Self-healing**Kubernetes automatically replaces and reschedules containers from failed nodes. It terminates and then restarts containers that become unresponsive to health checks, based on existing rules/policy. It also prevents traffic from being routed to unresponsive containers.
- **Horizontal scaling**With Kubernetes applications are scaled manually or automatically based on CPU or custom metrics utilization.
- **Service discovery and load balancing**Containers receive IP addresses from Kubernetes, while it assigns a single Domain Name System (DNS) name to a set of containers to aid in load-balancing requests across the containers of the set.

Additional fully supported Kubernetes features are:

- **Automated rollouts and rollbacks**Kubernetes seamlessly rolls out and rolls back application updates and configuration changes, constantly monitoring the application's health to prevent any downtime.
- **Secret and configuration management**Kubernetes manages sensitive data and configuration details for an application separately from the container image, in order to avoid a re-build of the respective image. Secrets consist of sensitive/confidential information passed to the application without revealing the sensitive content to the stack configuration, like on GitHub.
- **Storage orchestration**Kubernetes automatically mounts software-defined storage (SDS) solutions to containers from local storage, external cloud providers, distributed storage, or network storage systems.
- **Batch execution**Kubernetes supports batch execution, and long-running jobs, and replaces failed containers.
- **IPv4/IPv6 dual-stack**Kubernetes supports both IPv4 and IPv6 addresses.

# ****Why Use Kubernetes?****

Another one of Kubernetes' strengths is portability. It can be deployed in many environments such as local or remote Virtual Machines, bare metal, or in public/private/hybrid/multi-cloud setups.

Kubernetes extensibility allows it to support and to be supported by many 3rd party open-source tools which enhance Kubernetes' capabilities and provide a feature-rich experience to its users. Its architecture is modular and pluggable. Not only that it orchestrates modular, decoupled microservices-type applications, but also its architecture follows decoupled microservices patterns. Kubernetes' functionality can be extended by writing custom resources, operators, custom APIs, scheduling rules or plugins.

For a successful open-source project, the community is as important as having great code. Kubernetes is supported by a thriving community across the world. It has more than 3,236 contributors, who, over time, have pushed over 106,000 commits. There are meet-up groups in different cities and countries which meet regularly to discuss Kubernetes and its ecosystem. The community is divided into *Special Interest Groups* (SIGs), groups which focus on special topics, such as scaling, bare metal, networking, storage, etc. We will learn more about them in our last chapter, *Kubernetes Community*.

# ****Kubernetes Architecture****

At a very high level, Kubernetes is a cluster of compute systems categorized by their distinct roles:

- One or more **control plane** nodes
- One or more **worker** nodes 


![kA.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1662622730328/0_ov0eBCN.jpg align="left")

## Control Plane Node Components

A control plane node runs the following essential control plane components and agents:

- API Server
- Scheduler
- Controller Managers
- Key-Value Data Store.

In addition, the control plane node runs:

- Container Runtime
- Node Agent
- Proxy
- Optional add-ons for cluster-level monitoring and logging.

## Worker Node Components

A worker node has the following components:

- Container Runtime
- Node Agent - kubelet
- Proxy - kube-proxy
- Addons for DNS, Dashboard user interface, cluster-level monitoring and logging.


That's all, for now, today I know it's a small blog but if have started explaining the Kubernetes Architecture the blog will be very long. So my next blog is on **Kubernetes Architecture** 
We will talk about the components of the **Worker Node** and **Control Plane** In detail.
So Please stay tuned.