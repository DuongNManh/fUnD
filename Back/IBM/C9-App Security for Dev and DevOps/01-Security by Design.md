# 🔐 Security by Design – Learning Notes

Building secure software is **not something we bolt on at the end** — it must be **designed in from the start**. This approach is called **Security by Design**.

---

## 🚀 Why Security by Design?

- Security is often treated as an **afterthought**, leading to shutdowns, breaches, and rework.
- Involving the **security team early and continuously** reduces risks.
- Security should be integrated into **DevOps pipelines** to create a smooth, automated, and secure delivery process.

> ❗ **Security is cheaper and more effective when built-in, not patched-on.**

---

## 🔄 SDLC – Software Development Lifecycle

A structured sequence of phases to develop tested, high-quality software:

```txt
Requirements → Design → Develop → Test → Deploy
```

| Phase        | Goal                                    |
| ------------ | --------------------------------------- |
| Requirements | Understand what the customer wants      |
| Design       | Plan how the solution will work         |
| Develop      | Implement the solution in code          |
| Test         | Validate that code meets expectations   |
| Deploy       | Release into the production environment |

---

## 🔐 Secure SDLC – Adding Security to Every Phase

Secure SDLC = **SDLC + Security Activities**

| SDLC Phase   | Security Activity                                   |
| ------------ | --------------------------------------------------- |
| Requirements | Risk assessment, define security requirements       |
| Design       | Threat modeling, secure architecture review         |
| Develop      | Static code analysis, secure coding practices       |
| Test         | Vulnerability scans, risk-based security testing    |
| Deploy       | Security configuration, production security testing |

```txt
+--------------+     +-------------------+    +------------------------+
| SDLC Phase   | --> | Security Task     | -->| Outcome                |
+--------------+     +-------------------+    +------------------------+
| Requirements |     | Risk Profiling    |    | Secure Needs Defined   |
| Design       |     | Threat Model      |    | Secure Architecture    |
| Develop      |     | Static Analysis   |    | Secure Code            |
| Test         |     | VAPT scanning     |    | Fewer Vulnerabilities  |
| Deploy       |     | Config & Rollback |    | Safe Release           |
+--------------+     +-------------------+    +------------------------+
```

---

## 🔁 Mapping Secure SDLC into DevOps

DevOps brings together **development**, **operations**, and now **security (DevSecOps)** to create automated & secure CI/CD pipelines.

### ✏️ Requirements Phase (Plan)

- Perform **risk assessment**
- Define **security requirements**
- Profile potential **attackers**

### 🧩 Design Phase

- Perform **secure design & threat modeling**
- Ask: _What can go wrong? How do we protect against it?_

### ⚙ Develop Phase

- Run **static analysis tools**
- Integrate **security tasks into sprints (Secure Scrum)**
- Automate validation of secure input/output

### 🧪 Test Phase

- Add **vulnerability scanners**
- Simulate attacks ("**strive for failure**")
- **Parallelize testing** (run security tests alongside unit & functional tests)

### 🚀 Deploy Phase

- Secure **CI/CD pipeline**
- Support **automated rollback**
- Run **production security tests** (e.g., penetration testing)

```txt
       DevOps Pipeline
+---------+  +---------+  +------+  +--------+  +--------+
| Plan    |→ | Code    |→ | Build|→ | Test   |→ | Deploy |
+---------+  +---------+  +------+  +--------+  +--------+
   ▲           ▲           ▲         ▲           ▲
   │ (Risk     │ (Static   │ (Harden │ (Scan     │ (Prod
   │ Assessment│ Analysis) │ Build)  │ Code)     │ Tests)
```

---

## 🧠 Key Takeaways

- **Secure SDLC = SDLC + Security woven into every phase**
- Adding security early saves time, improves quality, and reduces risk.
- **Security + DevOps = DevSecOps** → security automation in CI/CD.
- Always consider **how attackers might break your system** before deploying it.

---

## 📌 Helpful Mnemonic: **“Shift Security Left”**

Bring security _from the right (deploy phase)_ toward the _left (requirements)_ to catch issues earlier.

---
