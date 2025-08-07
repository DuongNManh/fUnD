## 🎥 **Security Concepts and Terminology**

**Welcome to "Security Concepts and Terminology"!**

- Define **key security terms**
- Explain **core security concepts**

---

### 🆔 Authentication vs. Authorization

Let’s start with two words that are often confused: **Authentication** and **Authorization**.

- **Authentication** is the process of **verifying identity**.
  You’re checking, “Are you really who you say you are?”

- **Authorization** is about **access rights**.
  Once authenticated, **what are you allowed to do?**

**Plain-text diagram:**

```
+-----------------------+      +----------------------+
|   Authentication      |      |    Authorization     |
|  Who are you?         | ---> | What can you access? |
+-----------------------+      +----------------------+
```

🔑 _Authentication comes first._
🔒 _Authorization comes next._

---

### 🔐 Encryption

**Encryption** is the process of **encoding information** so only **authorized parties** can access it.

There are two main types:

1. **Symmetric Encryption**

   - Same key for **encryption and decryption**
   - Fast, but both sender and receiver must share the key

2. **Asymmetric Encryption**

   - Uses a **public key** to encrypt
   - And a **private key** to decrypt
   - More secure for key sharing

**Plain-text example:**

```
Symmetric:       🔑 Encrypt  -->  🔐 Message  --> 🔑 Decrypt
                 (same key)                     (same key)

Asymmetric:      🔓 Public Key --> 🔐 Message --> 🔑 Private Key
```

---

### ✅ Integrity

**Integrity** means **data hasn’t been changed** by unauthorized sources.

It's about **trusting the data** you receive or store.

One common way to ensure integrity is using **hashing algorithms** (like SHA-256):

1. A **hash** is generated from the original data.
2. Later, the data is checked again—if the **hash has changed**, the data has been tampered with.

---

### 🔁 CI/CD (Continuous Integration / Continuous Delivery)

You’ve probably heard about **CI/CD pipelines**. But what do they mean for security?

Let’s break it down:

- **CI = Continuous Integration**
  Regularly build, test, and merge new code.

- **CD = Continuous Delivery / Deployment**

  - **Delivery** = Automatically release to staging or testing
  - **Deployment** = Automatically deploy to production

---

### 🔐 Security in CI/CD Pipelines

Security must be **integrated throughout** the development pipeline—not just at the end.

Here’s how:

1. **During CI**

   - Scan source code for vulnerabilities early
   - Use static analysis tools to catch issues

2. **During CD**

   - Add automated security tests
   - Ensure nothing vulnerable gets deployed

3. **After Deployment**

   - Use runtime security tools
   - Monitor production for threats

**Plain-text visual:**

```
[Code Commit]
     ↓
[CI Stage: Build & Test]
     ↓   <-- Source Code Scanning
[CD Stage: Release]
     ↓   <-- Security Tests
[Deploy to Production]
     ↓   <-- Runtime Threat Detection
```

---

### 🧠 Recap

Let’s summarize what you’ve learned:

- ✅ **Authentication** checks identity.
- ✅ **Authorization** checks permissions.
- ✅ **Symmetric encryption** uses the same key to encrypt/decrypt.
- ✅ **Asymmetric encryption** uses different keys.
- ✅ **Integrity** ensures data hasn't been altered.
- ✅ **CI/CD** can and should include automated security checks.

---
