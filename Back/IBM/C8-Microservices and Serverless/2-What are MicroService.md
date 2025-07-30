# 📘 What are Microservices?

## 🎯 Learning Objectives

By the end of this module, you will be able to:

- Define what microservices are
- Explain the benefits of microservices architecture
- Describe how microservices can be scaled

---

## 🧩 Overview: What Are Microservices?

**Microservices architecture** is an approach in which a **single application** is composed of **many smaller, independent services**, each responsible for a **specific business capability**.

### Key Characteristics:

- **Loosely coupled** and **independently deployable**
- Each service often has its own:

  - **Technology stack**
  - **Database**
  - **Data management model**

- Services communicate through:

  - **REST APIs**
  - **Event streaming**
  - **Message brokers**

- Services are aligned with **business functionality** and grouped by **bounded context**

✅ **Example:**
An e-commerce app may have separate microservices for:

- **Inventory Management**
- **User Accounts**
- **Order Processing**
- **Payment Gateway**

Each of these can be maintained, updated, and scaled independently.

---

## 🧪 Benefits of Microservices

### 🛠️ 1. Independent Deployment & Updates

- You can update or modify a **single microservice** without needing to re-deploy the whole application.

✅ **Example:**
You can fix a bug in the **Payment Service** without affecting **User Login** or **Inventory Services**.

---

### 🧰 2. Technology Stack Flexibility

- Each team can choose the **programming language** and tools that best suit the service’s requirements and the team's expertise.

✅ **Example:**

- The **Recommendation Service** might use **Python** and **TensorFlow**
- The **Auth Service** might be built in **.NET**

---

### 🚀 3. Individual Scalability

- Microservices allow for **horizontal scaling** of **individual components**.
- This means **adding instances** of the microservice that is under high load, without scaling the entire application.

✅ **Example:**
If the **Search Service** receives high traffic, it can be scaled out independently, without also scaling the **Checkout Service**.

---

### 💡 4. Efficient Infrastructure Usage

- Only services that need more resources get scaled, reducing overall cost and hardware waste compared to monolithic apps.

---

### 🔧 5. Reduced Risk & Easier Iteration

- Since services are **independent**, changes in one do not break others.
- Teams can iterate quickly with **low risk of regression** in unrelated parts.

✅ **Example:**
A failure in the **Email Notification Service** doesn’t bring down the **Order Processing Service**.

---

## 📈 Scaling Microservices

### 🔁 Horizontal Scaling (aka "Scaling Out")

- **Add more instances** of a service to meet increased demand.
- More efficient than vertical scaling (increasing resources on a single machine).

✅ **Example:**
During Black Friday sales, multiple instances of the **Checkout Service** can be deployed to handle the load.

---

### 🔄 State Management and Event Streaming

- **API calls** are good for **initializing state**, but not for staying updated.
- Use **event streaming** (via message brokers) to **broadcast state changes** to interested services.

✅ **Example:**
When a product goes out of stock, the **Inventory Service** can broadcast that event.

- The **Order Service** listens and updates availability in real-time.

---

## ✅ Summary

- Microservices architecture breaks down applications into **modular, independently scalable components**.
- Services:

  - Communicate via APIs, messages, and events
  - Are built and deployed independently
  - Can use **different tech stacks**

- **Horizontal scaling** allows targeting only the services under heavy load
- **Event streaming** improves responsiveness and scalability
