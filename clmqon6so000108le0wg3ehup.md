---
title: "Kubernetes Pods For your Containers"
seoTitle: "Kubernetes Pods"
datePublished: Tue Sep 19 2023 19:02:50 GMT+0000 (Coordinated Universal Time)
cuid: clmqon6so000108le0wg3ehup
slug: pods
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695150064860/19d37d1a-ffe5-46ad-a8d7-82e4842b85cc.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1695150141887/609fdc71-439d-458d-89e0-cb657da01571.png
tags: kubernetes, devops, containers, kubernetes-container, pods

---

Hey Everyone in today's blog we will learn about Kubernetes Pod. In Our last blog, we learned about Minikube which let us test our application in our local system. So let's go

# What is Pod?

In Kubernetes, a "Pod" is the smallest and simplest deployment unit. You can think of it as a small box or container where your application runs.

Imagine you have an application, like a website. Instead of putting the entire website in one big container, you might need multiple small containers to make it work - one for the web server, one for the database, and so on. Each of these small containers is like a specialized worker.

A "Pod" in Kubernetes is like a wrapper holding one or more small containers. It's a way to group them together, like putting them in a box. These containers inside the same Pod share the same network space and can easily communicate with each other, making them work together closely.

So, in simple terms, a Pod is like a box that holds one or more containers that need to work together to make your application run smoothly in the Kubernetes world.

## **How Pods Manage Multiple Container**

Managing multiple containers within a Kubernetes Pod is like having a team of workers inside a single room. Here's a simple way to understand how Pods handle multiple containers:

1. **Shared Space**: Imagine you have a room (the Pod) where your workers (containers) need to collaborate. They share the same space, which means they can easily talk because they're in the same room.
    
2. **Common Goal**: Each worker (container) in the room has a specific job to do. They all work together to achieve a common goal, like building software or a web application.
    
3. **Communication**: Since they're in the same room (Pod), they can talk to each other directly without any extra effort. This makes it easy for them to share information and work together smoothly.
    
4. **Resources**: The room (Pod) provides resources like electricity and internet, and the workers (containers) share these resources. They can use what they need to get their work done without worrying about the others in the room.
    

So, in a Kubernetes Pod, multiple containers work together in a shared space, communicate easily, and collaborate to achieve a common task or goal. It's like having a team of workers in the same room, each doing their part to make your application run effectively.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1694712485939/7aa08d99-7e8f-40d4-94e4-2b4533617bc4.png align="center")

### Let's deploy the container on the pod

To show you the container deployed in the pod we will deploy a nginx web server. So first we have to create a deployment file so let's write the deployment file.

### Yaml file

```yaml
apiVersion: v3
kind: Service
metadata:
  name: nginx
  labels:
    app: nginx
spec:
  selector:
    app: nginx
  ports:
  - port: 80
    protocol: TCP
    targetPort: 80
  type: ClusterIP

---

  apiVersion: apps/v1
  kind: Deployment
  metadata:
    name: nginx
    labels:
      app: nginx
  spec: 
    replicas: 1
    selector:
      matchLabels:
        app: nginx
    template:
      metadata:
        labels:
          app: nginx
      spec:
        containers:
        - name: nginx
          image: nginx:latest
          imagePullPolicy: IfNotPeresent
          ports:
          - containerPort: 80
            protocol: TCP
```

So we have created the YAML file. Let me explain a little bit so that you can see there are 2 parts in this YAML file one is services and the other one is department.

In the services part we have the port number and the app name of the deployment app name and on the deployment part we have our metadata then the container details like image name port number etc.

### Apply the Yaml file

Now that our YAML file is ready let's apply our YAML file to our Minikube cluster.

To apply this YAML file to a cluster we will use these commands

```yaml
kubectl apply -f deploy.yml
```

`apply` it is used whenever we have to apply yaml file

`-f` this is a tag that will let you apply yaml file

`deploy.yml` is our yaml file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695145553788/e5839815-f983-452b-9cda-49c9a9aaafb0.png align="center")

We have successfully deployed the nginx as you can see in the above picture. So for this blog, we will focus on Pods.

### Pods Command

I think it's the best time to see all the commands related to Pods

`kubectl get pod` – **List one or more pods.**

`kubectl get pods --sort-by='.status.containerStatuses[0].restartCount'` – **List pods Sorted by Restart Count.**

`kubectl get pods --field-selector=status.phase=Running` – **Get all running pods in the namespace.**

`kubectl delete pod <pod_name>` – **Delete a pod.**

`kubectl describe pod <pod_name>` – **Display the detailed state of pods.**

`kubectl create pod <pod_name>` – **Create a pod.**

`kubectl exec <pod_name> -c <container_name> <command>` – **Execute a command against a container in a pod. Read more: Using Kubectl Exec: Connect to Your Kubernetes Containers**

`kubectl exec -it <pod_name> /bin/sh` – **Get an interactive shell on a single-container pod.**

`kubectl top pod` – **Display Resource usage (CPU/Memory/Storage) for pods.**

`kubectl annotate pod <pod_name> <annotation>` – **Add or update the annotations of a pod.**

`kubectl label pods <pod_name> new-label=<label name>` – **Add or update the label of a pod.**

`kubectl get pods --show-labels` – **Get pods and show labels.**

`kubectl port-forward <pod name> <port number to listen on>:<port number to forward to>` – **Listen on a port on the local machine and forward to a port on a specified pod.**

This command will be more than enough for any pod use case. You don't have to remember all these commands. You can just bookmark this blog and whenever you want to see some commands related to the pod you can refer to this.

### **Access our application**

The reason I have added the service is so that I can access the application on our local machine by exposing those ports.  
The command will be

```yaml
kubectl port-forward service/nginx 8080:80
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695148690821/e4f6cb2b-e7c1-4cdf-982a-9a36886e134a.png align="center")

We have executed the command. Now go to your browser and to go this URL `http://127.0.0.1:8080`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695148827077/8d908426-85de-49db-9218-46957af5766d.png align="center")

Yes, it working.

# THE END

That is all for today we learned a lot today if you have any questions please let me I will answer that. One more suggestion please write down those commands on a piece of paper that will be always on your table so that whenever you need it you can refer from that.