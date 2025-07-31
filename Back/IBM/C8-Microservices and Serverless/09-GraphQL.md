# 📘 Basics of GraphQL

## 🎯 Learning Objectives

After studying this module, you will be able to:

- Describe what GraphQL is
- Explain the key characteristics of a GraphQL API
- Understand the benefits of using GraphQL
- See how Netflix uses GraphQL in a federated architecture

---

## 🧾 What is GraphQL?

GraphQL is a **query language for your API** and a runtime for executing those queries with your data. It allows clients to request exactly the data they need—nothing more, nothing less.

- It is **language agnostic** (you can build GraphQL APIs in any language).
- Instead of hitting multiple REST endpoints, you can access **all the required data from a single endpoint**.

Example:

```graphql
query {
  product(id: "123") {
    name
  }
}
```

Response:

```json
{
  "data": {
    "product": {
      "name": "Apple AirPods Pro"
    }
  }
}
```

✅ **Only the data you ask for is returned**.

---

## 🔁 REST vs. GraphQL

| Aspect           | REST API                       | GraphQL                                     |
| ---------------- | ------------------------------ | ------------------------------------------- |
| Data retrieval   | Multiple endpoints             | Single endpoint                             |
| Data returned    | Fixed by server                | Defined by client                           |
| Versioning       | Often uses versioning (v1, v2) | No need for versioning                      |
| Over/Under-fetch | Common                         | Eliminated                                  |
| Extensibility    | Requires new endpoints         | Just extend schema without breaking clients |

---

## 🛠️ GraphQL Components

| Component | Purpose                   | Analogy in REST          |
| --------- | ------------------------- | ------------------------ |
| Query     | Fetch data                | GET                      |
| Mutation  | Modify or post data       | POST/PUT/DELETE          |
| Schema    | Defines types & structure | N/A                      |
| Resolver  | How fields are populated  | Controller/Service logic |

---

## 🎥 Netflix Case Study

Netflix builds a **federated GraphQL API** known as the **Studio API** to unify and simplify access to data across their microservices.

Each domain team (like Talent, Content, Production, etc.) owns its **portion of the schema and logic**, and the Studio API **composes them together** into one unified API.

This makes it easy for frontend developers to query cross-domain data without worrying about backend complexity.

### 📊 Architecture Overview (ASCII Diagram)

```
                             ┌──────────────────┐
                             │   Client App     │
                             └────────┬─────────┘
                                      │
                                      ▼
                            ┌────────────────────┐
                            │   Studio GraphQL   │
                            │      Gateway       │
                            └────────┬───────────┘
                                     │
         ┌───────────────────────────┼───────────────────────────────┐
         ▼                           ▼                               ▼
 ┌──────────────┐          ┌─────────────────┐              ┌──────────────────┐
 │ Content Team │          │  Talent Team    │              │  Production Team │
 │ (Shows, Ep.) │          │ (Cast, Roles)   │              │ (Budget, Shoot)  │
 └──────┬───────┘          └─────────────────┘              └──────────────────┘
        │
        ▼
 ┌───────────────┐
 │ Licensing Svc │
 │ (Rights, Regions) │
 └─────────────────┘
```

Each service defines its own schema and resolvers. The Studio GraphQL Gateway **stitches them together** into a federated API.

---

## ✅ Summary

- GraphQL allows clients to request **exactly what they need**.
- It eliminates **over-fetching and under-fetching** problems.
- Only **one endpoint** is needed for all queries.
- Netflix uses **federated GraphQL architecture** to empower domain teams to expose their data independently, while providing a unified API to clients.

---
