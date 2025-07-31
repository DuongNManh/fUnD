# 🌐 Overview of Web and Cloud Development

## 🎯 Learning Objectives

After going through this document, you will be able to:

- Understand how a web browser interacts with a server
- Distinguish between static and dynamic web content
- Explain front-end vs back-end development
- Describe full-stack development
- Identify key developer tools like IDEs

---

## 🌍 How Websites Work

When you visit a website, here’s what typically happens:

1. You open a browser like Chrome, Edge, Firefox, or Safari.
2. You enter a URL, such as `www.ibm.com`.
3. The browser sends a request to a **web server**.
4. The server responds with resources that make up the website.

These resources include:

- **HTML** – for structure
- **CSS** – for styling
- **JavaScript** – for interactivity

### 🖼️ Plaintext Diagram – Web Request Flow

```plaintext
+-----------+           HTTP Request            +------------+
|           | --------------------------------> |            |
|  Browser  |                                   |   Server   |
|           | <-------------------------------- |            |
+-----------+          HTML, CSS, JS            +------------+

Example:
User types "www.ibm.com" → Browser requests → Server sends content
```

---

## 🗂️ Static vs Dynamic Content

- **Static Content**: Predefined, unchanging files (e.g., about page).
- **Dynamic Content**: Generated based on request context (e.g., user dashboard).

```plaintext
+------------------+         +------------------+
| Static HTML File | ----->  | Rendered As-Is   |
+------------------+         +------------------+

+------------------+         +-----------------------------+
| Dynamic Template | ----->  | Fetched with DB/User Logic  |
+------------------+         +-----------------------------+
```

---

## ☁️ Cloud Applications

- Work like websites but leverage **cloud services**.
- Support:

  - Cloud storage
  - Cloud processing
  - High **scalability** and **resilience**

---

## 🔧 Front-End vs Back-End Development

| Area       | Description                                              | Tools & Languages                      |
| ---------- | -------------------------------------------------------- | -------------------------------------- |
| Front-End  | User interface & interaction (client side)               | HTML, CSS, JS, React, Vue, Angular     |
| Back-End   | Business logic, authentication, data processing (server) | Node.js, Python, Java, .NET, Databases |
| Full-Stack | Combines both front-end and back-end                     | All of the above                       |

### ⚙️ Diagram – Dev Responsibilities

```plaintext
+---------------------+      +--------------------+
| Front-End Developer |      | Back-End Developer |
| - UI Design         |      | - APIs             |
| - DOM Manipulation  |      | - DB Interaction   |
| - Responsiveness    |      | - Auth Logic       |
+---------------------+      +--------------------+
              \                    /
               \                  /
                \                /
                +----------------+
                | Full-Stack Dev |
                +----------------+
```

---

## 🧰 Developer Tools

### 🔤 Code Editors & IDEs

- **Code Editors**: Lightweight, fast (e.g., Sublime, VS Code, Vim)
- **IDEs**: Full-featured (e.g., Visual Studio, Eclipse, NetBeans)

### IDE Features:

- Code editing
- Debugging
- Integration with Git/GitHub
- Extensions & themes
- Build tools

---

## 🧠 Summary

- The browser requests content from a server using URLs.
- HTML, CSS, and JavaScript render the site content.
- Websites often mix **static** and **dynamic** content.
- Development is divided into:

  - **Front-End**: Client-side code and UI
  - **Back-End**: Server-side logic and data
  - **Full-Stack**: Both sides

- Tools like **IDEs** and **code editors** help manage your workflow.

---
