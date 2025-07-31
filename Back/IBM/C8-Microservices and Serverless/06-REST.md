# 📘 What is REST?

## 🎯 Learning Objectives

After reading this document, you will be able to:

- Describe RESTful APIs
- Explain the key characteristics of a REST API
- Explain the benefits of using REST APIs

---

## 🧩 What is REST?

**REST** stands for **Representational State Transfer**. It is an **architectural style** that defines how applications should communicate over a network.

> 🔍 REST APIs provide a **flexible**, **lightweight** way to integrate applications and have become the most common method for connecting components in **microservices architectures**.

---

## 🧠 Key Characteristics of a REST API

A REST API must meet the following **three characteristics**:

### 1. Communication via HTTP

REST APIs manage all requests through **HTTP methods**. The standard operations are:

| HTTP Method | Action | Description                   |
| ----------- | ------ | ----------------------------- |
| POST        | Create | Create a new resource         |
| GET         | Read   | Retrieve an existing resource |
| PUT         | Update | Update an existing resource   |
| DELETE      | Delete | Remove a resource             |

> ✅ **Example:**
> To create a new user in a system:

```http
POST /api/users
Content-Type: application/json

{
  "name": "Alice",
  "email": "alice@example.com"
}
```

---

### 2. Stateless Communication

Each request contains **all the information** needed to process it. The server does **not store any client context** between requests.

> 📜 According to Roy Fielding (originator of REST):
> “Each request from client to server must contain all of the information necessary to understand the request, and cannot take advantage of any stored context on the server.”

> 🔁 **Example:**
> If a client wants to retrieve product info:

```http
GET /api/products/123
```

The server doesn't remember prior interactions with the client — it treats each request independently.

---

### 3. Uniform Interface

REST APIs expose a **consistent and predictable interface** for interacting with resources.

- **Resource-based URIs**: Each resource has a unique URI
- **Self-descriptive messages**: Responses contain all information the client needs
- **Statelessness**: No server-side session

> 🔍 **Example:**
> A product with ID `123` is always accessed via:

```http
GET /api/products/123
```

And the response might include:

```json
{
  "id": 123,
  "name": "Wireless Mouse",
  "price": 19.99
}
```

---

## 🚀 Benefits of REST APIs

- ✅ **Scalability**: Statelessness allows servers to handle more requests in parallel
- ✅ **Flexibility**: Lightweight and language-agnostic (often uses JSON)
- ✅ **Consistency**: Uniform interface makes integration predictable

> 🔧 **Example - Real-world REST API:** > [CEX.IO](https://cex.io), a cryptocurrency exchange, provides developers with access to Bitcoin and other crypto prices via a **REST API**.

You can retrieve the latest price of a currency pair:

```http
GET https://cex.io/api/ticker/BTC/USD
```

Response (JSON format):

```json
{
  "timestamp": "1639093821",
  "last": "49600.00",
  "high": "50000.00",
  "low": "47000.00"
}
```

## 📌 Summary

In this lesson, you learned:

- REST is an architectural style for designing networked applications
- REST APIs are **stateless**, **scalable**, and use **HTTP** methods like **POST**, **GET**, **PUT**, and **DELETE**
- REST APIs expose a **uniform interface** between components
- Real-world services like **CEX.IO** use REST to provide public access to their data
