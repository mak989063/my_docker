# Lab 02B - Docker Containers Fundamentals

## Why Are We Learning Containers?

Docker Images are only templates.

To actually run an application, Docker creates a Container.

Think of it like:

```text
Class Object Relationship

Image     = Blueprint
Container = Running Instance
```

Example:

```text
Nginx Image
### ↓
Nginx Container
```

Without containers, applications cannot execute.

---

# Learning Objectives

By the end of this lab, you should understand:

* What is a Container
* How Containers Work
* Container Lifecycle
* Container Isolation
* Common Container Commands
* Difference Between VM and Container
* Interview Questions

---

# What is a Docker Container?

A Container is a running instance of a Docker Image.

When we execute:

```bash
docker run nginx
```

Docker performs:

```text
1. Check Local Image
2. Pull Image if Missing
3. Create Container
4. Start Container Process
```

Result:

```text
Image
  |
  v
Container
```

---

# What Happens Internally?

Command:

```bash
docker run nginx
```

Docker:

```text
Docker CLI
     |
Docker Daemon
     |
Container Creation
     |
Linux Namespaces
     |
cgroups
     |
Container Process
```

A container is essentially a Linux process running with isolation.

---

# Container Is NOT a Virtual Machine

Many beginners think:

```text
Container = Small VM
```

Wrong.

Container is simply:

```text
Isolated Process
```

Containers share the host kernel.

---

# VM vs Container

## Virtual Machine

```text
Application
Guest OS
Hypervisor
Host OS
Hardware
```

Each VM has:

* Full OS
* Own Kernel
* More RAM Usage
* Slower Startup

---

## Container

```text
Application
Libraries
Container Runtime
Host OS Kernel
Hardware
```

Containers:

* Share Host Kernel
* Lightweight
* Fast Startup
* Less Resource Usage

---

# Why Containers Start Fast

VM:

```text
Boot Operating System
Start Services
Launch Application
```

Container:

```text
Start Process
```

Startup time:

```text
VM        -> Minutes
Container -> Seconds
```

---

# Container Lifecycle

```text
Created
   |
Running
   |
Paused
   |
Stopped
   |
Deleted
```

Every container follows this lifecycle.

---

# Run a Container

```bash
docker run nginx
```

Foreground mode.

Terminal gets attached.

---

# Run Container in Background

```bash
docker run -d nginx
```

Example Output:

```text
c5f2bbd39bb32a9e5afb38b705c1964801f0b52096c4cce21105d524533e5d3e
```

Docker returns Container ID.

---

# List Running Containers

```bash
docker ps
```

Example:

```text
CONTAINER ID   IMAGE   STATUS
c5f2bbd39bb    nginx   Up 5 mins
```

---

# List All Containers

```bash
docker ps -a
```

Shows:

* Running Containers
* Stopped Containers

---

# View Logs

```bash
docker logs <container-id>
```

Example:

```bash
docker logs c5f2bbd39bb
```

Useful for troubleshooting.

---

# Execute Commands Inside Container

```bash
docker exec -it <container-id> bash
```

Example:

```bash
docker exec -it c5f2bbd39bb bash
```

Enter container shell.

Verify:

```bash
hostname
```

Notice hostname equals container ID.

---

# Stop a Container

```bash
docker stop <container-id>
```

Example:

```bash
docker stop c5f2bbd39bb
```

Container state:

```text
Running -> Stopped
```

---

# Start a Stopped Container

```bash
docker start <container-id>
```

Example:

```bash
docker start c5f2bbd39bb
```

State:

```text
Stopped -> Running
```

---

# Restart a Container

```bash
docker restart <container-id>
```

Performs:

```text
Stop
  +
Start
```

---

# Delete a Container

```bash
docker rm <container-id>
```

Container must be stopped first.

---

# Force Delete

```bash
docker rm -f <container-id>
```

Stops and removes immediately.

---

# Container Names

Docker auto-generates names.

Example:

```text
sleepy_hopper
happy_turing
```

Custom name:

```bash
docker run -d --name webserver nginx
```

Check:

```bash
docker ps
```

---

# Inspect Container Details

```bash
docker inspect <container-id>
```

Shows:

* IP Address
* Mounts
* Environment Variables
* Network Settings

---

# Resource Isolation

Docker uses:

## Namespaces

Provide isolation.

Examples:

* Process Namespace
* Network Namespace
* Mount Namespace
* User Namespace

Container sees only its resources.

---

## cgroups

Control:

* CPU
* RAM
* Disk I/O

Example:

```bash
docker run -m 512m nginx
```

Container can use only 512 MB RAM.

---

# Container Lifecycle Theory (Scaler Notes)

```text
docker run
     |
Created
     |
Running
     |
docker stop
     |
Exited
     |
docker start
     |
Running
     |
docker rm
     |
Deleted
```

Interviewers ask this frequently.

---

# Common Interview Questions

## What is a Docker Container?

A running instance of a Docker Image.

---

## Is a Container a VM?

No.

Container is an isolated process sharing the host kernel.

---

## Why are Containers Lightweight?

Because they do not contain a full operating system.

They share the host kernel.

---

## Which command starts a container?

```bash
docker start <container-id>
```

---

## Which command lists running containers?

```bash
docker ps
```

---

## Which command enters a container?

```bash
docker exec -it <container-id> bash
```

---

## What is the difference between docker run and docker start?

docker run:

* Creates Container
* Starts Container

docker start:

* Starts Existing Container

---

## What command shows logs?

```bash
docker logs <container-id>
```

---

# Quick Revision

```bash
docker run -d nginx

docker ps

docker ps -a

docker logs <container-id>

docker exec -it <container-id> bash

docker stop <container-id>

docker start <container-id>

docker restart <container-id>

docker rm <container-id>

docker inspect <container-id>
```

---

# Scaler Notes Mapping

| Topic               | Covered |
| ------------------- | ------- |
| What is Container   | Yes     |
| Container Lifecycle | Yes     |
| docker run          | Yes     |
| docker ps           | Yes     |
| docker logs         | Yes     |
| docker exec         | Yes     |
| docker stop         | Yes     |
| docker rm           | Yes     |
| Namespaces          | Yes     |
| cgroups             | Yes     |
| VM vs Container     | Yes     |
| Interview Questions | Yes     |

---

# Next Lab

```text
Lab 03 - Docker Architecture
```

Topics:

* Docker Engine
* Docker CLI
* Docker Daemon
* Docker Registry
* Docker Client Server Architecture
* Container Runtime
* Linux Kernel Features
* Interview Notes
