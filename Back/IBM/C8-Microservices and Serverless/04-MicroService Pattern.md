# 📘 Microservices Patterns

## 🎯 Learning Objectives

By the end of this module, you will be able to:

- Identify common architectural patterns used with microservices
- Explain how each pattern addresses specific challenges
- Understand when and how to apply each pattern effectively

---

## 🧩 Overview

Microservices architecture provides flexibility and scalability — but it introduces complexity too. To address common challenges, several **design patterns** are commonly used in microservices systems.

Key patterns discussed:

- Single-Page Application (SPA)
- Backend for Frontend (BFF)
- Strangler Pattern
- Service Discovery Pattern
- Entity & Aggregate Pattern
- Adapter Pattern

---

## 🖥️ Pattern 1: Single-Page Application (SPA)

### 📌 Description

A **Single-Page Application (SPA)** is a web application that loads a **single HTML page** and updates content dynamically using **JavaScript** and **REST API calls**, rather than reloading or navigating to new pages.

### 🔗 Characteristics

- Built with HTML, CSS, and JavaScript
- Updates portions of the screen dynamically
- Provides a **fluid, responsive user experience**
- Heavily reliant on **backend REST APIs**

### ✅ Benefits

- Fast, seamless UI
- Reduced client-server communication overhead

### ⚠️ Tradeoffs

- More logic and responsibility shifts to backend services
- Not ideal for multi-channel (mobile + desktop) scenarios

---

## 📱 Pattern 2: Backend for Frontend (BFF)

### 📌 Description

The **Backend for Frontend (BFF)** pattern creates a dedicated backend service for **each frontend client** (e.g., web, mobile, smartwatch).

### 🔗 Characteristics

- Custom backends for each UI channel
- Each BFF orchestrates calls to underlying services
- Encapsulates UI-specific backend logic

### ✅ Benefits

- Optimized performance for each device type
- Allows **device-specific data shaping and filtering**
- Prevents bloated general-purpose APIs

### ⚠️ Tradeoffs

- Slight increase in code duplication and maintenance
- Requires maintaining multiple backends

### 💡 Example

- Web and Mobile apps access the same system

  - Web BFF provides **full dataset**, high-res images
  - Mobile BFF provides **reduced payload**, thumbnails, and lightweight logic

---

## 🌱 Pattern 3: Strangler Pattern

### 📌 Description

The **Strangler Pattern** helps **incrementally refactor** a monolithic application by replacing parts of it with microservices over time.

### 🔗 Process

1. **Transform**: Create a parallel new service for a specific domain or feature.
2. **Coexist**: Both monolith and new microservice handle different routes in the same URL space.
3. **Eliminate**: Gradually deprecate the monolithic components until fully replaced.

### ✅ Benefits

- Reduces risk of full system rewrite
- Enables gradual migration and testing
- Avoids downtime during migration

### 💡 Example

- Migrate `/users/profile` feature of a monolithic web app into a new microservice
- Redirect only that route to the new service
- Eventually, replace other parts until the monolith is gone

---

## 🔎 Pattern 4: Service Discovery

### 📌 Description

In microservices, services frequently scale, move, or restart. **Service Discovery** allows services to **locate and communicate with each other dynamically**.

### 🔗 Characteristics

- Automatically tracks service availability and addresses
- Often integrated with load balancers
- Supports health checks and failover

### ✅ Benefits

- Resilience to scaling, upgrades, and failures
- Helps maintain service communication consistency

### 💡 Example

- A load balancer or service registry (e.g., **Consul**, **Eureka**) automatically routes traffic to healthy instances of the `OrderService`.

---

## 📦 Pattern 5: Entity and Aggregate

### 📌 Description

Used in **Domain-Driven Design (DDD)**, this pattern organizes data models into logical **aggregates** and **entities**.

### ✅ Benefits

- Maintains business consistency within aggregates
- Simplifies transaction management

### 💡 Example

- In an e-commerce app:

  - **Order** is an aggregate
  - Includes **products**, **shipping address**, and **payment status** grouped by buyer

---

## 🔌 Pattern 6: Adapter Pattern

### 📌 Description

The **Adapter Pattern** helps connect two incompatible systems by **translating between interfaces or formats**.

### ✅ Benefits

- Enables integration with third-party services
- Keeps core logic independent from external APIs

### 💡 Example

- If your system uses XML and a third-party API only accepts JSON, an **adapter microservice** can transform data between the two formats

---

## ✅ Summary

| Pattern                  | Purpose                                              | Example Use Case                                     |
| ------------------------ | ---------------------------------------------------- | ---------------------------------------------------- |
| **SPA**                  | Dynamic frontends using backend APIs                 | Single-page booking or dashboard app                 |
| **Backend for Frontend** | Optimizes frontend per channel                       | Separate backends for mobile and web UIs             |
| **Strangler Pattern**    | Incremental migration from monolith to microservices | Gradually refactor a legacy system                   |
| **Service Discovery**    | Dynamic service registration and communication       | Routing requests to available microservice instances |
| **Entity & Aggregate**   | Data modeling using DDD                              | Order management in ecommerce                        |
| **Adapter Pattern**      | Connect incompatible systems                         | Bridging internal system with third-party API        |

---
