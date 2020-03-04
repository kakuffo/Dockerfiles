# Dockerfiles
The following is an overview of the use of Docker files, and the commands available for creating Docker images 
(assembling of stateless), which when runned become Docker containers suitable for hosting application.
This document will leverage the official [Docker Docker run reference](https://docs.docker.com/engine/reference/run/),
and illustrate the technique for employing, and using these commands.

# What is Docker
Docker is an open source containerisation platform for building and containerising applications. Docker Engine acts 
as a client-server application with several components, which together forms the Docker platform.  I have taken time
list these components, and given the official documentation to each.:

* Docker Engine
    * Docker Server - [Docker daemon documentation](https://docs.docker.com/engine/reference/commandline/dockerd/) 
        * Docker Storage - [Docker Storage documentation](https://success.docker.com/article/an-introduction-to-storage-solutions-for-docker-enterprise)
        * Docker Container - [Docker Container documentation](https://www.docker.com/resources/what-container)
            * runC - [Docker RunC documentation](https://docs.docker.com/engine/reference/run/) 
                * Namespace - [Docker Namespaces documentation](https://docs.docker.com/engine/docker-overview/)
                * Cgroups - [Docker Cgroups documentation](https://docs.docker.com/engine/docker-overview/)
                * Filesystem - [Docker Filesystem documentation](https://docs.docker.com/storage/) 
                * Linux Security - [Linux Security documentation](https://docs.docker.com/engine/security/security/)
            * Snapshot - [BTRFS Snapshot documentation](https://docs.docker.com/storage/storagedriver/btrfs-driver/) 
                * Storage Driver - [Docker Storage Driver documentation](https://docs.docker.com/storage/storagedriver/select-storage-driver/) 
        * Docker Network - [Docker Network documentation](https://docs.docker.com/engine/reference/commandline/network_create/)
            * Sandbox - [Docker SandBox documentation](https://docs.docker.com/engine/security/trust/trust_sandbox/) 
            * Endpoint(API) - [Docker API](https://docs.docker.com/engine/api/v1.24/)
            * Network Driver - [Docker Network](https://docs.docker.com/network/)
                * Host - [Docker Host](https://docs.docker.com/network/host/)
                * Bridge - [Docker Dridge](https://docs.docker.com/network/network-tutorial-standalone/)
                * Overlay - [Docker Overlay](https://docs.docker.com/network/overlay/)
                * macvian - [Docker macvlan](https://docs.docker.com/network/macvlan/)
            * IPAM Drive - [Docker DRIVER](https://docs.docker.com/engine/reference/commandline/network_create/) 
    * Docker REST API - [Docker Engine API](https://docs.docker.com/engine/api/)|
    * Docker CLI - [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/) 
 
|Docker Component       |What it does           | 
|:-----------------------|:---------------------|
| Docker Engine         | Docker Engine is an open source containerization technology for building and containerizing your applications|
| Docker Server (daemon)| The Docker daemon (dockerd) listens for Docker API requests and manages Docker objects such as images, containers, networks, and volumes. A daemon can also communicate with other daemons to manage Docker services.|
| Docker Storage| The file system in docker is managed by the container runtime and it uses a storage driver to write to the containers writable layer. However to persist data outside the container, Docker Enterprise Platform; volumes, bind mounts and tmpfs mounts.|
| Docker Container | Docker Containers are an abstraction at the app layer that packages code and dependencies together. | [Docker Container](https://www.docker.com/resources/what-container)|
| runC| runC, a lightweight universal container runtime, is a command-line tool for spawning and running containers according to the Open Container Initiative (OCI) specification.  This page gathers resources about managing containers in runC.|
| Namespace| Docker uses a technology called namespaces to provide the isolated workspace called the container. When you run a container, Docker creates a set of namespaces for that container.|
| Cgroups| A cgroup limits an application to a specific set of resources. Control groups allow Docker Engine to share available hardware resources to containers and optionally enforce limits and constraints.|
| Filesystem|Volumes are stored in a part of the host filesystem which is managed by Docker (/var/lib/docker/volumes/ on Linux). Non-Docker processes should not modify this part of the filesystem. Volumes are the best way to persist data in Docker.|
| Linux Security|Docker containers are very similar to LXC containers, and they have similar security features. When you start a container with docker run, behind the scenes Docker creates a set of namespaces and control groups for the container.|
| Snapshot|Docker’s btrfs storage driver leverages many Btrfs features for image and container management. Among these features are block-level operations, thin provisioning, copy-on-write snapshots, and ease of administration. You can easily combine multiple physical block devices into a single Btrfs filesystem.|
| Storage Driver|Docker supports several different storage drivers, using a pluggable architecture. The storage driver controls how images and containers are stored and managed on your Docker host.|
| Docker Network|The client and daemon API must both be at least 1.21 to use this command. Use the docker version command on the client to check your client and daemon API versions.|
| Sandbox|Docker sandbox allows you to configure and try trust operations locally without impacting your production images.|
| Endpoint(API)|The Engine API uses standard HTTP status codes to indicate the success or failure of the API call.|
| Network Driver|Docker containers and services are so powerful is that you can connect them together, or connect them to non-Docker workloads. Docker containers and services do not even need to be aware that they are deployed on Docker, or whether their peers are also Docker workloads or not.|
| Host|Docker host (the container shares the host’s networking namespace), and the container does not get its own IP-address allocated. For instance, if you run a container which binds to port 80 and you use host networking, the container’s application is available on port 80 on the host’s IP address.|
| Bridge|Docker Use the default bridge network demonstrates how to use the default bridge network that Docker sets up for you automatically. This network is not the best choice for production systems.|
| Overlay|Docker overlay network driver creates a distributed network among multiple Docker daemon hosts. This network sits on top of (overlays) the host-specific networks, allowing containers connected to it (including swarm service containers) to communicate securely when encryption is enabled.|
| macvlan|Some applications, especially legacy applications or applications which monitor network traffic, expect to be directly connected to the physical network.|
| IPAM Drive|Docker DRIVER accepts bridge or overlay which are the built-in network drivers.|
| Docker REST API|Docker provides an API for interacting with the Docker daemon (called the Docker Engine API), as well as SDKs for Go and Python.|
| Docker CLI|Depending on your Docker system configuration, you may be required to preface each docker command with sudo. |

# Kubernetes kubectl integration with Docker

You can use the Kubernetes command line tool kubectl to interact with the API Server. Using kubectl is straightforward 
if you are familiar with the Docker command line tool. However, there are a few differences between the docker commands 
and the kubectl commands. The following sections show a docker sub-command and describe the equivalent kubectl command.

## Docker run
To run an nginx Deployment and expose the Deployment, see kubectl run.
docker:

```bash
docker run -d --restart=always -e DOMAIN=cluster --name nginx-app -p 80:80 nginx
```
## Docker ps
To list what is currently running, see kubectl get.
docker:

```bash
docker ps -a
```


```bash

```
## Docker attach

## Docker exec

## Docker logs

## Docker stop and docker rm

## Docker login

## Docker version

## Docker info

 
