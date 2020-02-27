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
    * Docker Server 
        * Docker Storage
        * Docker Container
            * runC
                * Namespace
                * Cgroups
                * Filesystem
                * Linux Security
            * Snapshot
                * Storage Driver
        * Docker Network
            * Sandbox
            * Endpoint(API)
            * Network Driver
                * Host
                * Bridge
                * Overlay
                * macvian
            * IPAM Drive 
    * Docker REST API
    * Docker CLI
 
|Docker Component       |What it does           | Documentation Link    | 
|-----------------------|:---------------------:|:----------------------:
| Docker Engine         | Docker Engine is an open source containerization technology for building and containerizing your applications| [Docker Engine Documentation](https://docs.docker.com/install/linux/docker-ce/ubuntu/)                      |                       |
| Docker Server (daemon)         | The Docker daemon (dockerd) listens for Docker API requests and manages Docker objects such as images, containers, networks, and volumes. A daemon can also communicate with other daemons to manage Docker services.| [Docker daemon documentation]()                      |
| Docker Storage|The file system in docker is managed by the container runtime and it uses a storage driver to write to the containers writable layer. However to persist data outside the container, Docker Enterprise Platform; volumes, bind mounts and tmpfs mounts. |[Docker Storage](https://success.docker.com/article/an-introduction-to-storage-solutions-for-docker-enterprise)|                      |
| Docker Container |Docker Containers are an abstraction at the app layer that packages code and dependencies together. | [Docker Container](https://www.docker.com/resources/what-container)|
| runC|runC, a lightweight universal container runtime, is a command-line tool for spawning and running containers according to the Open Container Initiative (OCI) specification.  This page gathers resources about managing containers in runC.| [Docker RunC](https://docs.docker.com/engine/reference/run/)  |
| Namespace|Docker uses a technology called namespaces to provide the isolated workspace called the container. When you run a container, Docker creates a set of namespaces for that container.|[Docker Namespaces](https://docs.docker.com/engine/docker-overview/) |
| Cgroups|A cgroup limits an application to a specific set of resources. Control groups allow Docker Engine to share available hardware resources to containers and optionally enforce limits and constraints.|[Docker Cgroups](https://docs.docker.com/engine/docker-overview/)|
| Filesystem|Volumes are stored in a part of the host filesystem which is managed by Docker (/var/lib/docker/volumes/ on Linux). Non-Docker processes should not modify this part of the filesystem. Volumes are the best way to persist data in Docker.|[Docker Filesystem](https://docs.docker.com/storage/)|
| Linux Security|Docker containers are very similar to LXC containers, and they have similar security features. When you start a container with docker run, behind the scenes Docker creates a set of namespaces and control groups for the container.|[Linux Security](https://docs.docker.com/engine/security/security/)
| Snapshot|Docker’s btrfs storage driver leverages many Btrfs features for image and container management. Among these features are block-level operations, thin provisioning, copy-on-write snapshots, and ease of administration. You can easily combine multiple physical block devices into a single Btrfs filesystem.|[BTRFS Snapshot](https://docs.docker.com/storage/storagedriver/btrfs-driver/)|
| Storage Driver|Docker supports several different storage drivers, using a pluggable architecture. The storage driver controls how images and containers are stored and managed on your Docker host.|[Docker Storage Driver](https://docs.docker.com/storage/storagedriver/select-storage-driver/)|
| Docker Network|The client and daemon API must both be at least 1.21 to use this command. Use the docker version command on the client to check your client and daemon API versions.|[Docker Network](https://docs.docker.com/engine/reference/commandline/network_create/)|
| Sandbox|Docker sandbox allows you to configure and try trust operations locally without impacting your production images.|[Docker SandBox](https://docs.docker.com/engine/security/trust/trust_sandbox/)|
| Endpoint(API)|The Engine API uses standard HTTP status codes to indicate the success or failure of the API call.|[Docker API](https://docs.docker.com/engine/api/v1.24/)|
| Network Driver|Docker containers and services are so powerful is that you can connect them together, or connect them to non-Docker workloads. Docker containers and services do not even need to be aware that they are deployed on Docker, or whether their peers are also Docker workloads or not.|[Docker Network](https://docs.docker.com/network/)|
| Host|Docker host (the container shares the host’s networking namespace), and the container does not get its own IP-address allocated. For instance, if you run a container which binds to port 80 and you use host networking, the container’s application is available on port 80 on the host’s IP address.|[Docker Host](https://docs.docker.com/network/host/)|
| Bridge|Docker Use the default bridge network demonstrates how to use the default bridge network that Docker sets up for you automatically. This network is not the best choice for production systems.|[Docker Dridge](https://docs.docker.com/network/network-tutorial-standalone/)|
| Overlay|Docker overlay network driver creates a distributed network among multiple Docker daemon hosts. This network sits on top of (overlays) the host-specific networks, allowing containers connected to it (including swarm service containers) to communicate securely when encryption is enabled.|[Docker Overlay](https://docs.docker.com/network/overlay/)|
| macvlan|Some applications, especially legacy applications or applications which monitor network traffic, expect to be directly connected to the physical network.|[Docker macvlan](https://docs.docker.com/network/macvlan/)|
| IPAM Drive|Docker DRIVER accepts bridge or overlay which are the built-in network drivers.|[Docker DRIVER](https://docs.docker.com/engine/reference/commandline/network_create/)| 
| Docker REST API|Docker provides an API for interacting with the Docker daemon (called the Docker Engine API), as well as SDKs for Go and Python.|[Docker Engine API](https://docs.docker.com/engine/api/)|
| Docker CLI|Depending on your Docker system configuration, you may be required to preface each docker command with sudo. |[Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)|
        
* A server with a long-running daemon process docker.
* APIs which specify interfaces that programs can use to talk to and instruct the Docker daemon.
* A command line interface (CLI) client

![Docker Architecture](https://vmarena.com/wp-content/uploads/2018/08/DOCK02.png)

# What is Docker a Image
A Docker image is an inactive (stateless), and a collection of files representitive of Host OS, Infrastructure, 
and docker.  A Docker image translates into a Docker Container once it has been activated by the Run command, and 

Docker’s Client
Docker Host
Docker Objects
Docker’s Registry 

# How to docker01.png


![Docker Components](https://github.com/kakuffo/Dockerfiles/blob/master/vid/docker01.png?raw=true)


have a docker folder which holds each applications and their configuration. Here's an example project folder hierarchy for a web application that has a database.

docker-compose.yml
docker
├── web
│   └── Dockerfile
└── db
    └── Dockerfile