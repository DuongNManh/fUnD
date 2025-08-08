# Static Analysis

## 🎯 Learning Objectives

After studying this, you will be able to:

- Describe **static analysis**.
- Explain the **benefits** of using static analysis.

---

## 1. What is Static Analysis?

Static analysis = **debugging method** that automatically inspects **source code or binaries before execution**.

- Detects **common vulnerabilities** early.
- Also known as **Static Application Security Testing (SAST)**.
- Works **without running** the code.
- Some SAST tools:

  - Provide **APIs** for DevOps integration.
  - Work **before code is complete**.

---

## 2. Static Analysis in the SDLC

```
+--------+--------+------------+--------+---------+-----------+
| Plan   | Design | Develop    | Test   | Deploy  | Maintain  |
+--------+--------+------------+--------+---------+-----------+
                     ↑
     Static Analysis happens here
  (before testing begins — early feedback loop)
```

**For DevOps:**

- Occurs during the **Develop** stage.
- Creates an **automatic feedback loop** so developers fix issues **immediately**.

---

## 3. How Static Analysis Works

- Tools examine **code on the file system** without execution.
- Covers more paths than manual testing could.
- Pinpoints **exact problem locations**.
- Can be **integrated into CI/CD pipelines**.

---

## 4. Key Benefits of Static Analysis

### 📌 Benefits Layer Diagram

```
[ Depth ] → Scans most possible execution paths.
[ Speed ] → Faster than manual review, cheaper fixes early.
[ Accuracy ] → High precision with up-to-date vulnerability knowledge.
```

**Details:**

1. **Depth**

   - Goes beyond manual testing coverage.
   - In-depth checks based on predefined criteria.

2. **Speed**

   - Early detection → faster fixes.
   - Lower cost for fixing early-stage bugs.

3. **Accuracy**

   - Automated scanning leverages wide vulnerability databases.
   - Examines **every line of code**.

---

## 5. Practical Value

```
Write Code → Static Analysis → Early Fix → Testing → Deployment
```

- **Early fixes** = reduced rework and cost.
- Ensures **quality code** before functional testing.

---

## 6. Key Takeaways

```
[ Static Analysis ] → Debugging without execution.
[ SAST ]            → Starts early in SDLC (Develop stage).
[ Tools ]           → File system scan, CI/CD integration.
[ Benefits ]        → Depth, Speed, Accuracy.
```

- **Proactive** security measure.
- Complements manual code review.
- Strengthens **code quality** before production.

---
