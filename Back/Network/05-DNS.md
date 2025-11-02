# 🌐 Domain Name System (DNS)

The **Domain Name System (DNS)** is a fundamental Internet service that translates **human-readable names** (like `example.com`) into **IP addresses** (like `93.184.216.34`), which computers use to communicate.

---

## 🔁 What DNS Does

```txt
You enter in browser:   https://www.example.com
DNS resolves it to IP:  93.184.216.34
Browser then connects to that IP.
```

✅ DNS allows us to use **easy-to-remember domain names** instead of IP numbers.

---

### 🗃️ DNS as a Distributed Database

DNS can also be seen as a **globally distributed database**, stored across many computers. Each record maps:

- A **hostname** (e.g., `mail.google.com`)
- To its **corresponding IP address** (e.g., `142.250.190.69`)

---

### 🧩 3 Key Components of DNS

#### 1. 🧾 **Name Space**

Defines the **rules and hierarchy** for valid domain names.

- Examples of legal names:

  - `example.com`
  - `sub.domain.co.uk`

- Uses a **hierarchical structure**, separated by dots `.`:

```txt
root
 └── com
     └── example
         └── www
```

#### 2. 🌐 **Globally Distributed Database**

- Implemented on a **network of name servers** around the world.
- These **DNS servers** handle requests and store mappings of domain names to IP addresses.

Types of DNS servers:

- **Root Servers**
- **Top-Level Domain (TLD) Servers** (e.g., `.com`, `.org`)
- **Authoritative Servers** (store domain-specific records)

```txt
[Browser] → [Resolver] → [Root Server] → [TLD Server] → [Authoritative DNS]
```

#### 3. 🔍 **Resolver**

- Built-in **software in operating systems & applications**.
- Knows how to **ask DNS servers** for the correct IP.
- Handles the DNS query and returns the resolved address.

---

### 📊 DNS Summary Table

| Component                | Description                                              |
| ------------------------ | -------------------------------------------------------- |
| **Name Space**           | Syntax and structure of valid domain names               |
| **Distributed Database** | Global collection of name servers mapping names to IPs   |
| **Resolver**             | Software that issues DNS queries and processes responses |

---

### 🧠 Visual Summary

```txt
+------------------+          +-----------------------+
|  User Input      |  --->    | Resolver              |
|  www.example.com |          | (Browser / App / OS)  |
+------------------+          +----------+------------+
                                          |
                                     DNS Query
                                          v
                 +----------------------+---------------------+
                 |        DNS Name Server Hierarchy           |
                 +----------------------+---------------------+
                        | Root Server (.)
                        v
                    TLD Server (.com)
                        v
              Authoritative Server (example.com)
                        |
                        v
             Returns IP: 93.184.216.34
```

---

### ✅ Recap: DNS in Action

1. You type a domain name.
2. The **resolver** in your OS formulates a DNS query.
3. The query travels through **name servers** (root → TLD → authoritative).
4. The **IP address** is returned to your app or browser.
5. Your system connects to that IP.

---
