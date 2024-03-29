## KUBERNETES VOLUME: Do You Really Need It?

In today's Blog, we understand, data is the most precious asset for many startups and enterprises. In a Kubernetes cluster, containers in Pods can be either data producers, data consumers, or both. While some container data is expected to be transient and is not expected to outlive a Pod, other forms of data must outlive the Pod in order to be aggregated and possibly loaded into analytics engines. Kubernetes must provide storage resources to provide data to be consumed by containers or store data produced by containers. Kubernetes uses **Volumes** of several types and a few other storage resources for container data management. we will talk about **PersistentVolume** and **PersistentVolumeClaim** objects, which help us attach persistent storage Volumes to Pods.

# Volume

As we know, containers running in Pods are ephemeral in nature. All data stored inside a container is deleted if the container crashes. However, the **kubelet** will restart it with a clean slate, which means that it will not have any of the old data.

To overcome this problem, Kubernetes uses [Volumes](https://kubernetes.io/docs/concepts/storage/volumes/), storage abstractions that allow various storage technologies to be used by Kubernetes and offered to containers in Pods as storage media. A Volume is essentially a mount point on the container's file system backed by a storage medium. The storage medium, content and access mode are determined by the Volume Type.

![14.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1664888265099/kzWn5EwWt.png align="left")

In Kubernetes, a Volume is linked to a Pod and can be shared among the containers of that Pod. Although the Volume has the same life span as the Pod, meaning that it is deleted together with the Pod, the Volume outlives the containers of the Pod - this allows data to be preserved across container restarts.

## Volume Type

A directory which is mounted inside a Pod is backed by the underlying [Volume Type](https://kubernetes.io/docs/concepts/storage/volumes/#volume-types). A Volume Type decides the properties of the directory, like size, content, default access modes, etc. Some examples of Volume Types are:

- **emptyDir**:- An **empty** Volume is created for the Pod as soon as it is scheduled on the worker node. The Volume's life is tightly coupled with the Pod. If the Pod is terminated, the content of **emptyDir** is deleted forever.

- **hostPath**:- With the **hostPath** Volume Type, we can share a directory between the host and the Pod. If the Pod is terminated, the content of the Volume is still available on the host.

- **gcePersistentDisk**:- With the **gcePersistentDisk** Volume Type, we can mount a [Google Compute Engine (GCE) persistent disk](https://cloud.google.com/compute/docs/disks/) into a Pod.

- **awsElasticBlockStore**:- With the **awsElasticBlockStore** Volume Type, we can mount an [AWS EBS Volume](https://aws.amazon.com/ebs/) into a Pod.

- **azureDisk**:- With **azureDisk** we can mount a [Microsoft Azure Data Disk](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/managed-disks-overview) into a Pod.

- **azureFile**:- With **azureFile** we can mount a [Microsoft Azure File Volume](https://github.com/kubernetes/examples/blob/master/staging/volumes/azure_file/README.md) into a Pod.

- **cephfs**:- With **cephfs**, an existing [CephFS](https://ceph.io/ceph-storage/) volume can be mounted into a Pod. When a Pod terminates, the volume is unmounted and the contents of the volume are preserved.

- **nfs**:- With **nfs**, we can mount an [NFS](https://en.wikipedia.org/wiki/Network_File_System) share into a Pod.

- **iscsi**:- With **iscsi**, we can mount an [iSCSI](https://en.wikipedia.org/wiki/ISCSI) share into a Pod.

- **secret**:- With the **[secret](https://kubernetes.io/docs/concepts/configuration/secret/)** Volume Type, we can pass sensitive information, such as passwords, to Pods.

- **configMap:- **With **[configMap](https://kubernetes.io/docs/concepts/configuration/configmap/)** objects, we can provide configuration data, or shell commands and arguments into a Pod.

- **persistentVolumeClaim**:- We can attach a **[PersistentVolume](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)** to a Pod using a **[persistentVolumeClaim](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims)**.

You can learn more details about Volume Types from the [documentation](https://kubernetes.io/docs/concepts/storage/volumes/).

## Persistent Volume

In a typical IT environment, storage is managed by the storage/system administrators. The end user will just receive instructions to use the storage but is not involved with the underlying storage management.

In the containerized world, we would like to follow similar rules, but it becomes challenging, given the many Volume Types we have seen earlier. Kubernetes resolves this problem with the [PersistentVolume (PV)](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) ****subsystem, which provides APIs for users and administrators to manage and consume persistent storage. To manage the Volume, it uses the PersistentVolume API resource type, and to consume it, it uses the PersistentVolumeClaim API resource type.

A Persistent Volume is a storage abstraction backed by several storage technologies, which could be local to the host where the Pod is deployed with its application container(s), network attached storage, cloud storage, or a distributed storage solution. A Persistent Volume is statically provisioned by the cluster administrator.

![15.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1664888288761/zuXWpWDDG.png align="left")

PersistentVolumes can be [dynamically](https://kubernetes.io/docs/concepts/storage/dynamic-provisioning/) provisioned based on the StorageClass resource. A StorageClass contains pre-defined provisioners and parameters to create a PersistentVolume. Using PersistentVolumeClaims, a user sends the request for dynamic PV creation, which gets wired to the StorageClass resource.

Some of the Volume Types that support managing storage using PersistentVolumes are:

- GCEPersistentDisk
- AWSElasticBlockStore
- AzureFile
- AzureDisk
- CephFS
- NFS
- iSCSI.

For a complete list, as well as more details, you can check out the [types of Persistent Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#types-of-persistent-volumes).

### Persistent Volume Claim

A [PersistentVolumeClaim (PVC)](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims) ****is a request for storage by a user. Users request for PersistentVolume resources based on type, [access mode](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes), and size. There are three access modes: ReadWriteOnce (read-write by a single node), ReadOnlyMany (read-only by many nodes), and ReadWriteMany (read-write by many nodes). Once a suitable PersistentVolume is found, it is bound to a PersistentVolumeClaim.

![16.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1664888306184/sfJXZGa9D.png align="left")

After a successful bound, the PersistentVolumeClaim resource can be used by the containers of the Pod.

![17.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1664888318652/tF7u3OC8x.png align="left")

Once a user finishes its work, the attached PersistentVolumes can be released. The underlying PersistentVolumes can then be *reclaimed* (for an admin to verify and/or aggregate data), *deleted* (both data and volume are deleted), or *recycled* for future usage (only data is deleted), based on the configured **persistentVolumeReclaimPolicy** property.

To learn more, you can check out the [PersistentVolumeClaims](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims).

## Container Storage Interface (CSI)

Container orchestrators like Kubernetes, Mesos, Docker or Cloud Foundry used to have their own methods of managing external storage using Volumes. For storage vendors, it was challenging to manage different Volume plugins for different orchestrators. Storage vendors and community members from different orchestrators started working together to standardize the Volume interface; a volume plugin built using a standardized [Container Storage Interface](https://kubernetes.io/docs/concepts/storage/volumes/#csi) (CSI) designed to work on different container orchestrators. Explore the [CSI specifications](https://github.com/container-storage-interface/spec/blob/master/spec.md) for more details.

Between Kubernetes releases v1.9 and v1.13 CSI matured from alpha to [stable support](https://kubernetes.io/blog/2019/01/15/container-storage-interface-ga/), which makes installing new CSI-compliant Volume plugins very easy. With CSI, third-party storage providers can [develop solutions](https://kubernetes-csi.github.io/docs/) without the need to add them into the core Kubernetes codebase.

## Using a Shared hostPath Volume Type
```
$ vim app-blue-shared-vol.yaml
```
```
apiVersion: apps/v1
kind: Deployment
metadata:
     creationTimestamp: null
     labels:
        app: blue-app
     name: blue-app
spec:
    replicas: 1
    selector:
        matchLabels:
             app: blue-app
    strategy: {}
    template:
       metadata:
            creationTimestamp: null
            labels:
               app: blue-app
               type: canary
       spec:
           volumes:
           - name: host-volume
              hostPath:
                  path: /home/docker/blue-shared-volume
           containers:
           - image: nginx
              name: nginx
              ports:
              - containerPort: 80
              volumeMounts:
              - mountPath: /usr/share/nginx/html
                 name: host-volume
           - image: debian
              name: debian
              volumeMounts:
           - mountPath: /host-vol
              name: host-volume
           command: ["/bin/sh", "-c", "echo Welcome to BLUE App! > /host-vol/index.html ; sleep infinity"]
status: {}
```

This is all for today, please try this in your Kubernetes cluster as soon as possible. Until then, I'll see you later.