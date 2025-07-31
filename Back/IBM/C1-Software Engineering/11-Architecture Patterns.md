# 📐 Architectural Patterns in Software

## 🎯 Learning Objectives

After studying this guide, you will be able to:

- Describe common architectural patterns: **2-tier**, **3-tier**, **peer-to-peer**, **event-driven**, and **microservices**
- Provide real-world examples for each pattern
- Understand how patterns may be combined or contrasted

---

## 🧩 What is an Architectural Pattern?

An **architectural pattern** is a repeatable solution to common problems in software architecture.
These patterns highlight internal structures and interactions in software systems.

🧠 Note: Patterns often **share characteristics** and **can be combined**, depending on the system design.

---

## 🧱 Common Architectural Patterns Covered

1. 2-Tier (Client-Server)
2. 3-Tier (Presentation, Logic, Data)
3. Peer-to-Peer (P2P)
4. Event-Driven
5. Microservices

Other patterns not covered in detail: MVC, Message-Broker, Blackboard, Pipe-Filter, Controller-Responder

---

## 1️⃣ 2-Tier Architecture (Client-Server)

A **client-server** model where:

- The **client** has the interface and makes requests
- The **server** handles data/services

📊 **Diagram**:

```
[Client] ⇄ [Server]
```

📱 **Examples**:

- Messaging apps (e.g., texting)
- Database clients (e.g., MySQL Workbench)

---

## 2️⃣ 3-Tier Architecture (Presentation, Logic, Data)

A **layered architecture** with three logical and physical tiers:

1. **Presentation Tier**: UI
2. **Application Tier**: Business logic
3. **Data Tier**: Storage/Database

📊 **Diagram**:

```
[Presentation Layer]
        ⇅
[Application Layer]
        ⇅
    [Data Layer]
```

🌐 **Example**:

- Web apps with:

  - Web server (UI)
  - Application server (logic)
  - Database server (storage)

---

## 3️⃣ Peer-to-Peer Architecture (P2P)

A **decentralized network** where each node is **both a client and a server**.

📊 **Diagram**:

```
 [Node A] ⇄ [Node B]
    ⇅         ⇅
 [Node C] ⇄ [Node D]
```

🪙 **Example**:

- Blockchain (Bitcoin, Ethereum)
- File sharing (BitTorrent)

🧠 **Key Idea**:

- No central server
- Nodes share CPU, bandwidth, or storage

---

## 4️⃣ Event-Driven Architecture

Architecture focused on **events** triggering **actions** via **producers**, **routers**, and **consumers**.

📊 **Diagram**:

```
[Producer] → (Event) → [Event Router] → [Consumer]
```

🚗 **Example**:

- Ride-sharing apps (Uber, Lyft)

  - Rider sends ride request (event)
  - Event routed to nearby driver (consumer)

🧠 Events can come from:

- Users (clicks)
- Program state changes
- Other systems

---

## 5️⃣ Microservices Architecture

Application broken into **independent services** communicating via APIs.

📊 **Diagram**:

```
            [Client]
                ⇅
          [API Gateway]
   ⇅        ⇅         ⇅
[Service A] [Service B] [Service C]
```

📱 **Example**:

- Social media:

  - Account service
  - Friend recommendation
  - Content delivery
  - Ads service

🧠 Key Concepts:

- Each service does **one thing well**
- Communication managed by **API Gateway** and **Orchestration**

---

## 🔄 Combining Patterns

Patterns can be **combined** in modern systems:

✔ Examples:

- Microservices can be part of a 3-tier system
- P2P systems can use event-driven interactions

❌ Incompatible:

- **P2P ≠ 2-Tier**: In 2-tier, roles are fixed (client/server), while in P2P, each node is both.

---

## ✅ Summary Table

| Pattern       | Description                            | Example                    |
| ------------- | -------------------------------------- | -------------------------- |
| 2-Tier        | Client interacts with a server         | Messaging apps, DB clients |
| 3-Tier        | Presentation → Logic → Data            | Web applications           |
| Peer-to-Peer  | Nodes act as both client and server    | Bitcoin, File sharing      |
| Event-Driven  | Producers trigger events for consumers | Ride-hailing apps          |
| Microservices | Modular services with APIs             | Social media platforms     |

---

## 🧠 Final Notes

- Choose architecture based on **scalability**, **maintainability**, and **performance needs**
- Understand trade-offs in **complexity**, **deployment**, and **communication overhead**
