# 🧠 IBM Cloud Code Engine: Project, Application, Build, and Jobs

In this guide, you will learn:

- ✅ What a **Project** is in Code Engine
- ✅ What an **Application** is and how it runs
- ✅ What a **Build** does to create container images
- ✅ What a **Job** is and when to use it

---

## 📦 1. Project

A **Project** in IBM Cloud Code Engine is:

- A **logical group** that contains:

  - Applications
  - Builds
  - Jobs
  - TLS Certificates, etc.

- Provides a **namespace**:

  - All names must be unique within the project

- Controls:

  - ✅ **Access control**
  - ✅ **Resource limits (CPU/RAM)**
  - ✅ **Audit trail for activities**

### 🧩 Example: Project Structure

```
Project: my-project
│
├── Applications (11)
│   ├── my-api
│   ├── payment-gateway
│   └── ...
│
├── Jobs (2)
│   ├── data-cleanup
│   └── billing-report
│
├── Builds
│   ├── frontend-build
│   └── backend-build
│
└── TLS Certificates
```

---

## 🚀 2. Application

An **Application** in Code Engine:

- Is a **deployed service** that:

  - Serves **HTTP(S)** requests
  - Handles **WebSocket** sessions

- Automatically **scales up/down** based on load
- Source can come from:

  - A **container image**
  - **Source code** + Dockerfile or Buildpack

### ⚙️ Example Application Lifecycle

```
    Source Code (e.g., GitHub)
           │
           ▼
   ┌──────────────────────┐
   │  Dockerfile/Buildpack│
   └──────────────────────┘
           │
           ▼
   ┌─────────────────────┐
   │    Build Process    │
   └─────────────────────┘
           │
           ▼
   ┌─────────────────────┐
   │ Container Image Repo│
   └─────────────────────┘
           │
           ▼
   ┌────────────────────────────┐
   │ Code Engine Application    │
   │  ┌───────────────────────┐ │
   │  │ Handles HTTP/WebSocket│ │
   │  │ Auto-scales instances │ │
   │  └───────────────────────┘ │
   └────────────────────────────┘
           │
           ▼
     Public HTTPS Endpoint
```

### 🧠 Use Cases

- A web app that serves REST API calls
- A chat service using WebSockets
- A backend that scales to zero when idle

---

## 🛠️ 3. Build

A **Build** creates a **container image** from your source code using either:

- 🐳 A **Dockerfile**, or
- 🔧 A **Cloud Native Buildpack**

### 🏗️ Example Build Process

```
Source Code
   │
   ├──> Dockerfile --------┐
   │                       ▼
   └──> Buildpack -------> Build Process
                               │
                               ▼
                        Container Image
                               │
                               ▼
                     Used in Application
```

### 📌 Build Includes

- Executable code
- Dependencies
- Runtime configs
- Libraries and tools

---

## 🧾 4. Job

A **Job** is:

- A **one-time** execution of code
- Can scale to multiple instances **only during the job run**
- Terminates once completed

### 🔁 Example Job Use Cases

- 🧹 Data cleanup
- 📊 Report generation
- 📦 Batch data processing
- 🤖 ML model training

### 🔄 Job Execution Flow

```
Job Definition
   │
   └──▶ Workload Config (CPU, memory, env)
            │
            ▼
    ┌───────────────────────────────┐
    │   Job Executed by Code Engine │
    └───────────────────────────────┘
            │
            ▼
    ┌───────────────────────────────┐
    │  One or more Instances Spawned│
    └───────────────────────────────┘
            │
            ▼
     Executes Task → Terminates
```

---

## ✅ Recap

| Concept         | Description                                                          |
| --------------- | -------------------------------------------------------------------- |
| **Project**     | A namespace grouping applications, jobs, and builds                  |
| **Application** | A deployed service that handles HTTP/WebSocket, scales automatically |
| **Build**       | Creates a container image from code using Dockerfile or Buildpack    |
| **Job**         | A one-time task execution (e.g., batch job, report, ML training)     |

---
