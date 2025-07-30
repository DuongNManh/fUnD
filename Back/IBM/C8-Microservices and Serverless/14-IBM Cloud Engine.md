# 🌩️ IBM Cloud Code Engine

## 🎯 Learning Objectives

By the end of this lesson, you will be able to:

* Describe the **challenges of self-hosting microservices**
* Explain the **purpose and features of IBM Cloud Code Engine**
* Identify **how IBM Cloud Code Engine simplifies deployment**

---

## 🧱 The Challenges of Self-Hosting Microservices

After developing and testing microservices locally, self-hosting them in production presents several non-trivial challenges:

### Key Challenges

| Challenge                      | Description                                                            |
| ------------------------------ | ---------------------------------------------------------------------- |
| 🛠️ Configuration              | Must configure assets, credentials, dependencies, etc.                 |
| 🏗️ Infrastructure Choice      | Choose from servers, OS, databases, and more                           |
| 📈 Traffic Scalability         | Must handle dynamic load (e.g., holiday peaks on e-commerce platforms) |
| 🔄 Multi-Service Communication | Microservices must interact reliably and securely                      |
| 📊 Observability               | Requires logging, monitoring, alerting, and dashboards                 |

---

## 🧪 Example: Deploying a Python Microservice

Let’s say you’ve built a microservice using **Flask**. To self-host it:

* Choose a **web server interface**:

  * **WSGI** (sync) → Green Unicorn, uWSGI
  * **ASGI** (async) → Daphne, Hypercorn
* Provision infrastructure manually
* Configure networking and dependencies
* Add logging and scaling logic

🧨 Clearly, this involves significant operational overhead.

---

## 🚀 Introducing IBM Cloud Code Engine

IBM Cloud Code Engine is a **fully managed, serverless platform** designed to offload the burden of managing infrastructure.

### 🔧 What It Does

* Abstracts server, cluster, and scaling management
* Offers a simple CLI and web UI to deploy applications
* Supports:

  * Microservices
  * Event-driven functions
  * Web apps
  * Batch jobs

---

## 🛠️ Deployment Options with Code Engine

1. **Deploy Prebuilt App**
   Push your container image or app bundle to Code Engine.

2. **Deploy From Source Code**

   * Push from GitHub/local
   * Let Code Engine build and deploy it automatically

3. **Run Batch Jobs**
   Schedule or trigger asynchronous data processing jobs

---

## 🖼️ Architecture Diagram

Here’s a simple overview of how IBM Cloud Code Engine fits into the workflow:

```plaintext
                        ┌────────────────────────┐
                        │    Developer Code      │
                        └─────────┬──────────────┘
                                  │  (push)
                    ┌─────────────▼────────────────┐
                    │     IBM Cloud Code Engine    │
                    │ ──────────────────────────── │
                    │   - Build & Deploy Apps      │
                    │   - Run Batch Jobs           │
                    │   - Auto Scaling             │
                    └───────┬───────────────────┬──┘
                            │                   │
              ┌─────────────▼────────┐    ┌─────▼───────────────┐
              │ HTTPS Microservice   │    │   Batch Job (ETL)   │
              └──────────────────────┘    └─────────────────────┘
```

---

## ✅ Benefits Summary

| Benefit                  | Description                                                  |
| ------------------------ | ------------------------------------------------------------ |
| ⚙️ No Cluster Management | IBM handles provisioning, config, and scaling                |
| 🕒 Fast Deployment       | Build & deploy in seconds for quick iteration                |
| 📈 Auto-Scaling          | Scale up/down with traffic                                   |
| 🔐 Secure by Default     | TLS, IAM, and workload isolation                             |
| 🔗 IBM Cloud Integration | Works with other services like Cloud Databases, Object Store |

---

## 🧠 Key Takeaways

* Self-hosting microservices is **complex and effort-intensive**
* IBM Cloud Code Engine **abstracts infrastructure** and lets you focus on writing code
* Supports **three modes**: app deploy, source code build & deploy, and batch jobs

---
