# 📘 Introduction to Serverless Computing

After going through this document, you'll be able to:

- ✅ Define **serverless computing** and describe its core concepts.
- ✅ Identify key characteristics of serverless architecture.
- ✅ Understand how serverless compares to traditional, IaaS, and PaaS models.

---

## 💡 What Is Serverless Computing?

> The **Cloud Native Computing Foundation (CNCF)** defines serverless as:

> "The concept of building and running applications that do not require server management. It describes a finer-grained deployment model where applications, bundled as one or more functions, are uploaded to a platform and then executed, scaled, and billed in response to the exact demand needed at the moment."

### 🔧 In Simple Terms:

- Cloud providers **manage the infrastructure**.
- Developers **write and deploy small functions**.
- Applications scale **automatically based on demand**.
- You’re **billed for actual execution time**, not idle capacity.

---

## 🛠️ Components of Serverless

### 🔸 Function-as-a-Service (FaaS)

- Run discrete functions (e.g., AWS Lambda, Azure Functions).
- Stateless, event-triggered, and short-lived.

### 🔸 Backend-as-a-Service (BaaS)

- Managed backend services such as:
  - Cloud databases (e.g., Firebase)
  - Object storage (e.g., Amazon S3)
  - Messaging systems (e.g., Google Pub/Sub)

---

## 🕰️ Evolution of Computing Models

| Model             | Provision Time | Lifespan      | Management    |
| ----------------- | -------------- | ------------- | ------------- |
| Physical Machines | Weeks/Months   | Years         | Manual        |
| VMs (Virtual)     | Minutes        | Days/Weeks    | Automated     |
| Containers        | Seconds        | Minutes/Hours | Lightweight   |
| **Serverless**    | Milliseconds   | Seconds       | Fully managed |

---

## ⚙️ How Does Serverless Work?

1. **Write a Function**  
   Use languages like Python, Java, Node.js, Go, C#, etc.

2. **Upload to the Cloud**  
   Via CLI or UI to AWS Lambda, Azure, GCP, etc.

3. **Define Event Triggers**  
   Such as HTTP requests, database changes, or file uploads.

4. **Function is Executed**  
   Only when the event occurs → billed per invocation time.

---

## 📌 Characteristics of Serverless

| Characteristic          | Description                           |
| ----------------------- | ------------------------------------- |
| **Hostless**            | No server provisioning or management. |
| **Elastic**             | Auto-scales instantly with traffic.   |
| **Load-balanced**       | Requests are routed across instances. |
| **Stateless**           | No memory of previous invocations.    |
| **Event-driven**        | Only runs when triggered.             |
| **Highly available**    | Built-in fault tolerance.             |
| **Usage-based billing** | Billed per function execution.        |

---

## 🔄 Practical Example

> Let's say you want to **process a user-uploaded image** using serverless:

1. **User uploads an image** to S3.
2. **S3 triggers a Lambda function**.
3. Lambda performs:
   - Resize
   - Add watermark
   - Save to another bucket
4. All done **without managing any server**.

---

## 🧱 Serverless vs Other Cloud Models

```plaintext
Stack Responsibility by Model:

+----------------------+------------+---------+---------+-----------+-----------+
| Component            | Traditional|  IaaS   |  PaaS   | Serverless|   SaaS    |
+----------------------+------------+---------+---------+-----------+-----------+
| Application          |   ✅       |   ✅    |   ✅    |    ✅    |           |
| Data                 |   ✅       |   ✅    |   ✅    |           |           |
| Runtime              |   ✅       |   ✅    |         |           |           |
| Middleware           |   ✅       |   ✅    |         |           |           |
| OS                   |   ✅       |         |         |           |           |
| Virtualization       |   ✅       |         |         |           |           |
| Servers              |   ✅       |         |         |           |           |
| Storage/Networking   |   ✅       |         |         |           |           |
+----------------------+------------+---------+---------+-----------+-----------+

✅ = You manage it
(blank) = Cloud provider manages it
```

---

## 🎯 Benefits for Developers

- Write code → Upload → Done ✅
- Focus on business logic, not infrastructure.
- Improved productivity and deployment velocity.
- Use any supported language.
- Granular billing & high scalability.

---

## 📊 Serverless Architecture Diagram

```plaintext
                      ┌────────────────────────────┐
                      │     Cloud Provider         │
                      │  (e.g., AWS, Azure, GCP)   │
                      └────────────┬───────────────┘
                                   │
                 ┌─────────────────┼─────────────────┐
                 ▼                 ▼                 ▼
         ┌────────────┐   ┌────────────────┐   ┌──────────────┐
         │   Storage  │   │    Triggers    │   │   API GW     │
         │  (e.g. S3) │   │ (e.g. SQS, DB) │   │  (Optional)  │
         └────┬───────┘   └──────┬─────────┘   └──────┬───────┘
              │                  │                    │
              ▼                  ▼                    ▼
          ┌────────────────────────────────────────────┐
          │          Serverless Function(s)            │
          │  (e.g. Resize image, validate form, etc.)  │
          └────────────────────────────────────────────┘
                                   │
                                   ▼
                      ┌────────────────────────────┐
                      │  Processed result output   │
                      │  (DB, S3, Client API, etc.)│
                      └────────────────────────────┘
```

---

## ✅ Summary

You learned that:

- Serverless abstracts infrastructure for **simpler deployments**.
- Developers focus on **functions and events**, not servers.
- **Cloud provider** handles updates, patching, scaling, and billing.
- **Granular billing** means you pay only for usage.
- It’s a key evolution from traditional → virtual → container → serverless computing.

---
