# 📦 Introduction to Docker Objects

After reading this document, you will be able to:

- Identify and describe core Docker objects
- Recognize essential Dockerfile instructions
- Explain how Docker images are named
- Understand how Docker uses networks, storage, and plugins

---

## 🔧 Docker Objects Overview

Docker includes a set of objects that are essential for building, running, and managing containers:

- **Dockerfile** – A script defining how to build a Docker image
- **Image** – A read-only template used to create containers
- **Container** – A runnable instance of an image
- **Network** – Enables communication and isolation between containers
- **Volume** – Stores persistent data
- **Plugins** – Extend Docker functionality (e.g., storage, networking)

---

## 📄 Dockerfile

A **Dockerfile** is a text file containing the commands needed to assemble a Docker image.

### ✨ Key Dockerfile Instructions

| Instruction | Description                                                                         |
| ----------- | ----------------------------------------------------------------------------------- |
| `FROM`      | Specifies the base image (must be the first instruction)                            |
| `RUN`       | Executes a command in the image during build                                        |
| `CMD`       | Sets the default command to run when a container starts (only the last one is used) |

### Example

```dockerfile
FROM node:20
RUN npm install -g serve
CMD ["serve", "-s", "build"]
```

> Note: Only the **last `CMD`** will be executed if multiple are defined.

---

## 🖼️ Docker Images

A **Docker image** is a read-only template that defines how to run a container.

### 🔄 Image Layers

- Each Dockerfile instruction creates a **new layer**
- When you rebuild an image, Docker **reuses unchanged layers** for efficiency
- Shared layers **reduce disk usage and network transfer**

### ⬇️ Diagram: Image Layering

```
+--------------------+
| CMD: serve         |
+--------------------+
| RUN: npm install   |
+--------------------+
| FROM: node:20      |
+--------------------+
```

> When instantiated, a **writable container layer** is added on top.

---

## 🧾 Docker Image Naming Convention

Docker image names follow the format:

```
[hostname]/[repository]:[tag]
```

### Example

```
docker.io/ubuntu:18.04
```

| Part        | Description                                      |
| ----------- | ------------------------------------------------ |
| `docker.io` | Hostname (Docker Hub registry) – optional in CLI |
| `ubuntu`    | Repository (the image name)                      |
| `18.04`     | Tag (specific version)                           |

---

## 📦 Docker Containers

A **Docker container** is a running instance of an image.

### 📌 Container Capabilities

- Start/stop/create/delete using Docker CLI or API
- Connect to networks
- Attach storage
- Create new images based on current container state

### 🔒 Isolation

Docker containers are:

- Isolated from each other
- Isolated from the host system (unless configured otherwise)

---

## 🌐 Docker Networks

- Used to **isolate and control communication** between containers
- Containers can join multiple networks
- Default network provides **basic isolation**

---

## 💾 Docker Storage

### 🗂️ Types of Storage

| Type             | Description                                   |
| ---------------- | --------------------------------------------- |
| **Volumes**      | Managed by Docker, persistent                 |
| **Bind Mounts**  | Link to specific host file/folder, persistent |
| **Temp Storage** | Lost when the container stops                 |

> ⚠️ By default, **data does not persist** unless stored in volumes or bind mounts.

---

## 🧩 Docker Plugins

Plugins extend Docker’s functionality, for example:

- **Storage plugins** to connect to external storage (e.g., cloud volumes)
- **Network plugins** for custom networking solutions

---

## ✅ Summary

- Docker objects: Dockerfile, image, container, network, storage (volumes), plugins
- Essential Dockerfile instructions: `FROM`, `RUN`, `CMD`
- Docker image names: `[hostname]/[repository]:[tag]`
- Containers are isolated and can use networks and storage
- Volumes and bind mounts ensure data persistence
- Plugins allow integration with external services

---
