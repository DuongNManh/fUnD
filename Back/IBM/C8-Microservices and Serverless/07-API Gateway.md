# 🧩 Introduction to API Gateway

## 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Explain what an **API Gateway** is
- Describe the **benefits** and **drawbacks** of using an API Gateway
- Identify **common API Gateway products**, both managed and open-source

---

## 🔍 What is an API Gateway?

An **API Gateway** is an **API management tool** that acts as a **single entry point** between a client and a set of backend services.

> It aggregates requests to multiple services and returns a **unified response** to the client.

---

### 📊 Figure: API Gateway Architecture

```plaintext
                    +------------------+
                    |     Client       |
                    +--------+---------+
                             |
                             ▼
                    +--------+---------+
                    |    API Gateway   |  ← Central entry point
                    +--------+---------+
                             |
     +-----------+-----------+-----------+-----------+
     |           |           |           |           |
     ▼           ▼           ▼           ▼           ▼
+----------+ +----------+ +----------+ +----------+ +--------------+
| Product  | | Inventory| |  Orders  | | Billing  | | Authentication|
| Service  | | Service  | | Service  | | Service  | | Service       |
+----------+ +----------+ +----------+ +----------+ +--------------+
```

> Example: In an **online store** app, the API Gateway provides unified access to:
>
> - `Product Service`: product name, price, description
> - `Inventory Service`: stock levels
> - `Order Service`: place/track orders
> - `Authentication Service`: login & user validation

---

## ✅ Benefits of Using an API Gateway

| Benefit                           | Description                                                                            | Example                                               |
| --------------------------------- | -------------------------------------------------------------------------------------- | ----------------------------------------------------- |
| 🔐 **Security & Throttling**      | Protects APIs from overuse or abuse with **rate limiting** and **authentication**      | Use JWT or OAuth with throttling rules                |
| 📈 **Monitoring & Analytics**     | Understand API usage patterns via integrated **metrics** and **logging**               | Use Prometheus, Azure Monitor, or built-in tools      |
| 💰 **Monetization**               | Enable billing for API usage                                                           | Bill by API call, e.g., per 1,000 requests            |
| 🧩 **Service Aggregation**        | Combines multiple service calls into one request                                       | Retrieve product info, stock, and pricing in one call |
| 🔄 **Seamless Service Updates**   | Add/remove/replace backend services **without breaking the client**                    | Replace `OrderService` with a new version             |
| 🔧 **Simplified Client Logic**    | Client doesn’t need to know how services are distributed                               | Mobile app only talks to the gateway                  |
| 🔌 **Standardized Communication** | Unified protocol regardless of internal communication types (HTTP/gRPC/message queues) | Expose all services via HTTP REST interface           |

> 💡 **Example**: A mobile app retrieves product details in one request:

```
GET /api/products/123/details
```

Behind the scenes, the API Gateway queries:

- Product Service → for name, price
- Inventory Service → for stock
- Ratings Service → for customer reviews

---

## ⚠️ Drawbacks of an API Gateway

| Drawback                              | Description                                                        |
| ------------------------------------- | ------------------------------------------------------------------ |
| 🛠 **Extra Development & Maintenance** | Gateway is an additional component to design, deploy, and maintain |
| 📉 **Single Point of Failure**        | If not highly available or replicated, the whole app may go down   |
| 🕒 **Increased Latency**              | Adds a network hop and request aggregation delay                   |

> 📌 **Mitigation Tips**:
>
> - Use **load balancing** and **caching**
> - Deploy with **high availability** (e.g., active-active)
> - Monitor **response times** and optimize aggregation logic

---

## 🛒 API Gateway Products

There are many **managed** and **open-source** options available:

### 🔹 Managed Gateways

| Provider            | Product                 |
| ------------------- | ----------------------- |
| **IBM**             | DataPower Gateway       |
| **Google**          | Apigee, Cloud Endpoints |
| **Microsoft Azure** | API Management          |
| **AWS**             | Amazon API Gateway      |

### 🔸 Open Source Gateways

| Product           | Notes                                          |
| ----------------- | ---------------------------------------------- |
| **Kong**          | Most popular, plugin ecosystem                 |
| **Apache APISIX** | Fast, scalable, cloud-native                   |
| **Tyk**           | Has both open-source and managed options       |
| **Gloo**          | Enterprise-grade, supports gRPC, REST, GraphQL |

---

## 📌 Summary

In this lesson, you learned:

- An **API Gateway** sits between clients and backend services to aggregate requests
- It enhances **security**, **scalability**, **observability**, and **client simplicity**
- It enables **seamless service updates**, **rate limiting**, **authentication**, and **analytics**
- Drawbacks include additional complexity, potential single point of failure, and added latency
- You can choose from **managed products** (e.g., AWS, Azure, Apigee) or **open-source tools** (e.g., Kong, Tyk, Gloo)

---

✅ **Next Steps**:
Try building a simple API Gateway using [Kong Gateway](https://konghq.com/kong/) or explore [AWS API Gateway](https://aws.amazon.com/api-gateway/) for managed deployment.

---
