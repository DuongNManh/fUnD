# 📦 Introduction to the Serverless Framework

## 🎯 Learning Objectives

By the end of this lesson, you will be able to:

- Describe the **Serverless Framework**.
- Explain how to **create** and **deploy** a basic Serverless function.
- Understand how to **test** a Serverless function.

---

## 📘 What is the Serverless Framework?

The **Serverless Framework** is a **free and open-source web framework** built with Node.js that simplifies the deployment and management of serverless applications.

It was originally designed for **AWS Lambda**, but now supports multiple cloud providers, including:

- ✅ **AWS** (Amazon Web Services)
- ✅ **Microsoft Azure**
- ✅ **Google Cloud Platform**
- ✅ **Apache OpenWhisk**

---

## 🧰 Core Features

- **Command Line Interface (CLI)**
  Provides automation and structure for managing functions, events, and resources.

- **Focus on Events & Functions**
  Lets you build **event-driven architectures** with ease.

- **Multi-Cloud Support**
  Not limited to AWS—can be extended to other cloud providers.

---

## 🧱 Key Concepts

| Concept      | Description                                                                                                                                |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------ |
| **Function** | A small unit of code triggered by an event (e.g., HTTP request, file upload).                                                              |
| **Event**    | An action that invokes a function (e.g., new S3 file, scheduled job).                                                                      |
| **Resource** | Infrastructure used by functions (e.g., S3 bucket, database).                                                                              |
| **Service**  | A unit of organization in Serverless Framework. Contains all related functions, events, and resources, defined in a `serverless.yml` file. |

---

## 🖼️ Visualizing the Structure

Here’s a conceptual diagram of how the Serverless Framework organizes and deploys your project:

```plaintext
          ┌────────────────────┐
          │ serverless.yml     │  ← Configuration File
          └────────┬───────────┘
                   │
        ┌──────────▼────────────┐
        │     Service           │  ← Project / Application Unit
        └────────┬──────────────┘
                 │
      ┌──────────▼───────────┐
      │     Functions        │  ← e.g. helloWorld()
      └──┬────────────┬──────┘
         │            │
         ▼            ▼
  Events (e.g.    Resources (e.g.
  HTTP Trigger)   S3 Bucket, DB)
```

---

## 🚀 Deploying a Hello World API (on AWS)

Let’s go through a simple demo:

### 🧪 Prerequisites

- Node.js and `npm` installed.
- AWS CLI and credentials configured.

### 🔧 Step-by-Step

1. **Install the Serverless CLI:**

   ```bash
   npm install -g serverless
   ```

2. **Create a new service:**

   ```bash
   serverless create --template aws-python --path hello-world-api
   cd hello-world-api
   ```

3. **Update function code**
   Edit `handler.py` to return a simple message:

   ```python
   def hello(event, context):
       return {
           "statusCode": 200,
           "body": "Hello World"
       }
   ```

4. **Configure `serverless.yml`:**
   Define the function and HTTP event:

   ```yaml
   functions:
     hello:
       handler: handler.hello
       events:
         - http:
             path: hello
             method: get
   ```

5. **Deploy the service:**

   ```bash
   serverless deploy
   ```

6. **Test the endpoint:**
   After deploy, you will see a public URL. Open it in your browser:

   ```
   https://xyz123.execute-api.us-east-1.amazonaws.com/dev/hello
   ```

   You should see:

   ```
   Hello World
   ```

---

## ✅ Summary

- The **Serverless Framework** simplifies the development and deployment of serverless functions.
- You define functions, events, and resources in a `serverless.yml` file.
- Functions can be triggered by various events like HTTP requests or file uploads.
- The CLI provides a fast way to deploy and test your services.

---
