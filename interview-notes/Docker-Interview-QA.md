# Docker Interview Questions & Answers

## Beginner to Intermediate Level

---

# 1. What is Docker?

Docker is an open-source containerization platform that allows applications and their dependencies to be packaged together into lightweight containers.

Benefits:

* Consistent environments
* Faster deployments
* Better resource utilization
* Portability across environments

---

# 2. Why was Docker created?

Before Docker:

* Applications worked on developer machines but failed in production.
* Dependency versions differed across environments.
* Infrastructure setup was inconsistent.

Docker solved this by packaging:

```text
Application
+ Dependencies
+ Libraries
+ Runtime
```

into a single deployable unit called an Image.

---

# 3. What is a Container?

A container is a running instance of a Docker Image.

Example:

```bash
docker run nginx
```

creates a container from the nginx image.

---

# 4. What is a Docker Image?

A Docker Image is a read-only template used to create containers.

It contains:

* Application Code
* Dependencies
* Runtime
* Configuration

Think:

```text
Image = Blueprint
Container = Running Instance
```

---

# 5. Difference Between Image and Container

| Image          | Container        |
| -------------- | ---------------- |
| Blueprint      | Running Instance |
| Read-only      | Read/Write       |
| Static         | Dynamic          |
| Stored on Disk | Running Process  |

---

# 6. What happens when you run:

```bash
docker run nginx
```

Docker performs:

1. Check local image
2. Pull image if absent
3. Create container
4. Create namespaces
5. Apply cgroups
6. Start nginx process

---

# 7. Is a Container a Virtual Machine?

No.

Containers share the host OS kernel.

VMs have their own operating system and kernel.

---

# 8. Difference Between VM and Container

| Virtual Machine     | Container           |
| ------------------- | ------------------- |
| Full OS             | Shares Host Kernel  |
| Heavyweight         | Lightweight         |
| Slower Startup      | Faster Startup      |
| More Resource Usage | Less Resource Usage |

---

# 9. What Linux Features Make Containers Possible?

Docker relies on Linux Kernel features:

### Namespaces

Provide isolation.

Examples:

* PID Namespace
* Network Namespace
* Mount Namespace
* User Namespace

### cgroups

Provide resource control.

Examples:

* CPU Limits
* Memory Limits
* Disk Limits

### Union Filesystem

Provides layered storage.

---

# 10. What are Namespaces?

Namespaces isolate resources.

Each container gets its own view of:

* Processes
* Network
* Filesystem
* Users

Containers cannot directly see processes running in other containers.

---

# 11. What are cgroups?

Control Groups (cgroups) limit and monitor resource usage.

Examples:

```bash
docker run -m 512m nginx
```

Limits container memory to 512 MB.

---

# 12. What is Union Filesystem?

A layered filesystem used by Docker.

Benefits:

* Layer reuse
* Faster builds
* Reduced storage

---

# 13. What is Docker Hub?

Docker Hub is a public image registry.

Used to:

* Store images
* Share images
* Pull images

Example:

```bash
docker pull nginx
```

---

# 14. What is Docker Architecture?

Main Components:

```text
Docker CLI
      |
Docker Daemon
      |
Container Runtime
      |
Linux Kernel
```

---

# 15. What is Docker CLI?

CLI stands for Command Line Interface.

Examples:

```bash
docker run
docker ps
docker images
```

CLI sends requests to Docker Daemon.

---

# 16. What is Docker Daemon?

Docker Daemon (dockerd):

Responsible for:

* Creating containers
* Managing images
* Managing networks
* Managing volumes

Runs as a background service.

---

# 17. What is Docker Engine?

Docker Engine consists of:

```text
Docker CLI
+
Docker Daemon
+
Docker APIs
```

---

# 18. What is the Container Lifecycle?

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

---

# 19. Difference Between docker run and docker start

docker run:

* Creates container
* Starts container

docker start:

* Starts existing container

---

# 20. Difference Between docker stop and docker kill

docker stop

* Graceful shutdown
* Sends SIGTERM

docker kill

* Immediate termination
* Sends SIGKILL

---

# 21. How Do You View Running Containers?

```bash
docker ps
```

---

# 22. How Do You View All Containers?

```bash
docker ps -a
```

---

# 23. How Do You View Logs?

```bash
docker logs <container-id>
```

---

# 24. How Do You Enter a Running Container?

```bash
docker exec -it <container-id> bash
```

---

# 25. How Do You Remove a Container?

```bash
docker rm <container-id>
```

---

# 26. How Do You Remove an Image?

```bash
docker rmi nginx
```

---

# 27. What is the Difference Between CMD and ENTRYPOINT?

CMD

* Default command
* Can be overridden

ENTRYPOINT

* Fixed executable
* Harder to override

---

# 28. What is a Dockerfile?

A text file containing instructions to build a Docker image.

Example:

```dockerfile
FROM nginx
COPY . /usr/share/nginx/html
```

---

# 29. What is the Purpose of FROM?

FROM specifies the base image.

Example:

```dockerfile
FROM ubuntu:24.04
```

Every Dockerfile starts with FROM.

---

# 30. Why is FROM Mandatory?

Docker images are built in layers.

FROM defines the first/base layer.

Without it Docker doesn't know what image to build on.

---

# 31. Docker on Windows Uses Linux Features. How?

Interview Favorite.

Containers require:

* Namespaces
* cgroups
* Union Filesystems

These exist in Linux.

Windows runs Docker using:

```text
Windows
   |
WSL2 / Lightweight Linux VM
   |
Docker Engine
   |
Containers
```

Therefore Linux kernel features are still used.

---

# 32. Why Are Containers Lightweight?

Because they share the host kernel.

No full operating system is installed inside each container.

---

# 33. Can Multiple Containers Use the Same Image?

Yes.

Example:

```text
Ubuntu Image
      |
      +--> Container 1
      +--> Container 2
      +--> Container 3
```

---

# 34. What Happens if an Image is Not Available Locally?

Docker:

1. Checks local image cache
2. Pulls image from registry
3. Stores locally
4. Creates container

---

# 35. Explain Docker in One Minute

Docker is a containerization platform that packages applications and dependencies into portable images. Containers created from those images run as isolated processes using Linux kernel features like namespaces and cgroups. Docker provides consistency across development, testing, and production environments while consuming fewer resources than traditional virtual machines.

---
