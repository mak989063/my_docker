# Docker Fundamentals

## Learning Objectives

After completing this module, one should understand basics of docker

* Why Docker was created
* What problems Docker solves
* What is a Linux process
* What is a Container
* Containers vs Virtual Machines
* Linux Namespaces
* Linux cgroups
* Union Filesystem
* How Docker uses Linux Kernel features

---

## Why Docker Was Created

Before Docker, applications often failed when moved between environments due to dependency and configuration differences.

Common issues:

* Works on my machine problem
* Dependency conflicts
* Environment inconsistency
* Difficult deployments

Docker solves these issues by packaging the application together with its dependencies into a portable container.

---

## What is Docker?

Docker is an open-source containerization platform that enables developers to package applications and their dependencies into lightweight, isolated containers.

Key benefits:

* Portability
* Consistency
* Faster deployments
* Better resource utilization

---

## What is a Linux Process?

A process is a running instance of a program.

Examples:

```bash
nginx
java
python app.py
sleep 100
```

Containers are essentially isolated Linux processes.

---

## What is a Container?

A container is an isolated process running on the host operating system.

A container has its own:

* Process tree
* Network stack
* Filesystem view
* Resource limits

while sharing the host kernel.

---

## Containers vs Virtual Machines

| Feature        | Container     | Virtual Machine |
| -------------- | ------------- | --------------- |
| Kernel         | Shared        | Separate        |
| Startup Time   | Seconds       | Minutes         |
| Size           | MBs           | GBs             |
| Resource Usage | Low           | High            |
| Isolation      | Process Level | Hardware Level  |

---

## Linux Namespaces

Namespaces provide isolation.

Types:

* PID Namespace
* Network Namespace
* Mount Namespace
* UTS Namespace
* User Namespace
* IPC Namespace

Namespaces determine what a process can see.

---

## Linux cgroups

cgroups (Control Groups) provide resource control.

Examples:

```bash
docker run -m 512m nginx
docker run --cpus=1 nginx
```

cgroups determine how much CPU and memory a process can consume.

---

## Namespace vs cgroup

Namespace = Isolation

cgroup = Resource Limits

---

## Union Filesystem

Docker images are built using multiple layers.

Benefits:

* Layer reuse
* Faster downloads
* Reduced storage consumption

---

## Quick Summary

Container = Isolated Process

Namespace = Isolation

cgroup = Resource Control

Image = Blueprint

Container = Running Instance of an Image
