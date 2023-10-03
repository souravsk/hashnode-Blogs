---
title: "What is a kubeconfig file?"
seoTitle: "What is kubeconfig file"
datePublished: Tue Oct 03 2023 02:12:09 GMT+0000 (Coordinated Universal Time)
cuid: cln9opddy000308kx4xgt6sg2
slug: kubeconfig
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696298916780/16f777c1-64d5-4d71-840b-e98c1e71e203.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1696299104131/6e394361-9d30-46ce-a921-f9c4e64a8f52.png
tags: kubernetes, devops, yaml, cluster, kubeconfig

---

Welcome to our latest blog post, where we delve into the world of Kubernetes kubeconfig files or config files. Whether you're new to Kubernetes or a seasoned pro, this guide will equip you with why we need kubeconfig files. Let's get started!

# so what is a kubeconfig file?

kubeconfig is the default way to authenticate to a Kubernetes cluster. It can be a little cryptic, but it is easy to understand if you look closely.

Whether you use [Kubernetes](https://www.redhat.com/en/topics/containers/what-is-kubernetes?intcmp=701f20000012ngPAAQ) in a bare-metal cluster, the cloud, or a simple virtual machine created with [minikube](https://minikube.sigs.k8s.io/docs/start/), you always have a `kubeconfig` file. The file contents may differ in some cases, but the principle is the same. This post uses a minikube installation to explain the `kubeconfig` file.

## **kubeconfig file components**

Kubernetes components like `kubelet`, `kube-controller-manager`, or `kubectl` use the `kubeconfig` file to interact with the Kubernetes API. Usually, the `kubectl` commands use the `kubeconfig` file.

The `kubeconfig` file's default location for `kubectl` is the `~/.kube` directory. Instead of using the full `kubeconfig` name, the file is just named `config`. The default location of the `kubeconfig` file is `~/.kube/config`. There are other ways to specify the `kubeconfig` location, such as the `KUBECONFIG` environment variable or the `kubectl --kubeconfig` parameter.

The `kubeconfig` file is a [YAML](https://opensource.com/downloads/yaml-cheat-sheet?intcmp=701f20000012ngPAAQ) file containing groups of clusters, users, and contexts.

* A **cluster** is a Kubernetes cluster.
    
* A **user** is a credential used to interact with the Kubernetes API.
    
* A **context** is a combination of a cluster and a user. Every time you execute an `kubectl` command, you reference a context inside `kubeconfig`.
    

The following is a sample `kubeconfig` file from a new minikube installation:

```yaml
apiVersion: v1
kind: Config
clusters:
- name: minikube
 cluster:
   certificate-authority: /home/hector/.minikube/ca.crt
   server: https://192.168.39.217:8443
users:
- name: minikube
 user:
   client-certificate: /home/hector/.minikube/profiles/minikube/client.crt
   client-key: /home/hector/.minikube/profiles/minikube/client.key
contexts:
- name: minikube
 context:
   cluster: minikube
   namespace: default
   user: minikube
current-context: minikube
```

**clusters** section lists all clusters that you already connected. In this case, there is only one, named **minikube**. This name is arbitrary and can be any name you like. Inside the cluster are two keys:

* **certificate-authority** contains a certificate for the [certificate authority (CA)](https://www.redhat.com/sysadmin/who-signed-my-cert) that signed all internal Kubernetes certificates. This can be a file path or a [Base64](https://www.redhat.com/sysadmin/base64-encoding) string of the certificate's Privacy Enhanced Mail (PEM) format.
    
* **server** is the address of the server.
    

**users** section lists all users already used to connect to a cluster. In this case, there is only a single user, named **minikube**. This name is arbitrary, and there is no relationship with any object inside Kubernetes or OpenShift. There are some possible keys for a user:

* **client-certificate** contains a certificate for the user signed by the Kubernetes CA. This can be a file path or a Base64 string in the certificate PEM format.
    
* **client-key** contains the key that signed the client certificate.
    
* **token** contains a token for this user when there is no certificate.
    

**contexts** section specifies a combination of a user and a cluster. It also defines a default namespace for this pair. The context name is arbitrary, but the user and cluster should be predefined inside the `kubeconfig` file. If the namespace does not exist inside Kubernetes, the commands will fail and display the default Kubernetes message for a nonexistent namespace.

# **Kubeconfig to Access Multiple Clusters**

By doing this example you will understand how kubeconfig files are written and how you can access **multiple Kubernetes clusters** with one kubeconfig file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696298709787/3c6d302c-7a8b-4d9e-b800-9064baeedf83.png align="center")

## Step - 1 (Create to Clusters)

For this example, we need 2 Kubernetes clusters. So I can show you how you can switch to both Kubernetes clusters. In my case I have created a **Minikube cluster** and other Kubernetes cluster I have created on Azure with **Azure Kubernetes service**.

This is my Minikube Cluster

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696280024106/c62e395d-1df8-411d-8330-52be53909f57.png align="center")

This is my Azure Kubernetes Services Cluster

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696280034118/0c4fb30f-b755-41e8-8ade-8ef6d0bd756b.png align="center")

## Step - 2 (Get both config files)

First thing first we will make a copy of our config. Use this command to make a copy

```yaml
cp ~/.kube/config ~/.kube/config.bak
```

Now create a folder on your desktop and then move the config file of the Minikube to this folder so that we can edit this config file. You can use this command to move the file.

```yaml
mv ~/.kind/config .
```

Now open that config file into a code editor. So this is our config file for our Minikube Cluster.

```yaml
apiVersion: v1
kind: Config
clusters:
- cluster:
    certificate-authority: /home/codespace/.minikube/ca.crt
    server: https://192.168.49.2:8443
  name: minikube
contexts:
- context:
    cluster: minikube
    namespace: default
    user: minikube
  name: minikube
current-context: minikube
preferences: {}
users:
- name: minikube
  user:
    client-certificate: /home/codespace/.minikube/profiles/minikube/client.crt
    client-key: /home/codespace/.minikube/profiles/minikube/client.key
```

Now we will download or get the config file for the Azure Kubernetes Services. To do so you can connect to the Azure Kubernetes Services Cluster using Azure Cloud shell.

This is my Azure Kubernetes Services Cluster

```yaml
apiVersion: v1
clusters:
- cluster:
    certificate-authority-data: LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUU2RENDQXRDZ0F3SUJBZ0lRTkWWG1kQzEzckNtVlI
  name: azure-cluster
contexts:
- context:
    cluster: azure-cluster
    user: clusterUser_az-400_azure-cluster
  name: azure-cluster
current-context: azure-cluster
kind: Config
preferences: {}
users:
- name: clusterUser_az-400_azure-cluster
  user:
    client-certificate-data: LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUZIakNDQXdhZ0F3SUJBZ0lSQU15dHlpb3pTQm8vN
    client-key-data: LS0tLS1CRUdJTiBSU0EgUFJJVkFURSBLRVktLS0tLQpNSUlKS0FJQkFBS0NBZ0VBeGdkVEdjLytLbnN0R0NzT1A2b05
    token: kdgbulnfv6rhfha8gcey99a5f2b4935ash98gvss5f1mpw7ecu5lzap3935n6xqgxgsu0mnmso5
```

## Step - 3 (Merge Kubeconfig file)

Now that we have both the files we merge both files in one config so that we can use that config file to assess both clusters just with one config file.

To merge kubeconfig file we have a command that we are going to use.

```yaml
$ KUBECONFIG=~/.kube/config:/path/to/other/config kubectl config view --flatten > /tmp/new_config
```

This command will create a new config file which will be the merger of both config files.

```yaml
apiVersion: v1
clusters:
- cluster:
    certificate-authority-data: LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0
  name: azure-cluster
- cluster:
    certificate-authority-data: LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1
    cluster: azure-cluster
    user: clusterUser_az-400_azure-cluster
  name: azure-cluster
- context:
    cluster: minikube
    namespace: default
    user: minikube
  name: minikube
current-context: minikube
kind: Config
preferences: {}
users:
- name: clusterUser_az-400_azure-cluster
  user:
    client-certificate-data: LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUZIakNDQXdhZ0F3SUJBZ
    client-key-data: LS0tLS1CRUdJTiBSU0EgUFJJVkFURSBLRVktLS0tLQpNSUlKS0FJQkFBS0NBZ0VBeGdkVEdjLy
    token: kdgbulnfv6rhfha8gcey99a5f2b4935ash98gvss5f1mpw7ecu5lzap3935n6xqgxgsu0mnmso5lv4dfi71tj6
- name: minikube
  user:
    client-certificate-data: LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSURJVENDQWdtZ0
    client-key-data: LS0tLS1CRUdJTiBSU0EgUFJJVkFURSBLRVktLS0tLQpNSUlFb3dJQkFBS0NBUUVB
```

Now we have merged both config files into one config file.

## Step - 4 (Access both Cluster)

First, if you have remembered we have moved our config file to a working dir. This means right now we don't have any config files in `~/.kube/` a folder. So now we will move this file newly made config file. To `~/.kube`

Use the mv command to move the file

```yaml
$ mv /config-folder/new_config ~/.kube/config
```

Now that we have moved our latest config file to the `.kube` file. Let's check whether it's working or not. To do so we can use this command that will show all the clusters that we can access.

```yaml
kubectl config get-clusters
```

There are other commands like

```yaml
kubectl config get-users #to get all users
kubectl config get-contexts # to get all the contexts
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696282866608/dc698d81-4d3e-44ed-9787-7f6440054a53.png align="center")

If you look closely at the last command it shows the contexts and if look at the **CURRENT** there is `*` on the Minikube because that Minikube is selected.

If you want to change the contexts from Minikube to the Azure Kubernetes then we have to use this command to access that cluster.

```yaml
kubectl config use-contexts <name>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696283504214/598a94e9-991c-4a57-bab2-0edbf86074b6.png align="center")

As you can see you have changed the cluster from Minikube to Azure-cluster.

### Some Commands to Manage Cluster & Contexts

```yaml
$ kubectl config --help
$ kubectl config view
$ kubectl config view --minify
$ kubectl config get-clusters
$ kubectl config get-users
$ kubectl config current-context
$ kubectl config set-context <CONTEXT_NAME> --namespace=dev
$ kubectl config set-context $(kubectl config current-context) --namespace=dev
$ kubectl config use-context <CONTEXT_NAME>
```

# THE END

That is all for today we learned a lot today if you have any questions please let me I will answer that. One more suggestion please write down those commands on a piece of paper that will be always on your table so that whenever you need it you can refer from that. Let me know if you are stuck at any point I will be happy to help.