# Dockerfiles

The following is an overview of the use of Docker files, and the commands available for creating Docker images 
(assembling of stateless), which when runned become Docker containers suitable for hosting application.

# What is Docker
Docker is an open source containerisation platform for building and containerising applications. Docker Engine acts 
as a client-server application with:

* Docker Engine - is the lightweight and powerful open source containerization technology combined with a work flow for building and containerizing your applications.)
    * Docker Server 
        * Docker Persistence Storage
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