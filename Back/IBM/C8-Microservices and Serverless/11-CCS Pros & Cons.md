# Serverless Computing: Pros and Cons

## Learning Objectives

After reviewing this document, you will be able to:

- Describe the benefits of serverless computing
- Describe the constraints of serverless computing
- Compare serverless with containers and traditional computing

---

## 🚧 Traditional Computing Challenges

In traditional computing, development and operations teams are responsible for setting up and maintaining infrastructure. This introduces several challenges:

- Time-consuming setup
- Complexity of infrastructure management
- High capital investments

---

## ✅ Serverless Benefits

Serverless computing enables developers to focus purely on code, with infrastructure management handled by the cloud provider.

### Key Benefits

- **No Infrastructure Management:** Cloud providers handle the infrastructure, reducing operational overhead.
- **Cost Efficiency:** Pay-per-request model; no charges for idle resources.
- **High Availability & Fault Tolerance:** Handled by the provider.
- **Faster Execution:**

  - Serverless: milliseconds
  - Containers: seconds
  - VMs: minutes

- **IDE Support:** Some providers offer built-in IDEs.
- **Flexible Language Support:** Most common languages are supported.
- **Third-party Integration:** Easy integration with authentication, databases, etc.
- **Greener Computing:** Efficient resource usage due to on-demand execution.

### Example

> A frontend must run continuously, but an **authentication function** can be serverless and run only when a user logs in — saving cost and compute.

---

## ❌ Serverless Constraints

Despite its advantages, serverless is not ideal for all use cases:

- **Cold Starts:** Initial startup latency when functions aren't warm
- **Vendor Lock-in:** Heavy reliance on cloud-specific services
- **Limited Use Cases:** Not suitable for long-running jobs
- **Latency-Sensitive Apps:** Not ideal for real-time apps like banking or healthcare
- **Debugging Challenges:** Harder to simulate and troubleshoot distributed functions locally
- **Limited State Management:** No persistent state between function invocations
- **Security Complexity:** Broader attack surface from code to endpoints
- **Limited Language Support:** Depends on the cloud provider

### Tip

> Use external caching like Redis or Memcached to overcome the lack of persistent local state.

---

## 🔄 Serverless + Containers

These are **not mutually exclusive** — they work better together in a hybrid model.

> 💡 _“Build serverless first. If needed, move to containers.”_

---

## 📊 Comparison Tables

### Serverless vs Containers

| Aspect            | Serverless                   | Containers                    |
| ----------------- | ---------------------------- | ----------------------------- |
| Cost              | Pay-per-request              | Depends on uptime & resources |
| Deployment Speed  | Milliseconds                 | Seconds                       |
| Scalability       | Automatic (by provider)      | Manual or semi-automatic      |
| Language Support  | Limited (provider-dependent) | Any language                  |
| Latency           | Cold start latency possible  | Very low                      |
| Long-running Jobs | Not suitable                 | Ideal                         |
| Debugging         | Difficult (no local BaaS)    | Easier                        |
| Portability       | Low (vendor lock-in)         | High (OS/language agnostic)   |

### Serverless vs Traditional

| Aspect           | Serverless                    | Traditional Computing      |
| ---------------- | ----------------------------- | -------------------------- |
| Cost             | Pay-per-request               | High CAPEX + OPEX          |
| Scalability      | Auto-scaled by cloud provider | Manual                     |
| Setup Complexity | Minimal                       | Complex                    |
| Speed to Market  | Faster development            | Slower due to infra burden |
| Vendor Lock-in   | High                          | Low                        |
| Security         | Cloud provider dependent      | Full control within org    |
| Network Access   | Requires API setup            | IP-based access            |

---

## 🧠 Summary

- Traditional computing involves infrastructure management; serverless abstracts this away.
- Serverless is cost-effective, fast, and scalable — ideal for on-demand workloads.
- Serverless has limitations like cold start, vendor lock-in, and limited control.
- Containers and serverless can be used together for flexibility.
- Choose based on your application’s nature: real-time, long-running, or burst-based.

---

## 📌 Visual Comparison (Markdown Figure)

```plaintext
                     ┌──────────────────────┐
                     │   Traditional App    │
                     └─────────┬────────────┘
                               │ Setup & Ops
                               ▼
                ┌──────────────────────────────┐
                │ Virtual Machines / Bare Metal│
                └──────────────────────────────┘


                     ┌──────────────────────┐
                     │   Containerized App  │
                     └─────────┬────────────┘
                               │ Docker Build/Run
                               ▼
                ┌──────────────────────────────┐
                │      Kubernetes / ECS        │
                └──────────────────────────────┘


                     ┌──────────────────────┐
                     │  Serverless Function │
                     └─────────┬────────────┘
                               │ Triggered on Demand
                               ▼
                ┌──────────────────────────────┐
                │   Cloud Provider (FaaS)      │
                └──────────────────────────────┘
```

---

> 📚 _Recommended path: Start with serverless. For longer tasks or better control, combine with containers._
