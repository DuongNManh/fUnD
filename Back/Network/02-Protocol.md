## 📦 Protocols

Protocols are **rules for packaging, sending, and receiving data** over a network.

They ensure **communication compatibility** between client and server, even if they run on **different platforms**.

### 🔁 TCP (Transmission Control Protocol)

- **Connection-based**: a reliable, continuous stream of data between two endpoints.
- **Acknowledgment mechanism**: confirms delivery of each packet.
- **Single path** (logical connection).
- Ensures **ordered, error-checked** delivery.
- Used by: **HTTP, HTTPS, FTP, SSH**

```txt
[Client] ========================= [Server]
           Reliable Line (TCP)
         Acknowledgment for each packet
```

✅ Reliable | 🐌 Slightly slower | 📦 Ordered delivery

---

### 📤 UDP (User Datagram Protocol)

- **Connectionless**: sends independent packets (called **datagrams**).
- **No acknowledgment** or delivery guarantee.
- Multiple paths may be used.
- Lightweight and faster, but **unreliable**.
- Often blocked by firewalls or routers.
- Used by: **Video streaming, DNS, VoIP, Online gaming**

```txt
[Client] --> [Server]
[Client] --> [Server]
[Client] --> [Server]
       Many parallel, stateless messages (UDP)
```

⚡ Fast | ❌ No delivery guarantee | 🔁 Out-of-order possible

---

## 🧠 Comparison Table

| Feature           | TCP                       | UDP                          |
| ----------------- | ------------------------- | ---------------------------- |
| Connection Type   | Connection-oriented       | Connectionless               |
| Reliability       | Reliable (uses ACKs)      | Unreliable (no ACKs)         |
| Delivery Order    | Guaranteed                | Not guaranteed               |
| Speed             | Slower                    | Faster                       |
| Use Cases         | Web, Email, File Transfer | Streaming, DNS, Online Games |
| Firewall Friendly | Usually allowed           | May be blocked by firewalls  |

---

## 🛡️ Important Note

> Many **firewalls and routers block UDP** to prevent abuse or untrusted traffic.
> ✅ Always **check with your system administrator** if your application requires UDP!

---
