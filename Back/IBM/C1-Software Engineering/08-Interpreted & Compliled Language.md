# Interpreted and Compiled Programming Languages

After reviewing this topic, you'll be able to:

- Identify **interpreted programming languages**
- Identify **compiled programming languages**

---

## 🧠 What Are Programming Languages?

Programming languages help us tell computers what to do. Since machines understand **binary (1s and 0s)**, we use **human-readable programming languages** to communicate with them.

There are two broad categories of programming languages:

```
+------------------------+------------------------+
| Interpreted Languages | Compiled Languages      |
+------------------------+------------------------+
| Python                 | C, C++, C#             |
| JavaScript             | Java                   |
| HTML                   |                        |
| Lua                    |                        |
+------------------------+------------------------+
```

---

## ⚙️ Interpreted Languages

Also called **scripting languages**, interpreted languages require an **interpreter** to execute code.

The **interpreter** reads the human-readable code **line-by-line** and executes it directly.

### 🧭 Key Features

- Easy to test and debug
- More portable (runs across different platforms)
- Slower execution compared to compiled languages

### 🔧 Examples of Interpreted Languages

```
+------------+----------------------------------------------+
| Language   | Usage                                        |
+------------+----------------------------------------------+
| JavaScript | Browser interactivity                        |
| Python     | General-purpose, popular in data science     |
| Lua        | Lightweight scripting, popular in games      |
| HTML       | Web page structure and formatting            |
+------------+----------------------------------------------+
```

### 🔁 Interpretation Flow

```plaintext
Human-readable Code
        ↓
   Interpreter
        ↓
   Machine Code Execution
```

---

## 🖥️ Compiled Languages

Compiled languages are used for building full applications and operating systems. The source code is **converted to machine code once**, producing a **single executable file**.

### 🧭 Key Features

- Faster execution speed
- Requires compilation before execution
- Better optimization for large applications

### 🔧 Examples of Compiled Languages

```
+--------+---------------------------------------------+
| C/C++  | System programming (Windows, macOS, Linux)  |
| C#     | Microsoft ecosystem, desktop & web apps     |
| Java   | Android development, cross-platform backend |
+--------+---------------------------------------------+
```

### 📦 Compilation Flow

```plaintext
Human-readable Code
        ↓
      Compiler
        ↓
  Executable Machine Code
        ↓
      Run Program
```

---

## 🖱️ Real-World Analogy

Imagine you're cooking:

- **Interpreted** = Following the recipe step-by-step as you read it
- **Compiled** = Preparing a ready-to-eat meal in advance and just serving it

---

## 🧠 Summary

| Feature     | Interpreted              | Compiled              |
| ----------- | ------------------------ | --------------------- |
| Execution   | Line-by-line             | All at once           |
| Speed       | Slower                   | Faster                |
| Portability | High                     | Depends on platform   |
| Examples    | JavaScript, Python, HTML | C, C++, Java          |
| Use Case    | Web, small scripts       | Full applications, OS |

---
