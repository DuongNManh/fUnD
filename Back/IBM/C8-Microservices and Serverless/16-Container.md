# 🐳 Building Container Images for Microservices

## 🎯 Learning Objectives

After studying this section, you will be able to:

- ✅ Explain what a **container** is.
- ✅ Describe what **Docker** is and how it works.
- ✅ Understand how to **build a Docker container image**.
- ✅ Use **Dockerfile** instructions effectively.
- ✅ Push and pull images from a **container registry**.

---

## 📦 What Is a Container?

A **container** is:

- A **standalone**, **executable**, and **lightweight** unit of software.
- Contains the **application source code**, **libraries**, **runtime**, and **dependencies**.
- Can run on:

  - 🖥️ Laptops
  - 🖥️ Servers
  - ☁️ Cloud platforms

Containers differ from virtual machines because they **leverage the host OS**, avoiding the need for a guest OS per instance.

> ✅ **Perfect for microservices**: Containers align well with microservices due to their **small size**, **portability**, and **resource isolation**.

---

## 🐳 What Is Docker?

**Docker** is a popular platform to:

- Build
- Run
- Share containers

Docker has led to a growing ecosystem of container tools and has become the **standard** container technology — including in **IBM Cloud Code Engine**.

---

## 🔨 Building a Docker Container Image

Here's a typical workflow:

```plaintext
App source code + Dependencies
         ↓
    Dockerfile blueprint
         ↓
  docker build → Container Image
         ↓
 docker run → Running Container
```

### 🧱 What's a Dockerfile?

A **Dockerfile** is a text file with **instructions** for how to build a container image.

Example Dockerfile for a **Flask-based Python microservice**:

```Dockerfile
# Use Python base image
FROM python:3.11

# Set the working directory
WORKDIR /app

# Copy local code into the container image
COPY . /app

# Set environment variable
ENV LISTEN_PORT=8080

# Expose port
EXPOSE 8080

# Install dependencies
RUN pip install -r requirements.txt

# Run the Flask app
CMD ["python", "app.py"]
```

> ⚠️ You can only have **one `CMD` instruction** in a Dockerfile.

---

## 📸 Image vs Container

```plaintext
           +----------------------+
           |   Container Image    |
           |  (like a class)      |
           +----------------------+
                     ↓
        docker run → Creates instance
                     ↓
           +----------------------+
           |   Running Container  |
           |  (like an object)    |
           +----------------------+
```

- `Image`: Read-only template
- `Container`: Running instance based on the image

---

## 🗃️ Pushing to a Container Registry

Once the image is built:

1. Push it to a **container registry** (e.g., Docker Hub, IBM Cloud Container Registry)
2. Other systems or pipelines can **pull it** using the image name.

### 🏷️ Image Naming Convention

```plaintext
HOSTNAME/REPOSITORY:TAG
```

Example:

```plaintext
icr.io/myorg/myservice:v1.0.0
```

- `icr.io`: IBM Cloud Container Registry hostname
- `myorg/myservice`: Repository name
- `v1.0.0`: Tag/version

---

## 📌 Summary

| Concept            | Description                                                 |
| ------------------ | ----------------------------------------------------------- |
| Container          | Executable unit of software with all dependencies           |
| Docker             | Platform to build, run, and manage containers               |
| Dockerfile         | Instructions to build a container image                     |
| Container Image    | Immutable blueprint for containers                          |
| Container Registry | Remote storage for built images (e.g., Docker Hub, IBM ICR) |

---

## 📊 Visual Summary

```plaintext
            ┌───────────────────────────────┐
            │      Source Code (Flask)      │
            └───────────────────────────────┘
                         │
                         ▼
                ┌────────────────────┐
                │    Dockerfile      │
                └────────────────────┘
                         │
                         ▼
         ┌───────────────────────────────┐
         │      docker build .           │
         └───────────────────────────────┘
                         │
                         ▼
            ┌───────────────────────────────┐
            │  Container Image (Read-Only)  │
            └───────────────────────────────┘
                         │
                         ▼
         ┌───────────────────────────────┐
         │ docker push icr.io/app:v1     │
         └───────────────────────────────┘
                         │
                         ▼
         ┌───────────────────────────────┐
         │ Container Registry (ICR)      │
         └───────────────────────────────┘
                         │
                         ▼
         ┌───────────────────────────────┐
         │ docker run icr.io/app:v1      │
         └───────────────────────────────┘
                         │
                         ▼
             ┌─────────────────────┐
             │   Running Container │
             └─────────────────────┘
```

---
