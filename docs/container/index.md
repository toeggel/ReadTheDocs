---
tags:
  - container
aliases:
  - k8s
  - OS
  - docker
---

# Containerization

> [!ABSTRACT] **Docker** is used to package and ship the app, whereas, **Kubernetes** deploys and scales the app, and **OpenShift** provides an additional layer of management and automation on top of Kubernetes, enhancing its features and simplifying its use.

- Different services in an app have different requirements, dependencies, libraries, ... A specific environment is therefore needed. This can be achieved by using a VM but it might be difficult to set it up to fulfill all those different requirements. Containers allow to setup an optimized environment for each part of the application.
- Container use less resources and are generally faster and more efficient than VMs. This is because VMs simulate the hardware and each VM is running its own OS. Containers only virtualize the OS.
- If we want to scale our application individually (e.g. different services) we would need to create multiple VMs (which generally take more resources than containers). With a container setup we can easily scale individually.

**3 Step process**

1. manifest (container description) (e.g. a docker file). 
	- This is used to create the image.
2. image
	- a snapshot of the software with all the dependencies needed to run it (incl. OS).
	- executable software
3. (actual) container
	- actual running software

# Docker

 Docker is a containerization platform that allows developers to build and run applications in isolated containers with all their dependencies

 see: [docker-cheat-sheet](docker-cheat-sheet.md)

## docker vs docker-compose

The `docker` cli is used when managing individual containers on a docker engine. It is the client command line to access the docker daemon api.

The `docker-compose` cli can be used to manage a **multi-container application**. It also moves many of the options you would enter on the `docker run` cli into the `docker-compose.yml` file for easier reuse. It works as a front end "script" on top of the same docker api used by `docker`, so you can do everything `docker-compose` does with `docker` commands and a lot of shell scripting. See [this documentation on docker-compose](https://docs.docker.com/compose/overview/) for more details.

### Volumes

Docker usually persists data within a container and survives container stops (`docker stop`) and starts (`docker start`). However, if a container gets removed (`docker rm`), everything in the container is deleted. This can be prevented by making use of _data volumes_ which persist data even if the associated containers are deleted. Data can be mapped to either a host directory (e.g. `C:\SQL`) or a data volume container.

# Kubernetes (k8s)

Kubernetes is a platform that orchestrates containers from different runtimes, including Docker, across a cluster of servers, providing features like load balancing, self-healing, and automated rollouts.

Kubernetes adds the ability to orchestrate Docker containers across multi-host installations.

# OpenShift (OS)

Platform as a Service

**An abstraction layer above Kubernetes** which makes the task (like deploying) a bit easier to handle. OpenShift uses an opinionated stack compared to Kubernetes which you have (can) decide yourself.

## How OpenShift works

Can be hooked to a source control (e.g. git). After a commit it trigger Jenkins to build a docker image out of the code and publishes to a registry. Afterwards it gets pushed into a Kubernetes cluster.
