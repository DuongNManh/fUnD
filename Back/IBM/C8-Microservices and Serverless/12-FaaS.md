# Introduction to the FaaS Model

## 🎯 Learning Objectives

By the end of this document, you will be able to:

- Describe what Function-as-a-Service (FaaS) is.
- Explain the benefits of the FaaS model.
- Describe the principles and best practices of FaaS.

---

## 📘 What is FaaS?

**Function-as-a-Service (FaaS)** is a cloud computing model that allows developers to execute discrete pieces of code (functions) in response to events—without managing infrastructure.

### 🔍 Characteristics of FaaS:

- Subset of **Serverless Computing**.
- Applications are broken into **individual functions**.
- Functions are **stateless**.
- Can be deployed on **hybrid cloud** or **on-premises** environments.
- Executes in **milliseconds** and processes **individual requests in parallel**.
- **Lightweight** and highly **decoupled**.
- **Pay-per-use** billing model (only pay for execution time).

### 🧠 Key Benefits:

| Feature                | Description                                          |
| ---------------------- | ---------------------------------------------------- |
| Cost Efficiency        | Pay only for the execution duration of the function. |
| Auto Scalability       | Functions scale independently and automatically.     |
| High Availability      | FaaS is distributed across multiple regions/Zones.   |
| Reduced Time-to-Market | Focus on code, not infrastructure.                   |

---

## 🧱 Serverless Stack Components

A typical **Serverless stack** includes:

1. **FaaS (Function-as-a-Service)**: Code executed in response to events.
2. **BaaS (Backend-as-a-Service)**: Third-party services (e.g., databases, storage).
3. **API Gateway**: Routes incoming requests to the correct function.

### 🔄 Flow of Events:

         ┌────────────┐
         │  Client    │
         └────┬───────┘
              │  HTTP Request / Event
              ▼
       ┌──────────────┐
       │ API Gateway  │
       └────┬─────────┘
            │  Invoke Function
            ▼
      ┌──────────────┐
      │  Function    │
      └────┬─────────┘
           │  Optional: Backend Call
           ▼
      ┌─────────────┐
      │   BaaS      │
      └────┬────────┘
           │  Result
           ▼
      ┌──────────────┐
      │  Function    │
      └────┬─────────┘
           │  Response
           ▼
       ┌──────────────┐
       │ API Gateway  │
       └────┬─────────┘
            │  Final Response
            ▼
         ┌────────────┐
         │  Client    │
         └────────────┘

---

## 🖼️ Real-World Example: Profile Picture Upload

**Scenario**: A user uploads a profile picture, and a thumbnail is generated.

```plaintext
                    ┌──────────────┐
                    │  Client App  │
                    └─────┬────────┘
                          │ Upload Image
                          ▼
                ┌──────────────────────────┐
                │ Object Storage (Bucket)  │
                └────────┬─────────────────┘
                         │ Event Trigger
                         ▼
               ┌────────────────────────┐
               │  IBM Cloud Function    │
               │ (Create Thumbnail)     │
               └────────┬───────────────┘
                        │ Save Thumbnail
                        ▼
                ┌──────────────────────────┐
                │ Object Storage (Thumbs)  │
                └──────────────────────────┘
```

---

## ✅ Best Practices

- Keep each function **focused** on a single task.
- Avoid excessive **third-party libraries**.
- Use **external caches** to maintain state if needed.
- Don’t over-decompose—too many functions can lead to increased complexity and costs.

---

## ☁️ FaaS Providers

### 🔹 Managed Providers

| Provider               | Platform                |
| ---------------------- | ----------------------- |
| AWS Lambda             | Amazon Web Services     |
| Azure Functions        | Microsoft Azure         |
| Google Cloud Functions | Google Cloud            |
| IBM Cloud Functions    | IBM Cloud               |
| OpenShift Functions    | Red Hat OpenShift       |
| Others                 | Netlify, Oracle, Twilio |

### 🔸 Self-Managed Frameworks

| Platform   | Description                                      |
| ---------- | ------------------------------------------------ |
| OpenFaaS   | Turns any Linux/Windows process into a function. |
| Fission    | FaaS framework on Kubernetes.                    |
| Knative    | Kubernetes-based serverless platform.            |
| Fn Project | Container-native serverless platform.            |

---

## 🧾 Summary

You’ve learned that:

- **FaaS** allows executing code in response to events without managing infrastructure.
- It is stateless, auto-scalable, cost-efficient, and easy to deploy.
- A serverless architecture typically includes **FaaS, BaaS**, and an **API Gateway**.
- Real-world use cases include thumbnail generation, webhook triggers, IoT event processing, and more.

> "Build only what you need, when you need it. FaaS makes that possible."

---
