# Here are some advanced topics related to Kubernetes that you should know about

So far, in this Kubernetes series, we have spent most of our time understanding the basic Kubernetes concepts and simple workflows to build a solid foundation.

To support enterprise-class production workloads, Kubernetes also supports multi-node pod controllers, stateful application controllers, batch controllers, auto-scaling, resource and quota management, package management, security contexts, network and security policies, etc. In this Blog, we will briefly cover a limited number of such advanced topics, since diving into specifics would be out of scope for this course.

# Annotations

With [Annotations](https://kubernetes.io/docs/concepts/overview/working-with-objects/annotations/), we can attach arbitrary non-identifying metadata to any objects, in a key-value format:
```
"annotations": {
  "key1" : "value1",
  "key2" : "value2"
}
```
Unlike Labels, annotations are not used to identify and select objects. Annotations can be used to:

- Store build/release IDs, PR numbers, git branch, etc.
- Phone/pager numbers of people responsible, or directory entries specifying where such information can be found.
- Pointers to logging, monitoring, analytics, audit repositories, debugging tools, etc.
- Ingress controller information.
- Deployment state and revision information.

For example, while creating a Deployment, we can add a description as seen below:
```
apiVersion: apps/v1
kind: Deployment
metadata:
     name: webserver
     annotations:
         description: Deployment based PoC dates 2nd Mar'2022
....
```
Annotations are displayed while describing an object:
```
$ kubectl describe deployment webserver

Name:                          webserver
Namespace:                default
CreationTimestamp:   Fri, 25 Mar 2022 05:10:38 +0530
Labels:                         app=webserver
Annotations:               deployment.kubernetes.io/revision=1
                                    description=Deployment based PoC dates 2nd Mar'2022
...
```
# Quota and Limits Management

When there are many users sharing a given Kubernetes cluster, there is always a concern for fair usage. A user should not take undue advantage. To address this concern, administrators can use the [ResourceQuota](https://kubernetes.io/docs/concepts/policy/resource-quotas/) API resource, which provides constraints that limit aggregate resource consumption per Namespace.

We can set the following types of quotas per Namespace:

- **Compute Resource Quota**We can limit the total sum of compute resources (CPU, memory, etc.) that can be requested in a given Namespace.

- **Storage Resource Quota**We can limit the total sum of storage resources (PersistentVolumeClaims, requests.storage, etc.) that can be requested.\

- **Object Count Quota**We can restrict the number of objects of a given type (pods, ConfigMaps, PersistentVolumeClaims, ReplicationControllers, Services, Secrets, etc.).

An additional resource that helps limit resources allocation to pods and containers in a namespace, is the [LimitRange](https://kubernetes.io/docs/concepts/policy/limit-range/), used in conjunction with the ResourceQuota API resource. A LimitRange can:

- Set compute resources usage limits per Pod or Container in a namespace.
- Set storage request limits per PersistentVolumeClaim in a namespace.
- Set a request to limit ratio for a resource in a namespace.
- Set default requests and limits and automatically inject them into Containers' environments at runtime.

# Autoscaling

While it is fairly easy to manually scale a few Kubernetes objects, this may not be a practical solution for a production-ready cluster where hundreds or thousands of objects are deployed. We need a dynamic scaling solution which adds or removes objects from the cluster based on resource utilization, availability, and requirements.

Autoscaling can be implemented in a Kubernetes cluster via controllers which periodically adjust the number of running objects based on single, multiple, or custom metrics. There are various types of autoscale available in Kubernetes which can be implemented individually or combined for a more robust autoscaling solution:

- **[Horizontal Pod Autoscaler (HPA)](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/)**HPA is an algorithm-based controller [API resource](https://github.com/kubernetes/community/blob/master/contributors/design-proposals/autoscaling/horizontal-pod-autoscaler.md#horizontalpodautoscaler-object) which automatically adjusts the number of replicas in a ReplicaSet, Deployment or Replication Controller based on CPU utilization.

- **[Vertical Pod Autoscaler (VPA)](https://github.com/kubernetes/autoscaler/tree/master/vertical-pod-autoscaler#readme)**VPA automatically sets Container resource requirements (CPU and memory) in a Pod and dynamically adjusts them in runtime, based on historical utilization data, current resource availability and real-time events.

- **[Cluster Autoscaler](https://github.com/kubernetes/autoscaler/tree/master/cluster-autoscaler#cluster-autoscaler)**Cluster Autoscaler automatically [re-sizes the Kubernetes cluster](https://github.com/kubernetes/autoscaler/blob/master/cluster-autoscaler/FAQ.md) when there are insufficient resources available for new Pods expecting to be scheduled or when there are underutilized nodes in the cluster.

# Jobs and CronJobs

A [Job](https://kubernetes.io/docs/concepts/workloads/controllers/jobs-run-to-completion/) creates one or more Pods to perform a given task. The Job object takes responsibility of Pod failures. It makes sure that the given task is completed successfully. Once the task is complete, all the Pods have terminated automatically. Job configuration options include:

- **parallelism** - to set the number of pods allowed to run in parallel;
- **completions** - to set the number of expected completions;
- **activeDeadlineSeconds** - to set the duration of the Job;
- **backoffLimit** - to set the number of retries before Job is marked as failed;
- **ttlSecondsAfterFinished** - to delay the clean up of the finished Jobs.

Starting with the Kubernetes 1.4 release, we can also perform Jobs at scheduled times/dates with [CronJobs](https://kubernetes.io/docs/tasks/job/automated-tasks-with-cron-jobs/), where a new Job object is created about once per each execution cycle. The CronJob configuration options include:

- **startingDeadlineSeconds** - to set the deadline to start a Job if scheduled time was missed;
- **concurrencyPolicy** - to *allow* or *forbid* concurrent Jobs or to *replace* old Jobs with new ones.

# StatefulSets

The [StatefulSet](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/) controller is used for stateful applications which require a unique identity, such as name, network identifications, or strict ordering. For example, **MySQL cluster**, **etcd cluster**.

The **StatefulSet** controller provides identity and guaranteed to order of deployment and scaling to Pods. However, the StatefulSet controller has very strict Service and Storage Volume dependencies that make it challenging to configure and deploy. It also supports scaling, rolling updates, and rollbacks.

# Custom Resources

In Kubernetes, a **resource** is an API endpoint that stores a collection of API objects. For example, a Pod resource contains all the Pod objects. Although in most cases existing Kubernetes resources are sufficient to fulfil our requirements, we can also create new resources using **custom resources**. With custom resources, we don't have to modify the Kubernetes source. Custom resources are dynamic in nature, and they can appear and disappear in an already-running cluster at any time. To make a resource declarative, we must create and install a **custom controller**, which can interpret the resource structure and perform the required actions. Custom controllers can be deployed and managed in an already running cluster. 
There are two ways to add custom resources:

- **[Custom Resource Definitions (CRDs)](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/)**This is the easiest way to add custom resources and it does not require any programming knowledge. However, building the custom controller would require some programming. 

- **[API Aggregation](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/apiserver-aggregation/)**For more fine-grained control, we can write API Aggregators. They are subordinate API services which sit behind the primary API Server. The primary API Server acts as a proxy for all incoming API requests - it handles the ones based on its capabilities and proxies over the other requests meant for the subordinate API services.

# Kubernetes Federation

With [Kubernetes Cluster Federation](https://github.com/kubernetes-sigs/kubefed/blob/master/README.md) we can manage multiple Kubernetes clusters from a single control plane. We can sync resources across the federated clusters and have cross-cluster discovery. This allows us to perform Deployments across regions, access them using a global DNS record, and achieve High Availability.

Although still a Beta feature, the Federation is very useful when we want to build a hybrid solution, with one cluster running inside our private data center and another one in the public cloud, allowing us to avoid provider lock-in. We can also assign weights for each cluster in the Federation, to distribute the load based on custom rules.

# Security Contexts, Pod Security Policies, and Pod Security Admission

At times we need to define specific privileges and access control settings for Pods and Containers. [Security Contexts](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/) allow us to set Discretionary Access Control for object access permissions, privileged running, capabilities, security labels, etc. However, their effect is limited to the individual Pods and Containers where such context configuration settings are incorporated in the **spec** section.

In order to apply security settings to multiple Pods and Containers cluster-wide, we can define [Pod Security Policies](https://kubernetes.io/docs/concepts/policy/pod-security-policy/) (PSP). They allow more fine-grained security settings to control the usage of the host namespace, host networking and ports, file system groups, usage of volume types, enforce Container user and group ID, root privilege escalation, etc. As of Kubernetes v1.21 the PSP resource is being deprecated, expecting a complete removal by Kubernetes v1.25.

A PSP replacement, the [Pod Security Admission](https://kubernetes.io/docs/concepts/security/pod-security-admission/) is a built in admission controller for Pod Security that is enabled by default in the API Server. It can enforce the three [Pod Security Standards](https://kubernetes.io/docs/concepts/security/pod-security-standards/) at the namespace level, by automating the security context restriction to pods when they are deployed. Each Pod Security Standard, *privileged*, *baseline*, and *restricted*, defines a level of security that ranges from entirely unrestricted (for privileged workload), to enforcing pod hardening best practices (for security-critical applications and less trusted users). The security levels are defined by sets of pod security context controls that are pre-determined for each standard.

# Network Policies

Kubernetes was designed to allow all Pods to communicate freely, without restrictions, with all other Pods in cluster Namespaces. In the time it became clear that it was not an ideal design, and mechanisms needed to be put in place in order to restrict communication between certain Pods and applications in the cluster Namespace. [Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/) are sets of rules which define how Pods are allowed to talk to other Pods and resources inside and outside the cluster. Pods not covered by any Network Policy will continue to receive unrestricted traffic from any endpoint.

Network Policies are very similar to typical Firewalls. They are designed to protect mostly assets located inside the Firewall but can restrict outgoing traffic as well based on sets of rules and policies.

The Network Policy API resource specifies **podSelectors**, *Ingress* and/or *Egress* **policyTypes**, and rules based on source and destination **ipBlocks** and **ports**. Very simplistic default allow or default deny policies can be defined as well. As a good practice, it is recommended to define a default deny policy to block all traffic to and from the Namespace, and then define sets of rules for specific traffic to be allowed in and out of the Namespace.

Let's keep in mind that not all the networking solutions available for Kubernetes support Network Policies. Review the Pod-to-Pod Communication section from the Kubernetes Architecture chapter if needed. By default, Network Policies are namespaced API resources, but certain network plugins provide additional features so that Network Policies can be applied cluster-wide.

# Monitoring and Logging

In Kubernetes, we have to collect resource usage data by Pods, Services, nodes, etc., to understand the overall resource consumption and to make decisions for scaling a given application. Two popular Kubernetes *monitoring* solutions are the Kubernetes Metrics Server and Prometheus.

- **Metrics Server** [Metrics Server](https://kubernetes.io/docs/tasks/debug-application-cluster/resource-metrics-pipeline/#metrics-server) is a cluster-wide aggregator of resource usage data - a relatively new feature in Kubernetes.

- **Prometheus**[Prometheus](https://prometheus.io/), now part of [CNCF](https://www.cncf.io/) (Cloud Native Computing Foundation), can also be used to scrape the resource usage from different Kubernetes components and objects. Using its client libraries, we can also instrument the code of our application.

Another important aspect of troubleshooting and debugging is *logging*, in which we collect the logs from different components of a given system. In Kubernetes, we can collect logs from different cluster components, objects, nodes, etc. Unfortunately, however, Kubernetes does not provide cluster-wide logging by default, therefore third-party tools are required to centralize and aggregate cluster logs. A popular method to collect logs is using [Elasticsearch](https://v1-18.docs.kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/) together with [Fluentd](http://www.fluentd.org/) with custom configuration as an agent on the nodes. Fluentd is an open-source data collector, which is also part of CNCF.

# Helm

To deploy a complex application, we use a large number of Kubernetes manifests to define API resources such as Deployments, Services, PersistentVolumes, PersistentVolumeClaims, Ingress, or ServiceAccounts. It can become counterproductive to deploy them one by one. We can bundle all those manifests after templatizing them into a well-defined format, along with other metadata. Such a bundle is referred to as *Chart*. These Charts can then be served via repositories, such as those that we have for **rpm** and **deb** packages.

[Helm](https://helm.sh/) is a package manager (analogous to **yum** and **apt** for Linux) for Kubernetes, which can install/update/delete those Charts in the Kubernetes cluster.

Helm is a CLI client that may run side-by-side with **kubectl** on our workstation, that also uses **kubeconfig** to securely communicate with the Kubernetes API server.

The **helm** client queries the Chart repositories for Charts based in search parameters, downloads a desired Chart, and then it requests the API server to deploy in the cluster the resources defined in the Chart. Charts submitted for Kubernetes are available [here](https://artifacthub.io/).

Additional information about helm and helm Charts can be found on [GitHub](https://github.com/helm/charts).

# Service Mesh

Service Mesh is a third-party solution alternative to the Kubernetes native application connectivity and exposure achieved with Services paired with Ingress Controllers. Service Mesh tools are gaining popularity, especially with larger organizations managing larger, more dynamic Kubernetes clusters. These third-party solutions introduce features such as service discovery, multi-cloud routing, and traffic telemetry.

A Service Mesh is an implementation that relies on a proxy component part of the Data Plane, which is then managed through a Control Plane. The Control Plane runs agents responsible for the service discovery, telemetry, load balancing, network policy, and gateway. The Data Plane proxy component is typically injected into Pods, and it is responsible for handling all Pod-to-Pod communication while maintaining constant communication with the Control Plane of the Service Mesh.

Several implementations of Service Mesh are:

- [Consul](https://www.consul.io/) by [HashiCorp](https://www.hashicorp.com/)
- [Envoy](https://www.envoyproxy.io/) built by Lyft, currently a [CNCF](https://www.cncf.io/) project
- [Istio](https://istio.io/) is one of the most popular service mesh solutions, backed by Google, IBM and Lyft
- [Kuma](https://kuma.io/) by [Kong](https://konghq.com/)
- [Linkerd](https://linkerd.io/) a [CNCF](https://www.cncf.io/) project
- [Maesh](https://traefik.io/traefik-mesh/) by [Containous](https://traefik.io/), the developers of [Traefik](https://traefik.io/traefik/) ingress controller
- [Tanzu Service Mesh](https://tanzu.vmware.com/service-mesh) by [VMware](https://www.vmware.com/).

# Application Deployment Strategies

A method presented earlier for new application release rollouts was the Rolling Update mechanism supported by the Deployment operator. The Rolling Update mechanism, and its reverse - the Rollback, are practical methods to manage application updates by allowing one single controller, the Deployment, to handle all the work that involves. However, while transitioning between the old and the new versions of the application replicas, the Service exposing the Deployment eventually forwards traffic to all replicas, old and new, without any possibility for the default Service to isolate a subset of the Deployment's replicas. Because of the traffic routing challenges, these update mechanisms introduce, many users may steer away from the one Deployment and one Service model, and embrace more complex deployment mechanism alternatives.

The **Canary** strategy runs two application releases simultaneously managed by two independent Deployment controllers, both exposed by the same Service. The users can manage the amount of traffic each Deployment is exposed to by separately scaling up or down the two Deployment controllers, thus increasing or decreasing the number of their replicas receiving traffic.

The **Blue/Green** strategy runs the same application release or two releases of the application on two isolated environments, but only one of the two environments is actively receiving traffic, while the second environment is idle, or may undergo rigorous testing prior to shifting traffic to it. This strategy would also require two independent Deployment controllers, each exposed by their dedicated Services, however, a traffic shifting mechanism is also required. Typically, traffic shifting can be implemented with the use of an Ingress.

# THE END

I would like to thank you if you have flowed along with the whole Kubernetes process from the very beginning and thank you if you haven't