# 🏗️ Production Deployment Components

## 🎯 Learning Objectives

After this guide, you will be able to:

- Describe **key components** used in production environments
- Understand the purpose of **firewalls**, **load balancers**, **servers**, and **proxies**
- Differentiate between **web servers**, **application servers**, and **database servers**

---

## 🧱 Production Architecture Overview

Production deployment commonly follows an **n-tier architecture**, with separate layers for presentation, web, application, and data.

### 📊 N-Tier Infrastructure Diagram

```
         ┌────────────────────────┐
         │    Presentation Tier   │
         │  (Client Applications) │
         └──────────┬─────────────┘
                    │
           🔥 Firewall (Security Layer)
                    │
         ┌──────────┴────────────┐
         │      Web Tier         │
         │ Web Load Balancer     │
         │⇅ Multiple Web Servers │
         └──────────┬────────────┘
                    │
         ┌──────────┴────────────┐
         │   Application Tier    │
         │ App Load Balancer /   │
         │    Proxy Server       │
         │⇅ Multiple App Servers │
         └──────────┬────────────┘
                    │
         ┌──────────┴────────────┐
         │      Data Tier        │
         │  Primary DB Server    │
         │  + High-Availability  │
         │    Replica (optional) │
         └───────────────────────┘
```

🧠 Not all deployments need every tier or component. Some environments may:

- Skip application servers
- Merge tiers based on simplicity or budget

---

## 🔐 Firewall

A **firewall** is a security device that:

- **Monitors traffic** between networks
- **Blocks or allows data** based on rules
- Protects internal systems from **viruses, malware, and intrusions**

📊 **Diagram**:

```
[Internet] ⇄ [🔥 Firewall] ⇄ [Internal Network]
```

---

## ⚖️ Load Balancer

A **load balancer**:

- Distributes incoming traffic across **multiple servers**
- Prevents **overloading** a single server
- Enhances **availability** and **response time**

📊 **Diagram**:

```
         [Client Requests]
                 ↓
         ┌───────────────┐
         │ Load Balancer │
         └──────┬────────┘
        ⇩       ⇩       ⇩
 [Server A] [Server B] [Server C]
```

---

## 🌐 Web Server

A **web server**:

- Handles **HTTP(S)** requests
- Serves **static content** (HTML, CSS, JS, images)
- Responds to **browser-based clients**

🧠 Example: Apache, Nginx, IIS

---

## ⚙️ Application Server

An **application server**:

- Runs **backend business logic**
- Manages user requests that involve **data manipulation or computation**
- Connects to database, processes input/output

🧠 Example: Node.js, Tomcat, WebLogic

---

## 🧩 Proxy Server

A **proxy server** acts as an **intermediary** between two systems:

📌 Responsibilities:

- Load balancing
- Caching
- Security filtering (e.g., malware scanning, encryption)
- Obfuscating origin IP
- Request optimization

📊 **Diagram**:

```
[Client] ⇄ [Proxy] ⇄ [App Servers / Web Servers]
```

---

## 🗃️ Database Server

A **database server**:

- Stores and manages structured data
- Controlled by a **DBMS** (Database Management System)
- Handles data **read/write** operations from apps

🧠 Examples:

- **DBMS**: MySQL, PostgreSQL, MongoDB, SQL Server
- **Operations**: Create, read, update, delete (CRUD)

📊 **Diagram**:

```
[App Server] ⇄ [DBMS] ⇄ [Database Storage]
```

High-availability environments may use **replication**:

```
[Primary DB] ⇄ [Replica DB]
```

---

## ✅ Summary Table

| Component          | Role                                                         |
| ------------------ | ------------------------------------------------------------ |
| 🔥 Firewall        | Secures traffic between networks, blocks unauthorized access |
| ⚖️ Load Balancer   | Distributes traffic among servers for performance & uptime   |
| 🌐 Web Server      | Serves static content and handles HTTP requests              |
| ⚙️ App Server      | Executes business logic and dynamic processing               |
| 🧩 Proxy Server    | Optimizes traffic, provides security, enables load balancing |
| 🗃️ Database Server | Stores and controls access to application data               |

---

## 🧠 Final Notes

- Real-world systems often mix components based on **performance**, **security**, and **cost**
- Tiers may be **merged or separated** depending on application complexity
- Design should ensure **availability**, **scalability**, and **security**

---
