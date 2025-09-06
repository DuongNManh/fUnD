# 👨 Father vs 👦 Son in OOP

## 🧠 Real-Life Thinking

* In real life:

  * A **father** is *bigger*, more powerful, more complete.
  * A **son** is a *smaller* version, inherits from the father but has less experience, fewer responsibilities.

So we might think:
👉 *If the father is bigger, then a father object should hold more than a son object.*

---

## 💻 OOP Thinking (Memory + Inheritance)

* In OOP:

  * A **base class (Father)** defines some fields/methods.
  * A **derived class (Son)** *extends* that with **extra fields/methods**.
  * That means:

    * A `Son` object **contains everything a Father has** + **extra stuff**.
    * In memory → **Son is bigger than Father**.

### Example

```csharp
class Father {
    int age;           // Father has 1 field
    public void Work() { }
}

class Son : Father {
    string hobby;      // Son adds 1 more field
    public void Play() { }
}
```

📦 Memory layout (simplified):

```plaintext
Father object in memory:         Son object in memory:

┌──────────────┐                 ┌──────────────┐
│ age          │                 │ age          │  (inherited from Father)
│ Work()       │                 │ Work()       │  (inherited from Father)
└──────────────┘                 │--------------│
                                 │ hobby        │  (new field in Son)
                                 │ Play()       │  (new method in Son)
                                 └──────────────┘
```

---

## ⚠️ The Ambiguity in Method Calls

### Case 1: Parent reference → Child object

```csharp
Father f = new Son();
f.Work();   // ✅ Works (Father method)
f.Play();   // ❌ ERROR (Father doesn’t know Play())
```

* Even though the **object in memory is bigger (Son)**,
* The **reference type (Father)** limits what you can see.
* The compiler only allows what’s in `Father`.

👉 To use Son’s methods:

```csharp
((Son)f).Play();
```

---

### Case 2: Child reference → Parent object

```csharp
Son s = (Son)new Father(); // ❌ Runtime error
```

* You’re trying to treat a **smaller object (Father)** as if it were a **bigger one (Son)**.
* Memory doesn’t have space for `hobby` or `Play()`.
* So at runtime → `InvalidCastException`.

---

## 🧩 Real-Life vs OOP Analogy

| Perspective     | Real Life                       | OOP Memory Model                    |
| --------------- | ------------------------------- | ----------------------------------- |
| Parent vs Child | Parent is **bigger**            | Child object is **bigger**          |
| Contains what   | Child inherits traits of parent | Child contains all parent + extra   |
| Error source    | Child < Parent                  | Casting incorrectly = runtime error |

---

✅ **Key Insight**:
In OOP, the **child class is always a superset** of the parent class. That’s why **upcasting (Son → Father)** is safe, but **downcasting (Father → Son)** can fail.