## 🎥 **Threat Monitoring**

- Describe threat monitoring,
- Explain repository scanning,
- And explain container scanning.

---

### 🔍 What Is Threat Monitoring?

**Threat monitoring** is the practice of scanning code repositories and containers to identify security issues such as:

- Password mishandling
- Protocol insecurities
- Incorrect file or permission settings

These issues can compromise application security if not detected and resolved early.

---

### 🔁 Where Does Threat Monitoring Fit in the SDLC?

Threat monitoring takes place across **three key stages** of the Software Development Lifecycle (SDLC):

1. **Develop**
2. **Test**
3. **Deploy**

By integrating security tools into these stages, developers can **catch vulnerabilities early** and prevent threats from reaching production.

---

### 🧠 Using Code Scanning Tools in Development

Threat monitoring leverages **code scanning tools** within:

- **Integrated Development Environments (IDEs)**
- **Source Control Management (SCM)** systems (like GitHub or GitLab)

These tools reference known vulnerability databases such as:

- **OWASP Top 10**
- **Common Vulnerabilities and Exposures (CVEs)**

**Code checkers** are essential tools that:

- Analyze code for security flaws
- Highlight syntax, style, and documentation issues
- Provide insight into what needs to be fixed
- Help improve both **security** and **code quality**

---

### 📁 Repository Scanning

**Code repositories**, especially open-source or collaborative ones, carry a **higher risk** of vulnerabilities.

Threat monitoring in repositories includes:

- **Scanning all code changes** in real-time
- Generating **automatic fix pull requests**
- Providing **vulnerability reports** and remediation guidance
- Scanning **every pull request** for security issues
- **Signing commits** using PGP (Pretty Good Privacy) keys to verify trusted contributors

---

### 📦 Container Scanning

**Container scanning** is another crucial part of threat monitoring.
Containers bundle application code with its library dependencies, which can introduce external vulnerabilities.

Here's why container scanning matters:

- Containers often **reuse base images** that may contain known issues
- Scans must include **all layers** of the container image
- Vulnerabilities can exist in both application code and third-party dependencies

**Comprehensive scanning** of all container images helps to:

- Detect inherited vulnerabilities
- Reduce security risks before containers are deployed
- Maintain the integrity of cloud-native applications

---

### ✅ Summary

In this video, you learned that:

- **Threat monitoring** is the process of scanning repositories and containers for security issues.
- It’s integrated into the **Develop**, **Test**, and **Deploy** stages of the SDLC.
- **Code checkers** identify security problems and improve code quality.
- **Repository scanning** detects threats in codebases and manages vulnerabilities proactively.
- **Container scanning** ensures that all application layers are secure, including inherited base images.

---
