# 🐳 Docker Architecture - Learning Guide

After studying this topic, you will be able to:

- ✅ Identify the core components of Docker architecture
- ✅ Explain the function of each component
- ✅ Describe the containerization process with Docker

---

## 🧱 Docker Architecture Overview

Docker uses a **client-server architecture** that enables developers to build, ship, and run containerized applications.

### 🔧 Key Components

| Component           | Description                                                                                   |
| ------------------- | --------------------------------------------------------------------------------------------- |
| **Docker Client**   | Interface used to communicate with the Docker host (CLI or REST API).                         |
| **Docker Host**     | Machine running the Docker daemon (`dockerd`) that executes container tasks.                  |
| **Docker Daemon**   | The background service that builds, runs, and manages containers.                             |
| **Docker Registry** | Stores Docker images. Can be public (e.g., Docker Hub) or private (e.g., IBM Cloud Registry). |

---

## 🛰️ High-Level Docker Architecture Diagram

```plaintext
+-------------------+     docker CLI/API   +----------------------+      pull/push      +---------------------+
|   Docker Client   |  ----------------->  |   Docker Host        |  ---------------->  | Docker Registry     |
|  (CLI or REST API)|                      | (Docker Daemon, etc.)|  <----------------  | (e.g., Docker Hub)  |
+-------------------+                      +----------------------+                     +---------------------+
                                                  |
                                                  v
                                [ Manages Containers, Images, Networks ]
```

---

## 🔁 How Docker Works (Step-by-Step)

### 🔹 1. Interaction via Docker Client

- The **Docker Client** sends commands (e.g., `docker run`, `docker build`) to the Docker Host.
- This can be done **locally** or over a **remote connection**.

### 🔹 2. Docker Host Responsibilities

- The **Docker Daemon (`dockerd`)** receives and processes these commands.
- Manages:

  - Images
  - Containers
  - Namespaces
  - Networks
  - Volumes (Storage)
  - Plugins and Add-ons

### 🔹 3. Docker Registry

- A **Docker Registry** stores images that can be:

  - **Public** (e.g., Docker Hub)
  - **Private** (self-hosted or via cloud services like IBM Cloud Container Registry)

---

## 🧰 Containerization Process with Docker

```plaintext
[ Dockerfile / Base Image ]
            |
     docker build -t my-image:v1 .
            |
            v
    [ Docker Image Created ]
            |
    docker push my-image:v1
            |
            v
      [ Docker Registry ]
            |
    docker run my-image:v1
            |
            v
  [ Pulls image if needed ]
            |
            v
    [ Running Container ]
```

### 🔄 Process Breakdown

| Step        | Description                                                    |
| ----------- | -------------------------------------------------------------- |
| **Build**   | Use a Dockerfile to create a container image (`docker build`). |
| **Push**    | Upload the image to a registry (`docker push`).                |
| **Run**     | Start a container from the image (`docker run`).               |
| **Pull**    | Retrieve an image if not found locally (`docker pull`).        |
| **Execute** | Docker daemon creates and runs the container from the image.   |

---

## 📌 Summary

| Concept                   | Details                                                               |
| ------------------------- | --------------------------------------------------------------------- |
| Docker Architecture       | Consists of **Client**, **Host**, and **Registry**.                   |
| Docker Daemon (`dockerd`) | Core service that builds and runs containers.                         |
| Registry Types            | Public (Docker Hub) or Private (e.g., IBM Cloud, self-hosted).        |
| Containerization Process  | Involves **build → push → run**, and uses base images or Dockerfiles. |

---

### ✅ Docker Core Commands Recap

| Command        | Purpose                       |
| -------------- | ----------------------------- |
| `docker build` | Create image from Dockerfile  |
| `docker push`  | Push image to registry        |
| `docker pull`  | Pull image from registry      |
| `docker run`   | Run a container from an image |

---
