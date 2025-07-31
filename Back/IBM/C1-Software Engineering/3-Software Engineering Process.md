# 🏗️ Building Quality Software

After this lesson, you will be able to:

- List common software engineering processes
- Describe the key steps required to build high-quality software

---

## 🧩 Overview of Key Software Engineering Processes

There are **six essential processes** commonly involved in building quality software:

1. Requirements Gathering
2. Design
3. Coding for Quality
4. Testing
5. Releases
6. Documenting

Each of these processes contributes to delivering reliable, maintainable, and user-friendly software.

---

## 1. 📋 Requirements Gathering

The **Software Requirements Specification (SRS)** is the foundation of the development process. It documents what the software should do and how it should behave.

### 🔍 What it includes:

- **Use cases**: Business needs and user flows
- **Requirement categories**:

  - **Functional** (what the system does)
  - **External & UI** (how users interact)
  - **System features** (hardware/tech limits)
  - **Non-functional** (performance, security, scalability)

> ✅ _Example_:
> A requirement for a banking app might be: “Users must be able to transfer funds between accounts using a secure authentication system.”

---

## 2. 🧱 Software Design

Design transforms requirements into a structure that developers can implement.

### 🏗️ What it covers:

- **System architecture** and technical component breakdown
- **Component design**: Clear roles and responsibilities
- **Performance, platform, and security considerations**

### ✍️ Design includes:

- Business rules and logic
- API design
- User interface design
- Database structure

> ✅ _Example_:
> An e-commerce system design might include a `ProductService`, `CartService`, and `PaymentGateway`—each handling a specific function with defined API contracts.

---

## 3. 💻 Coding for Quality

High-quality code has characteristics that make it easy to work with and reliable over time.

### 🧪 Attributes of good code:

- **Maintainability**
- **Readability**
- **Testability**
- **Security**

### 🔧 Best practices:

- Use **coding standards** and conventions
- Apply **design patterns**
- Run **linters** to catch syntax/style issues
- Use **clear comments and documentation**

> ✅ _Example_:
> Developers use PEP8 (in Python) or ESLint (in JavaScript) to maintain code style consistency.

---

## 4. 🧪 Testing

Testing ensures that the software meets the requirements and is free of defects.

### 🧬 Levels of Testing:

| Level                     | Description                                          |
| ------------------------- | ---------------------------------------------------- |
| **Unit**                  | Test small pieces of code (e.g., functions, methods) |
| **Integration**           | Test interactions between components                 |
| **System**                | Test the whole system as a user would                |
| **User Acceptance (UAT)** | Performed by actual end-users                        |

### 🧠 Types of Testing:

- **Functional** (does it work as expected?)
- **Non-functional** (performance, scalability)
- **Regression** (does new code break old functionality?)

> ✅ _Example_:
> Automated tests ensure that changes to the checkout page don't break the login process.

---

## 5. 🚀 Releases

Software is delivered to users in stages to ensure stability and gather feedback.

### 🧾 Common Release Stages:

| Stage                     | Audience              | Purpose                                             |
| ------------------------- | --------------------- | --------------------------------------------------- |
| Alpha                     | Internal team         | Early preview with partial features and likely bugs |
| Beta                      | Select external users | Gather feedback in real-world conditions            |
| GA (General Availability) | All users             | Final, stable release for production use            |

> ✅ _Example_:
> A beta version of a photo editing app is released to influencers for feedback before going public.

---

## 6. 📝 Documentation

Documentation supports both technical and non-technical users.

### 📘 System Documentation

- For engineers, developers, architects
- Includes:

  - README files
  - Inline comments
  - Architecture/design documents
  - Test/verification info
  - Maintenance guides

### 📙 User Documentation

- For end-users
- Includes:

  - User manuals
  - Online help and tutorials
  - Instructional videos
  - Inline help within the app

> ✅ _Example_:
> A system may have Swagger-generated API docs for developers and a PDF user manual for customers.

---

## 🔁 Summary Diagram

```plaintext
+----------------------+      +-----------+     +----------------------+
|  Requirements (SRS)  | -->  |  Design   | --> |      Development     |
|                      |      |           |     | (Coding for Quality) |
+----------------------+      +-----------+     +----------------------+
                                            ↓
                          +--------------------------+
                          |        Testing           |
                          +--------------------------+
                                            ↓
                             +------------------+
                             |     Releases     |
                             +------------------+
                                            ↓
                             +------------------+
                             |   Documentation  |
                             +------------------+
```

---

## ✅ Final Recap

| Process            | Key Output                        | Purpose                              |
| ------------------ | --------------------------------- | ------------------------------------ |
| Requirements       | SRS + Use Cases                   | Define what the software must do     |
| Design             | System Architecture + UI/API docs | Plan how to implement it             |
| Coding for Quality | Source Code + Linters + Comments  | Write reliable and maintainable code |
| Testing            | Test Plans + Bug Reports          | Ensure the software works correctly  |
| Releases           | Alpha, Beta, GA Builds            | Deliver to users at different stages |
| Documenting        | Guides, Comments, Help Files      | Support users and future developers  |

---
