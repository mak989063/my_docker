# Lab 02A - Docker Images Fundamentals

## Why Are We Learning Docker Images?

Before running a container, Docker needs an image.

Think of it like:

```text
Image     = Blueprint
Container = Running Instance
```

Example:

```text
Ubuntu Image
      |
      v
Ubuntu Container
```

Without an image, a container cannot be created.

---

# Learning Objectives

By the end of this lab, you should understand:

* What is a Docker Image
* Why Images are needed
* How Images are downloaded
* Image Layers
* Docker Hub
* Difference between Images and Containers
* Common Image Commands
* Interview Questions

---

# What is a Docker Image?

A Docker Image is a read-only template used to create containers.

It contains:

* Application Code
* Libraries
* Dependencies
* Runtime
* Configuration Files

Example:

```text
Nginx Image

├── Ubuntu OS Layer
├── Required Packages
├── Nginx Software
└── Startup Command
```

When we run:

```bash
docker run nginx
```

Docker creates a container from the image.

---

# Why Docker Images Were Created

Before Docker:

```text
Developer Machine
        |
        v
Works Fine
        |
        v
Production Server
        |
        v
Fails
```

Problems:

* Dependency mismatch
* Library mismatch
* Different operating systems
* Different runtime versions

Docker Images solve this by packaging everything together.

```text
Code + Dependencies + Runtime = Docker Image
```

Result:

```text
Works on My Machine
       =
Works Everywhere
```

---

# Where Are Images Stored?

Images are usually stored in registries.

Popular Registries:

* Docker Hub
* AWS ECR
* Azure ACR
* Google Artifact Registry

Docker Hub is the default public registry.

Example:

```bash
docker pull nginx
```

Docker downloads the image from Docker Hub.

---

# Search for an Image

```bash
docker search nginx
```

Purpose:

Search Docker Hub repositories.

---

# Pull an Image

```bash
docker pull nginx
```

Output:

```text
Pulling from library/nginx
Downloaded newer image for nginx
```

Observation:

Docker downloads image layers.

---

# List Downloaded Images

```bash
docker images
```

Example Output:

```text
REPOSITORY   TAG      IMAGE ID
nginx        latest   xxxxxxxx
ubuntu       latest   xxxxxxxx
```

Purpose:

Shows locally available images.

---

# Understanding Image Layers

Docker Images are built layer by layer.

Example:

```text
Application Layer
      |
Nginx Layer
      |
Ubuntu Layer
```

Benefits:

* Faster downloads
* Less storage
* Layer reuse
* Efficient caching

---

# View Image History

```bash
docker history nginx
```

Purpose:

Shows how image layers were built.

Sample Output:

```text
IMAGE      CREATED BY
xxxx       CMD nginx
xxxx       COPY files
xxxx       RUN apt install
```

---

# Inspect Image Metadata

```bash
docker inspect nginx
```

Useful Information:

* Architecture
* Operating System
* Layer Information
* Environment Variables

---

# Difference Between Image and Container

| Image          | Container        |
| -------------- | ---------------- |
| Blueprint      | Running Instance |
| Read Only      | Read/Write       |
| Static         | Dynamic          |
| Stored on Disk | Running Process  |

Example:

```text
Ubuntu Image
      |
      +----> Container 1
      |
      +----> Container 2
      |
      +----> Container 3
```

One image can create multiple containers.

---

# Remove an Image

```bash
docker rmi nginx
```

Purpose:

Deletes image from local machine.

Note:

Container using the image must be removed first.

---

# Common Interview Questions

## What is a Docker Image?

A Docker Image is a read-only template used to create containers.

---

## What is Docker Hub?

Docker Hub is a public image registry where Docker images are stored and shared.

---

## What is the difference between Image and Container?

Image is a blueprint.

Container is a running instance of an image.

---

## Why are Docker Images layered?

To improve:

* Reusability
* Storage efficiency
* Faster downloads
* Build caching

---

## Can multiple containers use the same image?

Yes.

A single image can create multiple containers.

---

## Which command downloads an image?

```bash
docker pull nginx
```

---

## Which command lists images?

```bash
docker images
```

---

## Which command shows image layers?

```bash
docker history nginx
```

---

# Quick Revision

```bash
docker search nginx

docker pull nginx

docker images

docker history nginx

docker inspect nginx

docker rmi nginx
```

Remember:

```text
Image = Blueprint

Container = Running Instance

Docker Hub = Image Registry

Layers = Efficient Storage
```

---

# Scaler Notes Mapping

| Topic                  | Covered |
| ---------------------- | ------- |
| What is Docker         | Yes     |
| Why Docker Was Created | Yes     |
| Docker Images          | Yes     |
| Docker Hub             | Yes     |
| Image Layers           | Yes     |
| Docker Pull Process    | Yes     |
| Image Inspection       | Yes     |
| Interview Questions    | Yes     |

Next Lab:

```text
Lab 03 - Docker Containers
```

Topics:

* docker run
* docker ps
* docker logs
* docker exec
* docker stop
* docker rm
* Container Lifecycle
