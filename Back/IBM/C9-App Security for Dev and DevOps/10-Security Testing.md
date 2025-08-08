# Introduction to Security Testing and Mitigation Strategies

## 🎯 Learning Objectives

After studying this, you will be able to:

- Describe **security testing**.
- Describe **mitigation strategies**.
- List **five key mitigation strategies**.

---

## 1. Understanding Security Testing

Security testing = **procedures for comparing the states of an application or a system**.

**Purpose:**

- Provide a **secure baseline** for development.
- Identify vulnerabilities early.
- Prevent regressions in security after code changes.

**When to do it?**

- On **all new code**.
- Whenever **code changes** occur.

---

## 2. Security Testing in the SDLC

Security testing happens mainly in the **Test** phase, but should be integrated across the **entire lifecycle**.

```
+--------+--------+------------+--------+---------+-----------+
| Plan   | Design | Develop    | Test   | Deploy  | Maintain  |
+--------+--------+------------+--------+---------+-----------+
                           ↑
             Security Testing is critical here
         (but should be integrated throughout all stages)
```

---

## 3. Secure Baseline & Functional Security Testing

1. **Establish a secure baseline** during development.
2. Use it for comparison during later tests.
3. Include **functional security testing** to ensure the software behaves securely.

**Functional Security Testing:**

- **Ad hoc testing** → Performed when vulnerabilities are found.
- **Exploratory testing** → Testing ideas/hypotheses outside formal plans.

---

## 4. Automated Security Testing

**Approaches:**

- **Unit testing** → Small scope; tests classes/methods to validate API contracts.
- **Integration testing** → Wide scope; tests interaction between components.

**Popular automation frameworks:**

```
+---------------+-------------------------------------------+
| Framework     | Key Feature                               |
+---------------+-------------------------------------------+
| BDD-Security  | Behavior-driven security testing          |
| Mittn         | Continuous integration security testing   |
| Gauntlt       | Hooks into other security tools easily    |
+---------------+-------------------------------------------+
```

---

## 5. Five Key Mitigation Strategies in the SDLC

### 📌 Workflow Diagram

```
[ PLAN ] ---------------------------+
                                     |
[ DESIGN ] --------------------+     |
                               |     |
[ DEVELOP ] --- (1) JSON APIs  |     |
             --- (2) Secure Coding   |
             --- (3) Vulnerability Scanning
                               |     |
[ TEST ] ------ (4) Threat Modeling  |
             ------ (5) OWASP Awareness
                               |     |
[ DEPLOY ] --------------------+     |
                                     |
[ MAINTAIN ] ------------------------+
```

**Legend:**

1. **Use JSON for API payloads** – Simpler, faster parsing than XML.
2. **Secure coding practices** – Share standards, train teams.
3. **Vulnerability scanning** – Manual + automated.
4. **Threat modeling** – Predict, detect, contain attacks.
5. **OWASP Top 10 awareness** – Stay updated with critical risks.

---

## 6. Key Takeaways

```
[ Security Tests ]  → Compare system/application states.
[ Functional Tests ] → Check secure behavior against requirements.
[ Automated Tests ]  → Unit + Integration with security frameworks.
[ Mitigation ]       → JSON, Secure Coding, Scanners, Threat Modeling, OWASP.
```

- Security testing is **continuous**, not a one-time activity.
- Applying mitigation strategies at the **right SDLC stage** helps prevent costly vulnerabilities.
- **Awareness + automation** is key for long-term protection.

---
