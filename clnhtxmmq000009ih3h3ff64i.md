---
title: "Azure Kubernetes Service (AKS)"
seoTitle: "Benefits of AKS"
datePublished: Sun Oct 08 2023 19:00:42 GMT+0000 (Coordinated Universal Time)
cuid: clnhtxmmq000009ih3h3ff64i
slug: aks
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696551081822/33111d6d-2098-4464-8b40-ba81a98f1d02.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1696551099189/b56fe2e9-7f82-432b-9579-4099a51cfd78.png
tags: kubernetes, devops, containerization, aks, cost-optimisation

---

Welcome to our latest blog post, where we delve into the world of Azure Kubernetes Service. Whether you're new to Kubernetes or a seasoned pro, this guide will equip you with why we need AKS files. Let's get started!

## **What is Azure Kubernetes Service (AKS)?**

Azure Kubernetes Service is a managed container orchestration service based on the open-source Kubernetes system, which is available on the [Microsoft Azure public cloud](https://www.techtarget.com/searchcloudcomputing/definition/Windows-Azure). An organization can use AKS to handle critical functionality such as deploying, scaling and managing Docker containers and container-based applications.

[Kubernetes](https://www.techtarget.com/searchitoperations/definition/Google-Kubernetes) is the de-facto open-source platform for container orchestration but typically requires a lot of overhead in cluster management. AKS helps manage much of the overhead involved, reducing the complexity of deployment and management tasks. AKS is designed for organizations that want to build scalable applications with [Docker](https://www.techtarget.com/searchitoperations/definition/Docker) and Kubernetes while using the Azure architecture.

An AKS cluster can be created using the Azure command-line interface (CLI), an Azure portal or Azure PowerShell. Users can also create template-driven deployment options with Azure Resource Manager templates.

## **AKS features and benefits**

The primary benefits of AKS are flexibility, automation and reduced management overhead for administrators and developers. For example, AKS automatically configures all of the Kubernetes [nodes](https://www.techtarget.com/searchitoperations/definition/Kubernetes-Node) that control and manage the worker nodes during the deployment process and handles a range of other tasks, including Azure Active Directory ([AD](https://www.techtarget.com/searchwindowsserver/definition/Microsoft-Windows-Azure-Active-Directory-Windows-Azure-AD)) integration, connections to monitoring services and configuration of advanced networking features such as HTTP application routing. Users can monitor a cluster directly or view all clusters with Azure Monitor.

Because AKS is a managed service, Microsoft handles all Kubernetes upgrades for the service as new versions become available. Users can decide whether and when to upgrade the Kubernetes version in their own AKS cluster to reduce the possibility of accidental workload disruption.

AKS integrates with Azure AD to provide role-based access control ([RBAC](https://www.techtarget.com/searchsecurity/definition/role-based-access-control-RBAC)) for security and monitoring of Kubernetes architecture.

AKS also enables users to create and modify custom tags for AKS resources created by end users.

## **The architecture of AKS**

When a user creates an AKS cluster, a [control plane](https://www.techtarget.com/searchnetworking/definition/control-plane-CP) is automatically created and configured. The control plane is a managed Azure resource the user cannot access directly. The control plane contains resources that:

* provide interaction for management tools;
    
* maintain the state and configuration of the Kubernetes cluster;
    
* schedule and specify which nodes run the workload; and
    
* oversee smaller actions, such as replicating [Kubernetes pods](https://www.techtarget.com/searchitoperations/definition/Kubernetes-Pod) or handling node operations.
    

The user defines the size and number of nodes, and the Azure platform configures secure communication between the nodes and the control plane.

An AKS cluster has at least one node. The central processing unit and memory are the node resources used to help the node function as part of a cluster. Nodes with similar configurations are grouped together into node pools.

AKS deployments also cover two resource groups. One group is only the Kubernetes service resource, while the other is the node resource group. The node resource group contains all of the infrastructure resources associated with the cluster. A service principal or managed identity is needed to create and manage other Azure resources.

## **AKS security, monitoring and compliance**

AKS supports RBAC through Azure Active Directory, which enables an administrator to tailor Kubernetes access to AD identity and group associations. Admins can monitor container health using processor and memory metrics collected from containers, Kubernetes nodes and other points in the infrastructure. Container logs are also collected and stored for more detailed analytics and troubleshooting. Monitoring data is available through the AKS management portal, AKS CLI and application programming interfaces ([APIs](https://www.techtarget.com/searchapparchitecture/definition/application-program-interface-API)).

AKS meets the regulatory requirements of System and Organization Controls and is compliant with major regulatory bodies, including the International Organization for Standardization, the Health Insurance Portability and Accountability Act and the Health Information Trust Alliance. AKS is also certified as Kubernetes conformant by the [Cloud Native Computing Foundation](https://www.techtarget.com/searchitoperations/definition/Cloud-Native-Computing-Foundation-CNCF), which oversees open-source Kubernetes.

If an AKS cluster is created or scaled up, the nodes are automatically deployed with the most recent security updates. Azure will also automatically apply operating system (OS) security patches to Linux-based nodes; however, Windows Server nodes do not automatically apply the most recent updates.

## **AKS availability and costs**

AKS is a free Azure service, so there is no charge for Kubernetes cluster management. AKS users are, however, billed for the underlying compute, storage, networking and other cloud resources consumed by the containers that comprise the application running within the Kubernetes cluster.

AKS is currently [available in numerous regions](https://docs.microsoft.com/en-us/azure/aks/availability-zones), including Eastern, Central and Western U.S.; Central Canada; Northern and Western Europe; and Southeast Asia. Other regions will be added over time.

# THE END

That is all for today we learned a lot today if you have any questions please let me I will answer that. One more suggestion please write down those commands on a piece of paper that will be always on your table so that whenever you need it you can refer from that.