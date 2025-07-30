# 📘 Twelve-Factor App Methodology

## 🎯 Learning Objectives

By the end of this module, you will be able to:

- Describe the characteristics of modern software development
- State the goal of twelve-factor apps
- Identify the twelve factors and explain how they map to three phases of the software delivery lifecycle: **Code**, **Deploy**, and **Operate**

---

## 🧩 Overview

Modern software development often delivers software as a service (SaaS). These applications are:

- Centrally hosted
- Accessed via the internet
- Examples: Booking reservations, filing taxes online

> 🔹 **Note:** Microservices are not required but often complement twelve-factor apps.

---

## 🧱 Code Phase

### **Factor 1: Codebase**

- Use version control (e.g., **Git**).
- Maintain **one codebase per app**, even if there are **multiple deployments**.

✅ **Example:**
Same codebase deployed to both `dev`, `test`, and `production`, with different versions active.

---

### **Factor 2: Dependencies**

- Declare all dependencies **explicitly**.
- Avoid relying on packages/tools **implicitly installed**.

✅ **Example:**
When a new developer clones the project, they can install all dependencies without manual setup.

---

### **Factor 10: Dev/Prod Parity**

- Minimize differences between environments (dev, test, prod).
- Ensures consistent behavior across environments.

✅ **Example:**
If using **MySQL 8.0 in production**, use **the same version** in development.

---

## 🚀 Deploy Phase

### **Factor 3: Config**

- Configurations vary by environment (e.g., database URLs, credentials).
- Store them in **environment variables**, **not constants** in code.

✅ **Example:**
Use environment variables to connect to different databases for `staging` and `production`.

---

### **Factor 4: Backing Services**

- Treat local and 3rd-party services the same.
- Access all backing services via a **URL** and credentials.

✅ **Example:**
If your database goes down, you can replace it with another without changing the app code.

---

### **Factor 5: Build, Release, Run**

- **Build**: Compile and package code.
- **Release**: Combine build with config.
- **Run**: Launch the app.

🚫 Do **not** change the code at runtime — changes must go through **build**.

✅ **Example:**
A change in config should trigger a new **release**, not direct code alteration at runtime.

---

### **Factor 6: Processes**

- App runs as **one or more stateless processes**.
- Persistent data must be in a **backend service** (e.g., database).

✅ **Example:**
If Process A handled the first request, and Process B handles the next, no state should be shared in memory between them.

---

### **Factor 7: Port Binding**

- App must **export HTTP via port binding**.
- Include web server as a **declared dependency**.

✅ **Example:**
Bind app to port 8080 via Express (Node.js) or Kestrel (.NET), allowing URL-based access.

---

## ⚙️ Operate Phase

### **Factor 8: Concurrency**

- Scale apps horizontally by starting **multiple stateless processes**.
- No interdependency between processes.

✅ **Example:**
To handle more load, spin up more app instances without breaking functionality.

---

### **Factor 9: Disposability**

- Processes should:

  - **Start fast**
  - **Shut down gracefully**

✅ **Example:**
This enables fast deploys and makes autoscaling easier on platforms like Kubernetes.

---

### **Factor 11: Logs**

- Treat logs as **event streams**.
- Write logs to **standard output**.

✅ **Example:**
Use tools like Fluentd or ELK Stack to capture and analyze logs from stdout.

---

### **Factor 12: Admin Processes**

- Run admin/management tasks (e.g., **migrations**) as **one-off processes**.
- Use the same **codebase and config** as the main app.

✅ **Example:**
Run `python manage.py migrate` or `dotnet ef database update` using the production config and release.

---

## ✅ Summary

- Modern software emphasizes **SaaS** and centralized hosting.
- **Twelve-Factor App Methodology** makes SaaS apps more **scalable**, **portable**, and **maintainable**.
- The factors map to:

  - **Code**: Codebase, Dependencies, Dev/Prod Parity
  - **Deploy**: Config, Backing Services, Build/Release/Run, Processes, Port Binding
  - **Operate**: Concurrency, Disposability, Logs, Admin Processes
