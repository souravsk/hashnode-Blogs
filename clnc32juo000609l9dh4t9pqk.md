---
title: "Kubernetes Services and its type"
seoTitle: "Kubernetes services"
datePublished: Wed Oct 04 2023 18:29:51 GMT+0000 (Coordinated Universal Time)
cuid: clnc32juo000609l9dh4t9pqk
slug: kubernetes-services-and-its-type
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696444028475/7fb18e7a-0edb-4ef0-bac3-aa91fd9039df.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1696444122368/9ec96b85-5945-40f9-b4a5-1423dea11e10.png
tags: kubernetes, devops, node, services, pods

---

Welcome to our latest blog post, where we delve into the world of Kubernetes services files or config files. Whether you're new to Kubernetes or a seasoned pro, this guide will equip you with why we need service files. Let's get started!

# What are Services and why do we need them?

Why do we need services in the first place? We know that we deploy pods as per our use and to communicate with each other they have IP Addresses but if you know about pods they get deleted and then created again with new IP Addresses. The deleting and creating can happen for many reasons.

So let's take an example suppose you have a pod named "Frontend" and another pod named "Backend" and they communicate with each other. So What happens when for some reason one of the pods got deleted and created a new pod? Which has a new IP Address. Now they can't communicate with each other or we have to change the OLD IP with the NEW IP which will make it more complex.

That's When Kubernetes Services Comes into the Picture

In Kubernetes, a Service is a method for exposing a network application that is running as one or more Pods in your cluster.

Services Provide you with a solution of a stable or static IP Address that stays even when the pod dies. So basically in front of each pod, we set a service that represents persistent stable IP Address access to that Pod.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696098984241/4335fb9a-49f9-4d79-bfc1-5f14317a270b.png align="center")

Service also provides Load Balancing Because when you have pod replicas for example three replicas of your microservices application or three replicas of MySQL application. The service will basically get each request targeted to that MySQL or microservices application and then forward it to one of those Pods. So clients can call a single stable IP Address instance calling each part individually.

So Services are good abstractions for loose coupling for communication within the cluster so the cluster Components or pods inside the cluster also form external services like if you have a browser request coming to the cluster.

# Type of Services

There are several types of services in Kubernetes. Kubernetes Service types allow you to specify what kind of Service you want.

### ClusterIP Services

The most common that probably you will use most of the time is the ClusterIP Type. This is the default type of a service meaning when you create a service with YAML and do not specify the type it will automatically take clusterIP as a type.

It exposes the services on the cluster-internal IP address that is only reachable from within the cluster. It enables communication between different pods within the same cluster. An Example could be a database service that should only be accessed by other services within the cluster.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696099035656/aef0d311-e9b5-4374-a261-a79a7f1e2540.png align="center")

### NodePort

This type of service exposes the services on a static port on each node in the cluster. It allows external access to the services by mapping the node port to the service Port.

For example, if you have a web application running on port 8080 in your cluster, a NodePort service can expose it on a specific port (e.g. 30000) and you can access the application using the IP address of any node in the cluster with the specified port.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696099066569/3573a30a-cc51-4289-8ef4-2d0b93203da2.png align="center")

### Load Balancer

This service type assigns an external IP address (usually provided by a cloud provider's load balancer) to the service. It distributes the incoming traffic across multiple pods. Load Balancer services are commonly used when you want to expose your application to the internet.

For Instance, if you have a web application a load balancer service can distribute the incoming web requests across multiple pods running the application providing scalability and redundancy.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696099111595/c666a034-f29f-48de-af10-ff257123ab00.png align="center")

### External Name

This type of service is used to provide an alias or redirect to an external service outside of the cluster. It allows you to use a Kubernetes service to refer to an external service by its DNS name.

For Example, you can create an ExternalName service called "my-external-service" that pointer to "external-service.example.com" and any requests to "my-external-service" will be redirected to "external-service.example.com"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696099367963/588ac11a-bac5-4b2a-a893-a112193d3fbb.png align="center")

# Let's Create NodePort Service

In this example, we will deploy nginx, NodePort service and configMap.

## Step - 1 (create configmap)

A [ConfigMap](https://kubernetes.io/docs/concepts/configuration/configmap/) is a Kubernetes resource that stores configuration data in key-value pairs. When used in conjunction with deployments, ConfigMaps can help manage and update application configuration data without having to rebuild images or restart containers. In simple terms, we can store some value in configMap and then access it in other deployments.

Let's write the configmap file

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: webpage
  namespace: default
data:
  index.html: |
    <html>
    <body>
    <h1 align="center">NodePort Services </h1>
    <h2 align="center"> This is the web page that is accessed by using kubernetes services and the type is NodePort </h2>
    </body>
    </html>
```

Now apply this yaml file.

```yaml
kubectl apply -f <configMap file name>
```

## Step - 2 (create nginx )

Now we will write the nginx deployment file.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx
  namespace: default
spec:
  selector:
    matchLabels:
      app: nginx
  replicas: 2
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
        volumeMounts:
          - name: nginx-index-file
            mountPath: /usr/share/nginx/html/
      volumes:
      - name: nginx-index-file
        configMap:
          name: webpage
```

Now apply this deployment file

```yaml
kubectl apply -f <deployment file>
```

## Step - 3 (create services)

Now we will write services yaml file.

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
  namespace: default
spec:
  selector:
    app: nginx
  type: NodePort
  ports:
    - port: 80
      nodePort: 30004
      targetPort: 80
```

Now apply the service file.

```yaml
kubectl apply -f <services file name>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696294902752/7723c227-da12-42f4-8b2c-536fbb2fd3d5.png align="center")

We have applied all the yaml files.

## Step - 4 (Access the app)

Now every this is deployed let's use the curl command to see if our service worked or not. I'm using minikube.

```yaml
curl <minikube ip>:30004
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696295024604/c06378aa-021f-4941-accc-a3fa94860e6e.png align="center")

Yes, it works.

## Most use Commands

`kubectl get services` – List one or more services.

`kubectl describe services` – Display the detailed state of a service.

`kubectl expose deployment [deployment_name]` – Expose a replication controller, service, deployment, or pod as a new Kubernetes service.

`kubectl edit services` – Edit and update the definition of one or more services.

# THE END

That is all for today we learned a lot today if you have any questions please let me I will answer that. One more suggestion please write down those commands on a piece of paper that will be always on your table so that whenever you need it you can refer from that.