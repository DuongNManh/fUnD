# 📚 Review of Docker Concepts and Understanding a Dockerfile

## **⏱️ Estimated Time: 30 Minutes** Review of Docker Concepts and Understanding a Dockerfile

## 🧠 Learning Objectives

After completing this reading, you will be able to:

- ✅ Define Docker containers, images, and registries
- ✅ Understand how and where Docker images are stored
- ✅ Break down a Dockerfile and explain each command
- ✅ Build a secure and production-ready container for a Node.js app
- ✅ Build a container image using a Dockerfile
- ✅ Create a running container from an image
- ✅ Understand and use key Docker commands

---

## 📌 Overview: Container Lifecycle

The process of developing and running containers consists of three main steps:

```
+----------------+       +----------------------+       +--------------------------+
|   Dockerfile   |  -->  |  Container Image     |  -->  | Running Docker Container |
+----------------+       +----------------------+       +--------------------------+
       ^                            ^                                 ^
       |                            |                                 |
Create instructions     Build using `docker build`           Run using `docker run`
```

---

## 🐳 Docker Concepts

### 🔹 What is Docker?

Docker simplifies the development and deployment of applications using **containers**—lightweight, isolated environments that bundle your app and its dependencies.

### 🔹 Key Terms

| Term             | Description                                                                  |
| ---------------- | ---------------------------------------------------------------------------- |
| **Dockerfile**   | A text file with step-by-step instructions to build a Docker image.          |
| **Container**    | A running instance of a Docker image.                                        |
| **Docker Image** | A snapshot of a container, created from a Dockerfile.                        |
| **Registry**     | A storage system for Docker images (e.g., Docker Hub or private registries). |

---

## 🗂️ Where Docker Images Exist

| Location          | Description                                                                    |
| ----------------- | ------------------------------------------------------------------------------ |
| **Local Machine** | When you build an image, it's stored locally. List with `docker images`.       |
| **Registry**      | After building, you can `push` images to a remote registry for access/sharing. |

---

## 🧱 1. Simple Dockerfile Example

A **Dockerfile** is a plain text file that contains instructions for building a Docker image.

### ✅ Basic Example: `Dockerfile`

```dockerfile
FROM alpine
CMD ["echo", "Hello World"]
```

- `FROM alpine` — Uses Alpine Linux as the **base image**
- `CMD` — Specifies the command to run (`echo "Hello World"`)

---

## 🧱 2. Comprehensive Dockerfile Example (Node.js App)

```Dockerfile
# Use the official Node.js image as the base image
FROM node:14

# Set environment variables
ENV NODE_ENV=production
ENV PORT=3000

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json files
COPY package*.json ./

# Install dependencies
RUN npm install --production

# Copy the rest of the application code
COPY . .

# Add additional file
ADD public/index.html /app/public/index.html

# Expose the port on which the application will run
EXPOSE $PORT

# Specify the default command to run when the container starts
CMD ["node", "app.js"]

# Labeling the image
LABEL version="1.0"
LABEL description="Node.js application Docker image"
LABEL maintainer="Your Name"

# Healthcheck to ensure the container is running correctly
HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 \
  CMD curl -fs http://localhost:$PORT || exit 1

# Set a non-root user for security purposes
USER node
```

---

## 🔍 Breakdown of the Dockerfile

### 1️⃣ Base Image

```Dockerfile
FROM node:14
```

- `FROM`: Specifies the **base image**.
- `node:14`: Pulls the official Node.js image, version 14.

---

### 2️⃣ Environment Variables

```Dockerfile
ENV NODE_ENV=production
ENV PORT=3000
```

- `ENV`: Defines environment variables used in the container.

---

### 3️⃣ Working Directory

```Dockerfile
WORKDIR /app
```

- `WORKDIR`: Sets the working directory for all subsequent commands.

---

### 4️⃣ Copy Package Files

```Dockerfile
COPY package*.json ./
```

- `COPY`: Transfers files from your machine to the container.
- `package*.json`: Includes both `package.json` and `package-lock.json`.

---

### 5️⃣ Install Dependencies

```Dockerfile
RUN npm install --production
```

- `RUN`: Executes commands inside the container during the image build.
- Installs only **production** dependencies.

---

### 6️⃣ Copy Application Code

```Dockerfile
COPY . .
```

- Copies the entire app directory into the container.

---

### 7️⃣ Add Additional Files

```Dockerfile
ADD public/index.html /app/public/index.html
```

- `ADD`: Similar to `COPY` but with additional features like URL handling.

---

### 8️⃣ Expose Port

```Dockerfile
EXPOSE $PORT
```

- Informs Docker the container will listen on this port.

---

### 9️⃣ Default Command

```Dockerfile
CMD ["node", "app.js"]
```

- `CMD`: The command to run when the container starts.

---

### � Label the Image

```Dockerfile
LABEL version="1.0"
LABEL description="Node.js application Docker image"
LABEL maintainer="Your Name"
```

- `LABEL`: Adds metadata to the image.

---

### 🔁 Health Check

```Dockerfile
HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 \
  CMD curl -fs http://localhost:$PORT || exit 1
```

- `HEALTHCHECK`: Validates that the app is running correctly by pinging its HTTP endpoint.

---

### 🔒 Use Non-Root User

```Dockerfile
USER node
```

- For security, containers should not run as root unless necessary.

---

## �🔨 3. Building the Image

Use the `docker build` command to create an image from the Dockerfile.

### 🧪 Example

```bash
docker build -t my-app:v1 .
```

- `-t my-app:v1` — Tags the image as `my-app` with version `v1`
- `.` — Refers to the current directory (containing the Dockerfile)

### 🧾 Sample Output

```
Sending build context to Docker Daemon  2.048kB
Step 1/2 : FROM alpine
 ---> abc12345
Step 2/2 : CMD ["echo", "Hello World"]
 ---> Using cache
Successfully built def67890
Successfully tagged my-app:v1
```

---

## 🔍 4. Verifying the Image

Use the `docker images` command to list all locally available images:

```bash
docker images
```

### 📋 Sample Output

```
REPOSITORY   TAG       IMAGE ID       CREATED          SIZE
my-app       v1        def67890       1 minute ago     5.57MB
```

---

## 🚀 5. Running a Container

Run the image as a container using the `docker run` command:

```bash
docker run my-app:v1
```

### 🖥️ Output

```
Hello World
```

To check active containers:

```bash
docker ps -a
```

---

## 🧰 6. Key Docker Commands Summary

| Command         | Description                             |
| --------------- | --------------------------------------- |
| `docker build`  | Build a Docker image from a Dockerfile  |
| `docker images` | List all Docker images                  |
| `docker run`    | Run a container from a Docker image     |
| `docker ps -a`  | List all running and stopped containers |
| `docker push`   | Push image to a remote registry         |
| `docker pull`   | Pull image from a remote registry       |

---
