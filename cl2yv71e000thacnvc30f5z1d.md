## Getting started with Portainer

# What is Portainer?

Portainer is a lightweight management UI which allows you to easily manage your different Docker environments (Docker hosts or Swarm clusters). 

Portainer is meant to be as simple to deploy as it is to use. it consists of a single container that can run on any Docker Engine (Can be deployed as Linux container or a Windows native container, supports other platforms too). Portainer allow you to manage all your Docker resource ( containers, images, volume, networks and more)! . it is compatible with the standalone Docker engine and with Docker swarm mode.

# Why Portainer?

Portainer is a great fit for organizations that cannot hire or train their staff for the new cloud-native gap. Because Portainer is so simple to install and manage all your containers with a good and simple UI. 

# Portainer architecture

![portainer-architecture-detailed.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652097962664/e38RAWP_Y.png align="left")
### Portainer consists of two elements: 
- The Portainer Server  
- The Portainer Agent

Both run as lightweight containers on your existing containerized infrastructure. The Portainer Agent should be deployed to each node in your cluster and configured to report back to the Portainer Server container. A single Portainer Server will accept connections from any number of Portainer Agents, providing the ability to manage multiple clusters from one centralized interface. To do this, the Portainer Server container requires data persistence. The Portainer Agents are stateless, with data being shipped back to the Portainer Server container.

Both Portainer server and agents run as containers on existing infrastructure. The agents communicate with the server; for this to work, the server and the agents must be on the same network. Furthermore, there are the edge agents, which run as instances on remote devices. What is special about edge agents is that they communicate with the server across network boundaries

## Security

Portainer runs exclusively on your servers, within your network, and behind your own firewalls. As a result, Portainer does not currently hold any SOC or PCI/DSS compliance because it does not host any of your infrastructures. You can even run Portainer completely disconnected (air-gapped) without any impact on functionality.

## Ports

In order to access the UI and API, and for the Portainer Server instance and the Portainer Agents to communicate, certain ports need to be accessible. The Portainer Server listens on port 9443 for the UI and API (or on 30779 for Kubernetes with NodePort) and exposes a TCP tunnel server on port 8000. The Portainer Agents listen on port 9001.

# Install Portainer

There are many ways you can install Portainer in any system. Portainer is especially straightforward to install. 

**There are two options:** 
- Installing a new
- Adding an environment to an existing installation.

**We will Set up a new Portainer Server**

- Docker Standalone

- Docker Swarm

- Kubernetes

As you can see we can Select the environment for your new Portainer as you wish we will go with  Docker Standalone and will be installing Portainer with Docker on WSL / Docker Desktop 

### To get started, you will need:

- The latest version of Docker Desktop is installed and working.
- Administrator access on the machine that will host your Portainer Server instance.
- Windows Subsystem for Linux (WSL) installed and a Linux distribution selected. For a new installation, we recommend WSL2.
- By default, Portainer Server will expose the UI over port 9443 and expose a TCP tunnel server over port 8000. The latter is optional and is only required if you plan to use the Edge compute features with Edge agents.
- A license key for Portainer Business Edition. (Only if you want the Business Edition)

## Deployment

First, create the volume that Portainer Server will use to store its database:

```
docker volume create portainer_data

``` 

Then, download and install the Portainer Server container:


```
docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest

``` 

> By default, Portainer generates and uses a self-signed SSL certificate to secure port 9443. Alternatively, you can provide your own SSL certificate during installation or via the Portainer UI after installation is complete.

> If you require HTTP port 9000 open for legacy reasons, add the following to your docker run command:
-p 9000:9000

Portainer Server has now been installed. You can check to see whether the Portainer Server container has started by running docker ps:


```
root@server:~# docker ps
CONTAINER ID   IMAGE                                              COMMAND                  CREATED        STATUS        PORTS                                                                                  NAMES
f4ab79732007   portainer/portainer-ee:latest                      "/portainer"             2 weeks ago    Up 29 hours   0.0.0.0:8000->8000/tcp, :::8000->8000/tcp, 0.0.0.0:9443->9000/tcp, :::9443->9443/tcp   portainer

``` 

## Logging In

Now that the installation is complete, you can log into your Portainer Server instance by opening a web browser and going to:

```
https://localhost:9443

``` 
Replace localhost with the relevant IP address or FQDN if needed, and adjust the port if you changed it earlier.

### Creating the first user

Your first user will be an administrator. The username defaults to admin but you can change it if you prefer. The password must be at least 12 characters long and meet the listed password requirement


![be-server-setup-1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652108860862/k-sINYKEy.png align="left")

### Connecting Portainer to your environments

Once the admin user has been created, the Environment Wizard will automatically launch. The wizard will help get you started with Portainer.


![2.10-install-setup-wizard.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652108906253/74XwQHM5G.png align="left")

The installation process automatically detects your local environment and sets it up for you. If you want to add additional environments to manage with this Portainer instance, click Add Environments. Otherwise, click Get Started to start using Portainer!



Thank you for reading 📖 





