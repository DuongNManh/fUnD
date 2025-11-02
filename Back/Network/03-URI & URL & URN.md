# URI, URL & URN

## 🌐 URI (Uniform Resource Identifier)

A **URI** is a specially formatted string that **identifies a resource** on the internet or a local network (LAN).

- Can point to:
  - A **web page**
  - A **file**
  - An **email address**
  - Any network resource

---

### 🔍 URI Components

A URI typically consists of the following components:

```txt
scheme://authority/path?query#fragment
```

| Component | Description                                  | Example                 |
| --------- | -------------------------------------------- | ----------------------- |
| Scheme    | Protocol used (e.g., `http`, `https`, `ftp`) | `https`                 |
| Authority | Domain and optional port                     | `www.example.com:443`   |
| Path      | Resource location on the host                | `/products/item1`       |
| Query     | Optional parameters (key=value)              | `?color=red&size=large` |
| Fragment  | Optional anchor within the resource          | `#reviews`              |

🔗 **Example URI**:

```txt
https://www.example.com:443/products/item1?color=red#reviews
```

---

## 🌍 URL (Uniform Resource Locator)

A **URL** is a **subset of URI** that specifies the **location** of a resource and **how to access it**.

- It combines the **protocol (scheme)** and **resource location**
- URLs are what we commonly use when visiting websites, downloading files, or accessing APIs.

---

### 🧱 URL Structure

Just like a URI, a URL has the following format:

```txt
scheme://host[:port]/path[?query][#fragment]
```

🔗 **Example URL:**

```txt
https://www.example.com:443/products/item1?color=red#reviews
```

| Component | Value             | Description                             |
| --------- | ----------------- | --------------------------------------- |
| Scheme    | `https`           | Protocol used to access the resource    |
| Host      | `www.example.com` | Server's domain name                    |
| Port      | `443` (optional)  | Network port (default for HTTPS is 443) |
| Path      | `/products/item1` | Resource path on the server             |
| Query     | `?color=red`      | Parameters sent with request            |
| Fragment  | `#reviews`        | Anchor within the page or document      |

---

### 🌐 Common URL Examples

| Type             | Example URL                                   |
| ---------------- | --------------------------------------------- |
| Website page     | `https://example.com/about`                   |
| File download    | `https://example.com/files/report.pdf`        |
| API endpoint     | `https://api.example.com/v1/users?id=123`     |
| FTP resource     | `ftp://ftp.example.com/data/log.txt`          |
| Email (URI only) | `mailto:support@example.com` (URI, not a URL) |

---

## 🌐 How URLs Work with DNS

URLs rely on the **Domain Name System (DNS)** to **symbolically address hosts**.

- DNS converts **domain names** (e.g., `www.example.com`) into **IP addresses** (e.g., `192.0.2.1`)
- After locating the host, a **file path-like syntax** is used to locate the specific resource.

```txt
URL: https://www.example.com/products/item1

DNS resolves:
  www.example.com --> 192.0.2.1

File-like path:
  /products/item1
```

✅ This makes mapping URLs to physical resources straightforward in **web servers and browsers**.

---

## 🏷️ URN (Uniform Resource Name)

A **URN** is a type of **URI** that uses the `urn:` scheme to **name** a resource rather than locate it.

- It is **location-independent**
- Often used to represent **persistent, globally unique names**
- Does **not guarantee resource availability**

### 🧱 URN Structure

```txt
urn:<namespace-identifier>:<namespace-specific-string>
```

🔗 **Example URNs**:

```txt
urn:isbn:0451450523            (book identified by ISBN)
urn:uuid:6ba7b810-9dad-11d1-80b4-00c04fd430c8  (a UUID)
```

---

### 📊 URI vs URL vs URN

| Feature          | URI                         | URL                              | URN                   |
| ---------------- | --------------------------- | -------------------------------- | --------------------- |
| Stands for       | Uniform Resource Identifier | Uniform Resource Locator         | Uniform Resource Name |
| Purpose          | Generic resource identifier | Identifies + locates resource    | Identifies by name    |
| Locates resource | Maybe                       | ✅ Yes                           | ❌ No                 |
| Requires DNS     | Maybe                       | ✅ Yes                           | ❌ No                 |
| Example          | `mailto:user@example.com`   | `https://example.com/index.html` | `urn:isbn:0451450523` |

---

### 🔍 Summary Diagram

```txt
                  ┌───────────────────────────────────┐
                  │              URI                  │
                  │  (Identifies any resource)        │
                  └───────────────────────────────────┘
                          ▲                   ▲
                          │                   │
              ┌───────────┘           ┌───────┴────────┐
              │                       │                │
         ┌──────────┐           ┌──────────┐     ┌───────────────┐
         │   URL    │           │   URN    │     │  Other URIs   │
         │ Locator  │           │ Name     │     │ (e.g., mailto)│
         └──────────┘           └──────────┘     └───────────────┘
```

---

## ✅ Quick Recap

| Concept | Identifies? | Locates? | Uses DNS? | Example                    |
| ------- | ----------- | -------- | --------- | -------------------------- |
| URI     | ✅ Yes      | Maybe    | Maybe     | `mailto:info@example.com`  |
| URL     | ✅ Yes      | ✅ Yes   | ✅ Yes    | `https://example.com/page` |
| URN     | ✅ Yes      | ❌ No    | ❌ No     | `urn:isbn:0451450523`      |

---
