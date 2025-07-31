# 📘 Phases of the Software Development Life Cycle (SDLC)

After this lesson, you will be able to:

- Name the phases involved in the SDLC
- Describe each phase
- Identify common tasks associated with each phase

---

## 🔁 Overview of the SDLC Phases

There are generally **six phases** in the Software Development Life Cycle:

1. **Planning**
2. **Design**
3. **Development**
4. **Testing**
5. **Deployment**
6. **Maintenance**

Each phase is **discrete**, meaning tasks in one phase should be completed before the next begins (in traditional waterfall methods).

> Note: Organizations may rename or restructure phases depending on their practices. For example:
>
> - “Planning” may also be called “Requirements” or “Analysis”
> - Some workflows may add or omit stages
> - Iterative or agile methods may blend phases or loop back to earlier ones

---

## 📊 SDLC Phase Diagram

```plaintext
+-----------+     +--------+     +-------------+     +---------+     +------------+     +-------------+
| Planning  | --> | Design | --> | Development | --> | Testing | --> | Deployment | --> | Maintenance |
+-----------+     +--------+     +-------------+     +---------+     +------------+     +-------------+
     |                                                                                        |
     +----------------------------------------------------------------------------------------+
                        Iteration: Feed improvements and fixes back into the cycle
```

---

## 📝 Phase Descriptions

### 1. 🧠 Planning

**Goal**: Gather, analyze, and document business requirements.

Key tasks:

- Identify users and business needs
- Define inputs/outputs and regulatory requirements
- Estimate cost, time, resources
- Allocate team roles
- Create a **Software Requirements Specification (SRS)** document

🧪 _Prototyping_: Optional small-scale mockups may be created to refine requirements early.

---

### 2. 🧱 Design

**Goal**: Translate requirements into technical architecture.

Key tasks:

- Define system architecture
- Collaborate with stakeholders
- Create **design documents**
- May include additional **prototypes**

---

### 3. 💻 Development

**Goal**: Convert design into working code.

Key tasks:

- Assign programming tasks
- Use appropriate programming languages, frameworks, and tools
- Follow coding standards or guidelines

---

### 4. 🧪 Testing

**Goal**: Ensure the software is stable, secure, and meets requirements.

Testing types:

- **Unit testing**: individual components
- **Integration testing**: combined modules
- **System testing**: complete system
- **Acceptance testing (UAT)**: validation with users

Testing may be **manual**, **automated**, or a hybrid.

---

### 5. 🚀 Deployment

**Goal**: Release the software to production environments.

Release methods:

- Staged deployment (UAT → Production)
- App stores (for mobile apps)
- Internal distribution servers

---

### 6. 🔧 Maintenance

**Goal**: Support, fix, and improve the software after release.

Key tasks:

- Identify bugs missed during testing
- Collect feedback from users
- Plan for future enhancements or fixes
- Start a new cycle if major changes are needed

---

## ✅ Summary

| Phase       | Key Output               | Purpose                              |
| ----------- | ------------------------ | ------------------------------------ |
| Planning    | SRS Document             | Define what to build                 |
| Design      | Design Document          | Define how to build it               |
| Development | Source Code              | Implement features                   |
| Testing     | Test Reports             | Validate functionality and stability |
| Deployment  | Deployed Application     | Make it available to users           |
| Maintenance | Feedback, Patch Releases | Support and improve post-release     |

---
