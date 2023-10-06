---
title: "Blog on Kubernetes Secrets"
seoTitle: "Save you secrets with Kubernetes Secrets"
datePublished: Fri Oct 06 2023 00:01:23 GMT+0000 (Coordinated Universal Time)
cuid: clnducr8v000009l256hjgxv3
slug: secret
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696550363089/1b6b2267-6c45-4b86-89fc-68f7202c322f.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1696550436664/b91eb5fb-c981-4251-b751-6483b09d1f16.png
tags: kubernetes, devops, yaml, secrets, environment-variables

---

Welcome to our latest blog post, where we delve into the world of Kubernetes Secrets. Whether you're new to Kubernetes or a seasoned pro, this guide will equip you with why we need secrets. Let's get started!

## What is a K8s secret?

A secret as the name implies is any information that needs to be kept confidential such as passwords, tokens, etc.

You can technically put the credentials directly into a pod specification in plain text but doing that is not very safe as you can imagine. To solve this, Kubernetes has the concept of secrets where you can store your sensitive info securely and also control how a pod consumes it.

## How to create secrets?

In general, both user and Kubernetes itself can create a secret. If all you need is to access the API securely, then K8s can automatically create a secret attached to a service account that contains credentials to access the API. This is the recommended way to access the API.

In the situation where we need to create our own secret for other uses, we can do that as well. Take for example we have a pod running our application that need to access another system with the username “*example-user*” and password “*example-password*”, how do we create the secret and get our pod to recognize and use the credentials? We can create it manually or with a yaml file.

### Manually create a secret

To create a secret manually, we must first convert the string to base64.

```bash
$ echo -n 'example-user' | base64
4oCYZXhhbXBsZS11c2Vy4oCZ
$ echo -n 'example-password' | base64
4oCYZXhhbXBsZS1wYXNzd29yZOKAmQ==
```

Then we create a yaml file (example.yaml) with our secret specs.

```yaml
apiVersion: v1
kind: Secret
metadata:
name: demo
type: Opaque
data:
username: 4oCYZXhhbXBsZS11c2Vy4oCZ
password: 4oCYZXhhbXBsZS1wYXNzd29yZOKAmQ==
```

We can check if a secret was created

```yaml
$ kubectl get secret
NAME                  TYPE                                  DATA      AGE
default-token-v8gqd   kubernetes.io/service-account-token   3         6m
demo                  Opaque                                2         11s
```

As you can see we have a system-generated secret and the one we just created. We can also describe our secret just to make sure our secret is not in plain text.

```yaml
Type:  Opaque
Data
====
username:  18 bytes
password:  22 bytes
```

# How to use the secret?

There are two ways to consume the secret we created above:

* Data volume
    
* Env variable
    

We will demonstrate both with a simple example.

### Consuming secret in a volume

To consume a secret in a volume, we must first make sure that the volume is defined in the pod manifest and the name of the secret is specified so that the container can use it. We can also do things like change file paths and permissions.

```yaml
apiVersion: v1
kind: Pod
metadata:
name: volume-pod
spec:
containers:
- name: mycontainer
image: redis
volumeMounts:             #We mount our volume
- name: foo
mountPath: "/etc/foo"
readOnly: true
volumes:                    #We use the volume and defined our secret
- name: foo
secret:
secretName: demo
```

We can see that our secret is in use

```yaml
Volumes:
foo:
Type:        Secret (a volume populated by a Secret)
SecretName:  demo
Optional:    false
default-token-v8gqd:
Type:        Secret (a volume populated by a Secret)
SecretName:  default-token-v8gqd
Optional:    false
```

Now to verify that the secret is what we defined above, we can use “kubectl exec” to get into the container and check.

```bash
$ kubectl exec -ti mypod bash
root@mypod:/data# cat /etc/foo/username 
'Example-user'
root@mypod:/data# cat /etc/foo/password 
‘example-password’
```

We can see that the container in the pod is in fact using the credentials we created above. Next let us see what it looks like using the same secret in env variable.

### Consuming secret in env variable

```yaml
apiVersion: v1
kind: Pod
metadata:
name: secret-env-pod
spec:
containers:
- name: mycontainer
image: redis
env:
- name: SECRET_USERNAME        
valueFrom:
secretKeyRef:
name: demo                #Name of secret
key: username             #secret key
- name: SECRET_PASSWORD
valueFrom:
secretKeyRef:
name: demo
key: password
restartPolicy: Never
```

As you can see, instead of the volumes, we are defining env\[\].valueFrom.secretKeyRef referencing the key in the secret. Let us see what this pod looks like after creating.

```bash
root@secret-env-pod:/data# env | grep SECRET
SECRET_PASSWORD='example-password'
SECRET_USERNAME='example-user'
```

## Final tips for K8s secrets

A few more things to keep in mind:

* When you update the secret that is already being consumed, Kubelet makes sure the key is automatically updated.
    
* A pod is not the only object that uses a secret, other parts of the system can also use a secret.
    
* A secret can be consumed by more than one pod.
    

# THE END

That is all for today we learned a lot today if you have any questions please let me I will answer that. One more suggestion please write down those commands on a piece of paper that will be always on your table so that whenever you need it you can refer from that.