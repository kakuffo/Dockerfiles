# Dockerfiles

The following is an overview of the use of Docker files, and the commands available for creating Docker images 
(assembling of stateless), which when runned become Docker containers suitable for hosting application.
This document will leverage the official [Docker Docker run reference](https://docs.docker.com/engine/reference/run/),
and illustrate the technique for employing, and using these commands.

# What is Docker
Docker is an open source containerisation platform for building and containerising applications. Docker Engine acts 
as a client-server application with:

* Docker Engine
    * Docker Server 
        * Docker Storage
        * Docker Container
            * runC
                * Namespace
                * Cgroups
                * Filesystem access
                * Linux Security
            * Snapshotter
                * Storage Drive
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
| Cgroups|
| Filesystem access|
| Linux Security|
| Snapshotter|
| Storage Drive|
| Docker Network|
| Sandbox|
| Endpoint(API)|
| Network Driver|
| Host|
| Bridge|
| Overlay|
| macvian|
| IPAM Drive| 
| Docker REST API|
| Docker CLI|
        
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

# How to 

![Docker Components](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2019/09/Picture1-15.png)


have a docker folder which holds each applications and their configuration. Here's an example project folder hierarchy for a web application that has a database.

docker-compose.yml
docker
├── web
│   └── Dockerfile
└── db
    └── Dockerfile