# Dynamic Analysis

## 🎯 Learning Objectives

After studying this, you will be able to:

- Describe **dynamic analysis**.
- Explain the **benefits** of using dynamic analysis.

---

## 1. What is Dynamic Analysis?

Dynamic analysis = **testing and evaluating an application while it is executing**.

- Usually performed on **fully built applications**.
- Common environments:

  - **Staging**
  - **Pre-production**
  - **Production**

- No need to create artificial test cases → runs in **real-time scenarios**.
- Detects **vulnerabilities**, **memory issues**, and **runtime crashes**.

---

## 2. DAST (Dynamic Application Security Testing)

- **Evaluates applications from the outside-in** (via the front end).
- **Acts like an attacker**:

  - Simulates real-world attacks.
  - Detects potential threats & vulnerabilities.

- **Black-box testing**:

  - No access to source code.
  - Tests behavior via inputs & outputs.

---

## 3. Dynamic Analysis in the SDLC

```
+--------+--------+------------+--------+---------+-----------+
| Plan   | Design | Develop    | Test   | Deploy  | Maintain  |
+--------+--------+------------+--------+---------+-----------+
                                    ↑
         Dynamic Analysis mainly here (Test/Pre-prod/Production)
```

- Complements **static analysis**.
- Targets **running applications**, not source code.

---

## 4. How Dynamic Analysis Works

- **Crawls** the application interface from the root URL.
- Attempts to **break into** the system.
- Tests behavior with **real or simulated inputs**:

  - URL requests.
  - Form submissions.

- Uses **dummy databases** during testing to avoid harming real data.
- Monitors **outputs and behavior** to identify:

  - Security holes.
  - Faults in dynamic code paths.
  - Unintended behaviors.

---

## 5. Key Benefits of Dynamic Analysis

### 📌 Benefits Diagram

```
[ Crawl Interface ] → Map attack surfaces, find breakpoints.
[ Behavioral Insights ] → See how app reacts to various inputs.
[ Fault Detection ] → Identify runtime issues missed by static tests.
```

**Details:**

1. **Crawl Interface**

   - Scans app from root URL.
   - Finds vulnerabilities in exposed interfaces.

2. **Behavioral Insights**

   - Observes reactions to inputs (URLs, forms).
   - Reveals crashes, errors, or unexpected behavior.

3. **Fault Detection**

   - Locates issues in **dynamic code paths**.
   - Provides accurate results from real execution.

---

## 6. Practical Value

```
Deploy App → Crawl & Attack Simulation → Analyze Behavior → Patch Vulnerabilities
```

- **Realistic testing** of production-like conditions.
- Ensures application can handle **live threats**.

---

## 7. Key Takeaways

```
[ Dynamic Analysis ] → Tests app during execution.
[ DAST ]              → Black-box, attacker-simulation approach.
[ Benefits ]          → Crawl interfaces, behavioral insights, runtime fault detection.
```

- Ideal for detecting **runtime vulnerabilities**.
- Complements **static analysis** for full security coverage.
- Provides **accurate, real-world** risk assessment.

---
