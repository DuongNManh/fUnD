# 🎨 Design Patterns in OOP

## 🔑 Why Design Patterns Matter

As software development has evolved, developers look for ways to build programs that are **efficient, maintainable, and scalable**.
The **common solutions** that address recurring problems are called **design patterns**.

✅ Design patterns are **reusable templates** that:

* Provide **standardized solutions** to common challenges.
* Improve **readability** and **maintainability**.
* Make applications more **efficient** and **scalable**.

---

## 🏗️ Categories of Design Patterns

### 1. 🧪 Creational Patterns

*Focus on how objects are created in a system.*

* Ensure objects are **created appropriately** for their use case.
* Avoid problems with **global variables** and **uncontrolled instantiation**.

**Example: Singleton Pattern**

* Restricts a class to **one instance**.
* Provides a **single access point** to it.
* Commonly used for:

  * Configuration managers
  * Database connections

```cpp
Class Singleton
-------------------------
- instance (private static)
-------------------------
+ GetInstance() → Singleton
```

---

### 2. 🏗️ Structural Patterns

*Define how classes and objects are **composed** to form larger structures.*

* Organize relationships to **minimize impact** of change.
* Focus on **composition** rather than inheritance.

**Example: Adapter Pattern**

* Bridges incompatible interfaces so objects can work together.

```cpp
RoundHole expects: GetRadius()
SquarePeg provides: GetWidth()

Adapter → translates width into radius
```

---

### 3. 🤝 Behavioral Patterns

*Define how classes and objects **interact and communicate**.*

* Set **protocols** for collaboration.
* Clarify **responsibilities** between components.
* Ensure efficiency as the system **scales or changes**.

---

## 🛠️ Tools for Enforcing Patterns

Modern IDEs (like **Visual Studio Code**) help developers stick to best practices by:

* Suggesting **refactorings** into common patterns.
* Detecting **improper use** of patterns.
* Alerting developers to **inconsistencies**.

---

## ✅ Key Takeaways

* **Design patterns** = reusable solutions to recurring software challenges.
* They fall into **3 main categories**:

  1. **Creational** → object creation
  2. **Structural** → class & object composition
  3. **Behavioral** → interaction & communication
* Patterns make code **cleaner, more consistent, and easier to maintain**.

---
