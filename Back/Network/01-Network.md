# 🌐 Some Definitions Related to Networking

## 🖥️ Platform

A **platform** consists of:

- **Hardware** (e.g., computer, router)
- **Operating System** (e.g., Windows, Linux)

It supports applications like web servers or browsers.

---

## 🧑‍💻 Client & Server Model

**Client:**  
An application that _requests_ data (e.g., web browser).

**Server:**  
An application that _responds with_ data (e.g., IIS, Kestrel, Nginx).

```txt
+--------+          Request           +--------+
| Client |  ----------------------->  | Server |
| (e.g., |                            |  IIS)  |
| Chrome)|          Response          |        |
+--------+  <-----------------------  +--------+
```

---

## 🌍 IP Address

An **IP address** identifies a network element (e.g., computer, router).

### IPv4

- 4 bytes (32 bits)
- Format: `192.143.5.1`
- Supports \~4.3 billion addresses

### IPv6

- 16 bytes (128 bits)
- Format: `2001:0db8:85a3::8a2e:0370:7334`
- Supports \~3.4×10³⁸ addresses

---

## 🔌 Port

A **port** is a 2-byte (16-bit) number used by the **OS** to distinguish between multiple **network processes** on a single machine.

- Range: `0` to `65535`
- Example:

  - HTTP: port `80`
  - HTTPS: port `443`

```txt
+--------------+       Port: 443       +--------------+
| Client App   |  -------------------> | Server (IIS) |
| (Browser)    | <-------------------  |  Port: 80    |
+--------------+                       +--------------+
```

---

## 🧠 Summary Table

| Concept  | Description                                               |
| -------- | --------------------------------------------------------- |
| Platform | Combination of hardware and OS                            |
| Client   | App that requests data (e.g., browser)                    |
| Server   | App that provides data (e.g., Nginx, Kestrel)             |
| IP       | Identifier for network devices                            |
| IPv4     | 4-byte address (e.g., 192.143.5.1)                        |
| IPv6     | 16-byte address (e.g., 2001\:db8::1)                      |
| Port     | 2-byte number identifying a network communication process |

---

✅ **Use Cases**

- A web browser (client) connects to a website (server) using IP + port.
- The server listens on port `443` (HTTPS), responds with data over IPv6 or IPv4.
