## Docker Storage


Docker simplifies and accelerates our workflow while giving developers the liberty to innovate with their choice of tools, application stacks, and deployment environments for every project. Docker uses **storage drivers** to manage the contents of the **image layers** and the **writable container** layer. 

In this blog, I’ve covered everything about **Docker Storage**. There are many places inside Docker (both at the engine level and container level) that use or work with storage.

# what is docker storage ?

![DStorage-00b-docker-storage.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1661327395276/Feq8ec8m4.jpg align="left")

Containers don’t write data permanently to any **storage location**. Docker storage must be configured if you would like your container to store data permanently. The data doesn’t prevail when the container is **deleted (using the remove command)**; this happens because when the **container is deleted**, the writable layer is also **deleted**. If the data is stored **outside** the container you can use it even if the container no longer exists.

If a container **crashes** and can’t be restored/restarted the data is gone! But, normally containers can be restarted and continued – in that case, the data is not lost. So, it’s always advisable moreover mandatory to **mount** the data outside the container.

Majorly used docker storage type

1. Volume

2. Bind Mount

3. Tmpfs mount

## Docker Volume

![Docker-storage-view-2.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661327711386/f2D8ulGXu.png align="left")

Docker volume is the most commonly used technology for the **permanent storage** of container data. Docker volume is managed by Docker itself and has a dedicated filesystem on the host, doesn’t depend upon the filesystem structure on the host. Docker volumes are explicitly managed via the Docker command line and can be created alone or during container initialization. The command used is `docker volume create`.

When stopping or deleting a container, the Docker volume remains permanently stored. The volumes are often manually deleted with the `docker volume prune` command. Multiple containers can be connected to the same Docker volume

### commands Use with docker volumes
```
docker volume create	#Create a volume
docker volume inspect	#Display detailed information on one or more volumes
docker volume Is	        #List volumes
docker volume prune	    #Remove all unused local volumes
docker volume rm	        #Remove one or more volumes

```

### **Docker Volume Use Cases**

- To share data between **multiple containers.**
- Back up and restore data.
- Connect to a remote location (cloud).
- Dedicated container-only filesystem.

## Docker Bind Mount

Docker bind mount is the second **permanent storage** option but with more limited options than Docker volume. It can’t be managed via Docker CLI and is totally dependent on the availability of the filesystem of the host. A host filesystem can be created when running a container. Bind mounts are a sort of **superset of Volumes** (**named or unnamed**).

**Commands:bind mount**: note that the host path should start with ‘/’. Use $(pwd) for convenience.

```
docker container run -v /host-path:/container-path image-name
```

**unnamed volume**: creates a folder in the host with an arbitrary name

```
docker container run -v /container-path image-name
```

**named volume**: should not start with ‘/’ as this is reserved for bind mount. `volume-name` is not a full path here. the command will cause a folder to be created with the path “/var/lib/docker/volume-name” in the host.

```
docker container run -v volume-name/container-path image-name
```

## tmpfs Mounts

tmpfs is a third storage option that is **not permanent** like Docker volume or bind mount. The data is written directly onto the host’s memory and deleted when the container is stopped. Very useful when it involves **sensitive** data that you simply don’t want to be permanent. A really significant difference is that containers can’t share tmpfs space unless they’re running on Linux OS. Two flags are used when creating tmpfs volume: tmpfs and mount. **Mount flag** is newer and supports multiple options during container startup.  Temporary filesystems are written to RAM (or to your swap file if RAM is filling up) and not to the host or the container’s own filesystem layer at Docker com: Docker tmpfs.

**Commands:**

```
docker run -d --name tmptest --mount type=tmpfs,destination=/app nginx:latest
```

```
docker run -d --name tmptest --tmpfs /app nginx:latest
```

# Network File System (NFS)

![docker-nfs-1-373x300.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661327597974/1p5Vw7PBD.png align="left")

When you create a container, you are going to be fairly limited in the amount of space in that container. This is exacerbated when you run multiple containers on the same host. So, to get around that, you could mount an NFS share at the start of the container. With NFS, my storage limits are only what my storage provider dictates. Access to a unified set of data across all containers. One thing you’ll notice while learning Docker is that the container OS is nothing like a virtual machine. These containers are essentially thin clients and are missing some functionality by design.

### **Creating The NFS Docker Volume:**

Here is the command to create an NFS type Docker volume in reading / write access from an existing NFS export :

```
# docker volume create --driver local --opt type=nfs --opt o=addr=<adresse ip serveur nfs>,rw --opt device=:<chemin export nfs> <nom du volume NFS Docker>

```

# Docker Storage Driver

![howitworks_graphic1.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1661327748987/3XW7Hje15.png align="left")

Docker storage driver is **liable**
 for creating a container write layer to log all the changes during c**ontainer runtime**
. When a container is started with an image, **all layers**
 that are part of the image are locked and read-only. Changes are written to the **recording layer**
 and deleted when the container is stopped. The driver creates a **Union filesystem**
 that allows filesystems to be shared from all layers. This is the default way to store data in a container unless the storage technologies described above are used. It’s important to notice that an additional driver layer brings additional performance overhead. It’s not recommended to use the default storage option for **write-intensive**
 containers like database systems.