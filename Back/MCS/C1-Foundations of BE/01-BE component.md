# 🖥️ Back-End Development Components

## 🔎 Overview

Back-end development focuses on **three main components** that work together to deliver data and services to the front end:

1. **Servers** – run the application logic
2. **Databases** – store and manage data
3. **APIs** – connect the front-end with the back-end

---

## ⚙️ Core Components

### 1. 🖧 Servers

* Powerful machines that **run application code**
* Receive requests from the front end
* Apply **business logic and processing**
* Send responses back to the client
* Manage system **resources** (CPU, memory, threads)

---

### 2. 🗄️ Databases

* Store and organize **user data, transactions, and app state**
* Allow data to be **queried, updated, and retrieved**
* Ensure **consistency and integrity**
* Support various **query languages** (e.g., SQL)
* Examples: **PostgreSQL, MySQL, MongoDB**

---

### 3. 🔗 APIs (Application Programming Interfaces)

* Define **rules** for accessing data/services
* Allow different systems to **communicate**
* Standardize formats like **JSON** or **XML**
* Provide **security mechanisms** (auth, tokens)
* Examples: REST, GraphQL, gRPC

---

## 📊 How They Work Together

```plaintext
+-------------+        +-------------+        +-------------+        +-------------+
|  Front-End  |  --->  |   API/Route |  --->  |   Logic     |  --->  |  Database   |
| (User UI)   |        | (e.g., /add)|        | (Process)   |        | (SQL/ORM)   |
+-------------+        +-------------+        +-------------+        +-------------+
          ⬍                     ⬍                     ⬍                      ⬍
  HTML/CSS/JS         Express/Flask/Django    Node/Python/Java       PostgreSQL/MySQL
```

---

✅ **Takeaway**:

* **Servers** execute the logic.
* **Databases** store and manage the data.
* **APIs** connect everything together.

---
