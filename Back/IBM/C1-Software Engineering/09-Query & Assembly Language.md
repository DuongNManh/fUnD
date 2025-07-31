# Query and Assembly Programming Languages

## 🎯 Learning Objectives

After this lesson, you will be able to:

- Compare **high-level** and **low-level** programming languages
- Describe **query languages**
- Describe **assembly languages**

---

## 🧠 High-Level vs Low-Level Programming Languages

Programming languages are grouped into two broad categories:

| Type           | Description                                                       | Examples                            |
| -------------- | ----------------------------------------------------------------- | ----------------------------------- |
| **High-Level** | Closer to human language, easier to write/debug                   | SQL, Python, Pascal                 |
| **Low-Level**  | Closer to machine code, uses symbolic instructions for processors | ARM, MIPS, x86 (Assembly Languages) |

```
+--------------------+                   +--------------------+
| High-Level         |  Abstract         | Low-Level           |
| Programming        | <------------->   | Programming         |
| Languages (e.g.    |  More Human-like  | Languages (e.g.     |
| Python, SQL)       |                   | Assembly, Machine)  |
+--------------------+                   +--------------------+
```

---

## 🔍 Query Languages

A **query** is a request for data from a **database**.

A **query language** (like SQL) allows us to interact with a **DBMS** (Database Management System).

### 💬 CRUD Operations

CRUD refers to:

- **C**reate
- **R**ead
- **U**pdate
- **D**elete

These are fundamental operations on a database.

### ✏️ SQL Statement Types

| Statement Type | Purpose              | Example                           |
| -------------- | -------------------- | --------------------------------- |
| **SELECT**     | Read data            | `SELECT * FROM users;`            |
| **INSERT**     | Add new data         | `INSERT INTO users VALUES (...);` |
| **UPDATE**     | Modify existing data | `UPDATE users SET name='John';`   |
| **DELETE**     | Remove data          | `DELETE FROM users WHERE id=1;`   |

### 🔧 SQL Statement Structure (Plaintext Figure)

```
+-------------+     +------------------------+
| Query Type  | --> | SQL Command Statement  |
+-------------+     +------------------------+

Examples:
  SELECT name FROM customers;
  INSERT INTO orders VALUES (1, 'Book');
  UPDATE products SET price = 9.99 WHERE id = 3;
  DELETE FROM users WHERE is_active = false;
```

---

## 🧾 SQL vs NoSQL

| SQL (Relational)             | NoSQL (Non-relational)                |
| ---------------------------- | ------------------------------------- |
| Structured schema            | Dynamic schema                        |
| Tables with rows and columns | JSON, documents, key-value, or graphs |
| Uses SQL                     | May use other languages like AQL, CQL |

---

## 🖥️ Assembly Languages

Assembly languages are **low-level**, meaning they’re close to machine code. Each instruction maps to **one machine operation**.

- Use **mnemonics** like `LDA`, `STA`, `ADD`, `INP`, `OUT`
- Written **line-by-line**, one instruction per line
- Require an **assembler** to convert to machine code

### ⚙️ Assembly Instruction Format

```asm
[label]   instruction   [operand(s)]   ; optional comment
```

#### Example:

```asm
START    LDA   NUM1     ; Load NUM1 into the accumulator
         ADD   NUM2     ; Add NUM2
         OUT            ; Output the result
         HLT            ; Stop program
NUM1     DAT   10
NUM2     DAT   5
```

### 🔁 Assembly Code Flow (Plaintext Diagram)

```
+-----------+        +-------------+        +----------+
| Load Data | -----> | Perform ADD | -----> | Output   |
+-----------+        +-------------+        +----------+
       |                                         |
       v                                         v
  [ LDA NUM1 ]                            [ OUT / HLT ]
```

---

## 🧩 Summary

| Topic                | Key Takeaway                                                                |
| -------------------- | --------------------------------------------------------------------------- |
| High-level Languages | Easier to write and debug, close to English                                 |
| Low-level Languages  | Closer to hardware, use symbols to represent machine instructions           |
| Query Language (SQL) | Used to communicate with relational databases using CRUD and query commands |
| Assembly Language    | Maps directly to machine instructions; requires an assembler                |

---

## ✅ You’ve Learned:

- The difference between **high-level** and **low-level** programming
- How to use **SQL** for querying and managing databases
- The purpose and syntax of **assembly language**
- How assembly instructions map **1:1** with machine instructions

---
