# 📦 Approaches to Application Architecture

After going through this document, you will be able to:

- Describe component-based architectures and service-oriented architecture (SOA)
- Explain the characteristics of a software component
- Differentiate between components and services
- Describe characteristics of distributed systems

---

## 🧩 What is a Component?

A **component** is an individual, encapsulated unit of functionality that works with other components in an application.

### 🔑 Characteristics of Components

| Characteristic       | Meaning                                                     |
| -------------------- | ----------------------------------------------------------- |
| Reusable             | Can be used in multiple applications                        |
| Replaceable          | Can be swapped without affecting the system                 |
| Independent          | Has minimal dependencies                                    |
| Extensible           | Can be extended without modifying others                    |
| Encapsulated         | Hides internal data and logic                               |
| Non-context specific | Works across various environments when passed external data |

### 💡 Examples of Components

- **API Library**: e.g., Open-source API for database access
- **DAO (Data Access Object)**: Interfaces with databases abstractly
- **Controller**: Coordinates component logic based on app behavior

---

## 🏗️ Component-Based Architecture

Component-based architecture decomposes an application into logical components. It is a **higher level of abstraction** than object-oriented design.

### 📌 Goals:

- Define loosely coupled components
- Compose them to build applications
- Ensure components are **modular, reusable, and testable**

---

## 🧱 Components vs. Services

| Feature                | Component                   | Service                                     |
| ---------------------- | --------------------------- | ------------------------------------------- |
| Unit of functionality  | ✅                          | ✅                                          |
| Encapsulated logic     | ✅                          | ✅                                          |
| Can be reused          | ✅                          | ✅                                          |
| Deployed independently | ❌                          | ✅                                          |
| System-wide singleton  | ❌                          | ✅ (one running instance across the system) |
| Example                | Controller, DAO, API client | Credit check service, Payment service       |

---

### 🔁 Relationship of Object → Component → Service

```plaintext
+-------------+     +-----------------+     +-----------------+
|   Object    | --> |    Component    | --> |     Service     |
+-------------+     +-----------------+     +-----------------+

Object: Smallest data + behavior unit
Component: Reusable unit made of objects
Service: Deployed business function built with components
```

---

## 🌐 Service-Oriented Architecture (SOA)

A **service** is a reusable, deployable unit that solves a business problem and communicates with other services via protocols (like HTTP).

### 🔄 Example Services:

- Credit Checking Service
- Loan Calculation Service
- Mortgage Application Processing Service

---

## 📡 What is a Distributed System?

A **distributed system** has multiple services on different machines working together as one logical system.

```plaintext
                    +---------------+
                    |    Client     |
                    +-------+-------+
                            |
                  +---------+----------+
                  |    HTTP Protocol    |
                  +---------+----------+
                            |
     +----------------+    +-----------------+   +------------------+
     |  Service A     |    |   Service B     |   |   Service C      |
     | (on Machine 1) |    |  (on Machine 2) |   |  (on Machine 3)  |
     +----------------+    +-----------------+   +------------------+
```

### ⚙️ Properties of Distributed Systems:

- **Resource Sharing**: Share software, data, and hardware
- **Fault-Tolerant**: Can continue operating if a node fails
- **Concurrent**: Executes tasks in parallel
- **Scalable**: Can handle more users by adding nodes
- **Heterogeneous**: Works across different OS and hardware

---

## 🧠 Understanding Nodes

- A **node** is any device on a network that can process and transmit data.
- In distributed systems, nodes run one or more services and communicate through protocols (e.g., HTTP, gRPC, AMQP).

---

## 🏛️ Distributed System Architectures

Distributed systems often follow one or more of the following architectural types:

```plaintext
Client-Server     ────> Centralized coordination (Web apps)
Three-Tier        ────> UI → Logic → Data separation
Peer-to-Peer      ────> Decentralized (e.g., BitTorrent)
Microservices      ───> Independent services for each feature
```

---

## ✅ Summary

- **Components** are modular, independent, and reusable building blocks
- **Component-based architecture** emphasizes separation of concerns via logical units
- **Services** are deployed independently and solve business needs
- **SOA** builds systems with loosely coupled, networked services
- **Distributed systems** run services on multiple machines to improve resilience, concurrency, and scalability

---
