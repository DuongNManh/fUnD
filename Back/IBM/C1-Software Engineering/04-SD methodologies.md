# 📘 Software Development Methodologies

In this document, you will:

- Understand several common software development methodologies.
- Learn about **Waterfall**, **V-Model**, and **Agile**.
- Compare the pros and cons of each method.

---

## 💡 Why Methodologies Matter

Software development methodologies provide structured approaches to:

- Clarify team communication.
- Define when and how information is shared.
- Guide software projects through predictable processes.

---

## 🧱 1. Waterfall Method

A **sequential** software development approach. Each phase must be completed before moving to the next.

```plaintext
 Requirements --> Design --> Implementation --> Testing --> Deployment --> Maintenance
```

### 🔍 Key Features:

- Each phase has a **fixed start and end**.
- **Customer** sees the product **only at the end**.
- Often used in **major releases** with long cycles.

### ✅ Pros:

- Easy to understand and follow.
- Good for **fixed-scope** projects.
- Budget and resource planning is straightforward.

### ❌ Cons:

- Inflexible to changes.
- Late feedback (at testing stage).
- Risk of misalignment with customer expectations.

---

## ✅ 2. V-Shape Model

An extension of the Waterfall method that emphasizes **testing** at every development stage.

```plaintext
       Verification             Validation
     ----------------         ----------------
    |  Planning        |     |  Acceptance Test  |
    |  System Design   |     |  System Testing   |
    |  Architecture    | --> |  Integration Test |
    |  Module Design   |     |  Unit Testing     |
     ----------------         ----------------
             \               /
             Coding Phase (Bottom of the V)
```

### 🔍 Key Features:

- Every **verification phase** has a **corresponding validation/test phase**.
- **Testing is planned early**, reducing bugs and rework.

### ✅ Pros:

- Clear mapping between design and testing.
- Easy to implement.
- Saves testing time later in the project.

### ❌ Cons:

- Even **less flexible** than Waterfall.
- Difficult to adapt to changing requirements.

---

## 🔁 3. Agile Methodology

An **iterative** approach focusing on short, collaborative development cycles called **sprints**.

```plaintext
Plan -> Design -> Build -> Test -> Review -> Repeat
            (per Sprint: 1-4 weeks)
```

### 🔍 Key Features:

- Cycles called **sprints** (1–4 weeks).
- In each sprint, teams release working code.
- Final stage: **Sprint Demo + Feedback**.
- After several sprints, a **Minimum Viable Product (MVP)** is delivered.

### 🧭 Agile Manifesto Values:

```plaintext
Individuals and interactions   >   Processes and tools
Working software               >   Comprehensive documentation
Customer collaboration         >   Contract negotiation
Responding to change           >   Following a plan
```

### ✅ Pros:

- Flexible to changing requirements.
- Continuous feedback from stakeholders.
- Supports modular and incremental development.
- Stakeholders always see progress (working code).

### ❌ Cons:

- Budgeting and scheduling can be **uncertain**.
- Requires **strong team collaboration** and communication.
- Scope may **shift frequently**.

---

## 📊 Comparison Table

| Feature                 | Waterfall            | V-Shape Model           | Agile                     |
| ----------------------- | -------------------- | ----------------------- | ------------------------- |
| Approach                | Sequential           | Sequential + Testing    | Iterative/Cyclic          |
| Flexibility             | Low                  | Very Low                | High                      |
| Planning                | Heavy upfront        | Heavy upfront + testing | Per sprint (lightweight)  |
| Feedback Timing         | Late (after testing) | Mid to Late             | Continuous (every sprint) |
| Stakeholder Involvement | Low                  | Low                     | High                      |
| Adaptability to Change  | Difficult            | Very difficult          | Easy                      |

---

## 🧠 Summary

- **Waterfall** and **V-Model** are **sequential** and easy to follow, but rigid.
- **Agile** is **iterative**, flexible, and better suited for modern software development.
- Agile supports **changing requirements**, but planning and scope can be fluid.

---
