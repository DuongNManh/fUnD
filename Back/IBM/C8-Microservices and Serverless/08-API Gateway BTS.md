# 🛍️ Shopee-like API Gateway Strategy for Product Detail Page

In large-scale e-commerce platforms like **Shopee**, **Lazada**, **Tiki**, or **Amazon**, the strategy for handling API requests on product detail pages uses a **hybrid model**:

> 🔁 **API Gateway routing for client-driven fetches**
> 🔄 **Backend-for-Frontend (BFF) aggregation for stable composite data**
> 🧠 **Edge caching + dynamic content separation for performance & personalization**

---

## 🧩 What Happens When User Visits a Product Detail Page?

The frontend needs to show multiple pieces of data, which come from different backend microservices. Instead of one giant request, the system splits the responsibility smartly.

---

### 🖼️ Figure: Hybrid API Gateway Strategy

```plaintext
                                ┌─────────────────────┐
                                │      Client App     │
                                └────────┬────────────┘
                                         │
                 ┌───────────────────────┼──────────────────────────────┐
                 ▼                       ▼                              ▼
     GET /api/product/123/overview   GET /api/product/123/ratings   GET /api/product/123/reviews?page=1
           (aggregated)                      (Ratings Svc)                    (Ratings Svc)

      ┌────────────┬────────────┐
      ▼            ▼            ▼
Product Svc   Inventory Svc   Promotion Svc

                 ▼
        (via API Gateway or BFF)

                 ▲                              ▲                            ▲
       GET /api/seller/456/info      GET /api/product/123/shipping   GET /api/product/123/recommendations
         (Seller Service)               (Shipping Service)                (Recommendation Service)
```

---

## 🔄 API Request Breakdown

| API Endpoint                            | Purpose                                                | Aggregation                 | Personalization             | Cacheable        |
| --------------------------------------- | ------------------------------------------------------ | --------------------------- | --------------------------- | ---------------- |
| `/api/product/123/overview`             | Basic info: name, price, image, discount, availability | ✅ Yes (via BFF or Gateway) | ❌ No                       | ✅ Yes (via CDN) |
| `/api/product/123/ratings-summary`      | Avg. score, count                                      | ❌ No                       | ❌ No                       | ✅ Yes           |
| `/api/product/123/reviews?page=1`       | Customer reviews (paginated)                           | ❌ No                       | ✅ Yes (e.g. liked reviews) | ❌ No            |
| `/api/product/123/recommendations`      | Related products                                       | ❌ No                       | ✅ Yes                      | ❌ No            |
| `/api/product/123/shipping?location=HN` | Delivery ETA & cost                                    | ❌ No                       | ✅ Yes                      | ❌ No            |
| `/api/seller/456/info`                  | Seller info                                            | ❌ No                       | ❌ No                       | ✅ Yes           |

---

## ✅ Why Use This Hybrid Strategy?

| Reason                                | Explanation                                                       |
| ------------------------------------- | ----------------------------------------------------------------- |
| ⚡ **Fast TTI (Time-to-Interactive)** | Load basic product info quickly with minimal aggregation          |
| 📦 **Scalable Services**              | Services like Ratings, Inventory, etc., scale independently       |
| 🧠 **Separation of Concerns**         | Business logic stays out of the API Gateway                       |
| 🌐 **Global Optimization**            | Product overviews are cached at CDN, dynamic content fetched live |
| 📱 **Client Flexibility**             | Frontend apps can control when/how each part of the page loads    |

---

## 🔧 Tools Typically Used

| Layer              | Tools/Tech                                            |
| ------------------ | ----------------------------------------------------- |
| **API Gateway**    | AWS API Gateway, YARP (.NET), Kong, Apigee            |
| **BFF Aggregator** | Node.js, ASP.NET Core Minimal API, NestJS             |
| **Frontend**       | React, Vue, Flutter, etc.                             |
| **Caching Layer**  | CDN (CloudFront, Cloudflare), Redis                   |
| **Service Layer**  | Microservices: ProductService, InventoryService, etc. |

---

## 📌 Summary

- Shopee-style platforms use **hybrid request models** to balance performance and flexibility.
- Product detail pages are built using **both aggregated APIs** and **independent data fetches**.
- API Gateway is used primarily for **routing, auth, and traffic control**, not heavy logic.
- **Frontend** triggers multiple requests to render a full page progressively.
- **Edge caching and personalization** are key to fast yet tailored experiences.

---

✅ **Pro Tip**: Aggregate only the **stable, common data** needed at first render, and let your frontend lazily load the rest based on user interaction or priority.

---
