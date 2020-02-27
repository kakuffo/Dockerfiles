# Dockerfiles
The following is an overview of the use of Docker files, and the commands available for creating Docker images, 
which when executed, and instantiated become Docker containers suitable for hosting application.
This document will leverage the official [ockerfile reference](https://docs.docker.com/engine/reference/builder/),
and illustrate the technique for employing, and using these commands.  This part of my work will create a collection
of DockerFiles for creating a Docker container of the many applications.  These will be used to illustrate my mastery
of DockerFiles !!
In a typical tech project a DockerFile is used by all in the development process to 
## DockerFile Best Practice
[![IMAGE ALT TEXT HERE](https://github.com/kakuffo/Dockerfiles/blob/master/vid/Recording.jpeg)
DockerFile best practice demands that each instruction creates one layer, and the start of each instruction starts with a reserved work
:
```Shell
FROM node:10.15.0-alpine AS build

RUN apk add git nodejs
RUN rm -rf /var/cache/apk/*
WORKDIR /usr/src/app
ARG application_name
COPY ./$application_name .
RUN npm install
RUN npm rebuild node-sass
RUN npm run build-dev

FROM nginx

ARG application_port
EXPOSE $application_port/tcp

COPY --from=build /usr/src/app/nginx/nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=build /usr/src/app/www /usr/share/nginx/html/admin

ENTRYPOINT nginx -g 'daemon off;'
```

MAINTAINER
Usage:

MAINTAINER <name>
The MAINTAINER instruction allows you to set the Author field of the generated images.

Reference

## RUN
### Usage:

RUN <command> (shell form, the command is run in a shell, which by default is /bin/sh -c on Linux or cmd /S /C on Windows)
```Shell
docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
```
#### Information:

The exec form makes it possible to avoid shell string munging, and to RUN commands using a base image that does not contain the specified shell executable.
The default shell for the shell form can be changed using the SHELL command.
Normal shell processing does not occur when using the exec form. For example, RUN ["echo", "$HOME"] will not do variable substitution on $HOME.
Reference - Best Practices

|Name, shorthand|Default	Description |
|:----------------|:------------------------------------------------------------|
|--add-host		|Add a custom host-to-IP mapping (host:ip)
|--attach , -a		|Attach to STDIN, STDOUT or STDERR
|--blkio-weight		|Block IO (relative weight), between 10 and 1000, or 0 to disable (default 0)
|--blkio-weight-device		|Block IO weight (relative device weight)
|--cap-add		|Add Linux capabilities
|--cap-drop		|Drop Linux capabilities
|--cgroup-parent		|Optional parent cgroup for the container
|--cidfile		|Write the container ID to the file
|--cpu-count		|CPU count (Windows only)
|--cpu-percent		|CPU percent (Windows only)
|--cpu-period		|Limit CPU CFS (Completely Fair Scheduler) period
|--cpu-quota		|Limit CPU CFS (Completely Fair Scheduler) quota
|--cpu-rt-period		|API 1.25+
|Limit CPU real-time |period in microseconds
|--cpu-rt-runtime	|	API 1.25+
|Limit CPU real-time |runtime in microseconds
|--cpu-shares , -c	|	CPU shares (relative weight)
|--cpus		API 1.25+|
|Number of CPUs|
|--cpuset-cpus		|CPUs in which to allow execution (0-3, 0,1)
|--cpuset-mems		|MEMs in which to allow execution (0-3, 0,1)
|--detach , -d		|Run container in background and print container ID
|--detach-keys		|Override the key sequence for detaching a container
|--device		|Add a host device to the container
|--device-cgroup-rule		|Add a rule to the cgroup allowed devices list
|--device-read-bps		|Limit read rate (bytes per second) from a device
|--device-read-iops		|Limit read rate (IO per second) from a device
|--device-write-bps		|Limit write rate (bytes per second) to a device
|--device-write-iops	|	Limit write rate (IO per second) to a device
|--disable-content-trust|	true	Skip image verification
|--dns		|Set custom DNS servers
|--dns-opt	|	Set DNS options
|--dns-option	|	Set DNS options
|--dns-search	|	Set custom DNS search domains
|--domainname	|	Container NIS domain name
|--entrypoint	|	Overwrite the default ENTRYPOINT of the image
|--env , -e		|Set environment variables
|--env-file		|Read in a file of environment variables
|--expose		|Expose a port or a range of ports
|--gpus		|API 1.40+
|GPU |devices to add to the container (‘all’ to pass all GPUs)
|--group-add	|	Add additional groups to join
|--health-cmd	|	Command to run to check health
|--health-interval	|	Time between running the check (ms|s|m|h) (default 0s)
|--health-retries	|	Consecutive failures needed to report unhealthy
|--health-start-period |		API 1.29+
|Start period for the container to initialize before starting health-retries countdown (ms|s|m|h) (default 0s)
|--health-timeout	|	Maximum time to allow one check to run (ms|s|m|h) (default 0s)
|--help		|Print usage
|--hostname , -h|		Container host name
|--init		| API 1.25+
|Run an init inside the container that forwards signals and reaps processes
|--interactive , -i	|	Keep STDIN open even if not attached
|--io-maxbandwidth	|	Maximum IO bandwidth limit for the system drive (Windows only)
|--io-maxiops	|	Maximum IOps limit for the system drive (Windows only)
|--ip	|	IPv4 address (e.g., 172.30.100.104)
|--ip6	|	IPv6 address (e.g., 2001:db8::33)
|--ipc	|	IPC mode to use
|--isolation	|	Container isolation technology
|--kernel-memory|		Kernel memory limit
|--label , -l	|	Set meta data on a container
|--label-file	|	Read in a line delimited file of labels
|--link		| Add link to another container
|--link-local-ip	|	Container IPv4/IPv6 link-local addresses
|--log-driver	|	Logging driver for the container
|--log-opt	|	Log driver options
|--mac-address	|	Container MAC address (e.g., 92:d0:c6:0a:29:33)
|--memory , -m	|	Memory limit
|--memory-reservation	|	Memory soft limit
|--memory-swap	|	Swap limit equal to memory plus swap: ‘-1’ to enable unlimited swap
|--memory-swappiness	| -1	Tune container memory swappiness (0 to 100)
|--mount|		Attach a filesystem mount to the container
|--name	|	Assign a name to the container
|--net	|	Connect a container to a network
|--net-alias	|	Add network-scoped alias for the container
|--network		|Connect a container to a network
|--network-alias	|	Add network-scoped alias for the container
|--no-healthcheck	|	Disable any container-specified HEALTHCHECK
|--oom-kill-disable	|	Disable OOM Killer
|--oom-score-adj	|	Tune host’s OOM preferences (-1000 to 1000)
|--pid		| PID namespace to use
|--pids-limit	|	Tune container pids limit (set -1 for unlimited)
|--platform		|experimental (daemon)API 1.32+
|Set platform |if server is multi-platform capable
|--privileged		|Give extended privileges to this container
|--publish , -p		|Publish a container’s port(s) to the host
|--publish-all , -P	|	Publish all exposed ports to random ports
|--read-only	|	Mount the container’s root filesystem as read only
|--restart	|no	Restart policy to apply when a container exits
|--rm		|Automatically remove the container when it exits
|--runtime		|Runtime to use for this container
|--security-opt	|	Security Options
|--shm-size		|Size of /dev/shm
|--sig-proxy	|true	Proxy received signals to the process
|--stop-signal	|SIGTERM	Signal to stop a container
|--stop-timeout	|	API 1.25+
|Timeout (in seconds) to stop a container
|--storage-opt	|	Storage driver options for the container
|--sysctl		|Sysctl options
|--tmpfs		|Mount a tmpfs directory
|--tty , -t		|Allocate a pseudo-TTY
|--ulimit		|Ulimit options
|--user , -u	|	Username or UID (format: <name|uid>[:<group|gid>])
|--userns		|User namespace to use
|--uts		|UTS namespace to use
|--volume , -v		|Bind mount a volume
|--volume-driver	|	Optional volume driver for the container
|--volumes-from		|Mount volumes from the specified container(s)
|--workdir , -w		|Working directory inside the container

## CMD
### Usage:

```Shell
CMD ["<executable>","<param1>","<param2>"] (exec form, this is the preferred form)
CMD ["<param1>","<param2>"] (as default parameters to ENTRYPOINT)
CMD <command> <param1> <param2> (shell form)
```
#### Information:

The main purpose of a CMD is to provide defaults for an executing container. These defaults can include an executable, or they can omit the executable, in which case you must specify an ENTRYPOINT instruction as well.
There can only be one CMD instruction in a Dockerfile. If you list more than one CMD then only the last CMD will take effect.
If CMD is used to provide default arguments for the ENTRYPOINT instruction, both the CMD and ENTRYPOINT instructions should be specified with the JSON array format.
If the user specifies arguments to docker run then they will override the default specified in CMD.
Normal shell processing does not occur when using the exec form. For example, CMD ["echo", "$HOME"] will not do variable substitution on $HOME.
Reference - Best Practices

## LABEL
### Usage:

```Shell
LABEL <key>=<value> [<key>=<value> ...]
```
#### Information:

The LABEL instruction adds metadata to an image.
To include spaces within a LABEL value, use quotes and backslashes as you would in command-line parsing.
Labels are additive including LABELs in FROM images.
If Docker encounters a label/key that already exists, the new value overrides any previous labels with identical keys.
To view an image’s labels, use the docker inspect command. They will be under the "Labels" JSON attribute.
Reference - Best Practices

## EXPOSE
### Usage:

```Shell
EXPOSE <port> [<port> ...]
```
#### Information:

Informs Docker that the container listens on the specified network port(s) at runtime.
EXPOSE does not make the ports of the container accessible to the host.
Reference - Best Practices

## ENV
### Usage:

```Shell
ENV <key> <value>
ENV <key>=<value> [<key>=<value> ...]
```
#### Information:

The ENV instruction sets the environment variable <key> to the value <value>.
The value will be in the environment of all “descendant” Dockerfile commands and can be replaced inline as well.
The environment variables set using ENV will persist when a container is run from the resulting image.
The first form will set a single variable to a value with the entire string after the first space being treated as the <value> - including characters such as spaces and quotes.
Reference - Best Practices

## ADD
### Usage:

```Shell
ADD <src> [<src> ...] <dest>
ADD ["<src>", ... "<dest>"] (this form is required for paths containing whitespace)
```
#### Information:

Copies new files, directories, or remote file URLs from <src> and adds them to the filesystem of the image at the path <dest>.
<src> may contain wildcards and matching will be done using Go’s filepath.Match rules.
If <src> is a file or directory, then they must be relative to the source directory that is being built (the context of the build).
<dest> is an absolute path, or a path relative to WORKDIR.
If <dest> doesn’t exist, it is created along with all missing directories in its path.
Reference - Best Practices

## COPY
### Usage:

```Shell
COPY <src> [<src> ...] <dest>
COPY ["<src>", ... "<dest>"] (this form is required for paths containing whitespace)
```
#### Information:

Copies new files or directories from <src> and adds them to the filesystem of the image at the path <dest>.
<src> may contain wildcards and matching will be done using Go’s filepath.Match rules.
<src> must be relative to the source directory that is being built (the context of the build).
<dest> is an absolute path, or a path relative to WORKDIR.
If <dest> doesn’t exist, it is created along with all missing directories in its path.
Reference - Best Practices

## ENTRYPOINT
### Usage:
```Shell
ENTRYPOINT ["<executable>", "<param1>", "<param2>"] (exec form, preferred)
ENTRYPOINT <command> <param1> <param2> (shell form)
```
#### Information:

Allows you to configure a container that will run as an executable.
Command line arguments to docker run <image> will be appended after all elements in an exec form ENTRYPOINT and will override all elements specified using CMD.
The shell form prevents any CMD or run command line arguments from being used, but the ENTRYPOINT will start via the shell. This means the executable will not be PID 1 nor will it receive UNIX signals. Prepend exec to get around this drawback.
Only the last ENTRYPOINT instruction in the Dockerfile will have an effect.
Reference - Best Practices

## VOLUME
### Usage:
```Shell
VOLUME ["<path>", ...]
VOLUME <path> [<path> ...]
```
Creates a mount point with the specified name and marks it as holding externally mounted volumes from native host or other containers.

Reference - Best Practices

## USER
### Usage:
```Shell
USER <username | UID>
```
The USER instruction sets the user name or UID to use when running the image and for any RUN, CMD and ENTRYPOINT instructions that follow it in the Dockerfile.

Reference - Best Practices

## WORKDIR
### Usage:

```Shell
WORKDIR </path/to/workdir>
```
#### Information:

Sets the working directory for any RUN, CMD, ENTRYPOINT, COPY, and ADD instructions that follow it.
It can be used multiple times in the one Dockerfile. If a relative path is provided, it will be relative to the path of the previous WORKDIR instruction.
Reference - Best Practices

## ARG
### Usage:

```Shell
ARG <name>[=<default value>]
```
#### Information:

Defines a variable that users can pass at build-time to the builder with the docker build command using the --build-arg <varname>=<value> flag.
Multiple variables may be defined by specifying ARG multiple times.
It is not recommended to use build-time variables for passing secrets like github keys, user credentials, etc. Build-time variable values are visible to any user of the image with the docker history command.
Environment variables defined using the ENV instruction always override an ARG instruction of the same name.
Docker has a set of predefined ARG variables that you can use without a corresponding ARG instruction in the Dockerfile.
HTTP_PROXY and http_proxy
HTTPS_PROXY and https_proxy
FTP_PROXY and ftp_proxy
NO_PROXY and no_proxy
Reference

## ONBUILD
###  Usage:

```Shell
ONBUILD <Dockerfile INSTRUCTION>
```

#### Information:

Adds to the image a trigger instruction to be executed at a later time, when the image is used as the base for another build. The trigger will be executed in the context of the downstream build, as if it had been inserted immediately after the FROM instruction in the downstream Dockerfile.
Any build instruction can be registered as a trigger.
Triggers are inherited by the "child" build only. In other words, they are not inherited by "grand-children" builds.
The ONBUILD instruction may not trigger FROM, MAINTAINER, or ONBUILD instructions.
Reference - Best Practices

## STOPSIGNAL
### Usage:

```Shell
STOPSIGNAL <signal>
```

The STOPSIGNAL instruction sets the system call signal that will be sent to the container to exit. This signal can be a valid unsigned number that matches a position in the kernel’s syscall table, for instance 9, or a signal name in the format SIGNAME, for instance SIGKILL.

Reference

## HEALTHCHECK
### Usage:
```Shell
HEALTHCHECK [<options>] CMD <command> (check container health by running a command inside the container)
HEALTHCHECK NONE (disable any healthcheck inherited from the base image)
```
#### Information:

Tells Docker how to test a container to check that it is still working
Whenever a health check passes, it becomes healthy. After a certain number of consecutive failures, it becomes unhealthy.
The <options> that can appear are...
```DOS
--interval=<duration> (default: 30s)
--timeout=<duration> (default: 30s)
--retries=<number> (default: 3)
```
The health check will first run interval seconds after the container is started, and then again interval seconds after each previous check completes. If a single run of the check takes longer than timeout seconds then the check is considered to have failed. It takes retries consecutive failures of the health check for the container to be considered unhealthy.
There can only be one HEALTHCHECK instruction in a Dockerfile. If you list more than one then only the last HEALTHCHECK will take effect.
<command> can be either a shell command or an exec JSON array.
The command's exit status indicates the health status of the container.
0: success - the container is healthy and ready for use
1: unhealthy - the container is not working correctly
2: reserved - do not use this exit code
The first 4096 bytes of stdout and stderr from the <command> are stored and can be queried with docker inspect.
When the health status of a container changes, a health_status event is generated with the new status.
Reference

## SHELL
### Usage:

```Shell
SHELL ["<executable>", "<param1>", "<param2>"]
```

#### Information:

Allows the default shell used for the shell form of commands to be overridden.
Each SHELL instruction overrides all previous SHELL instructions, and affects all subsequent instructions.
Allows an alternate shell be used such as zsh, csh, tcsh, powershell, and others.