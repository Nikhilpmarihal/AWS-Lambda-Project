# ☁️ AWS Lambda Project

## Secure Serverless REST API with API Gateway

A production-oriented **serverless cloud-native application** built using AWS Lambda and API Gateway.

This project demonstrates how to architect a **secure, scalable, and cost-efficient REST API** leveraging AWS managed services, API key authentication, request validation, and external API integration — aligned with real-world enterprise best practices.

---

## 🚀 Project Overview

This solution showcases:

* Serverless backend using **AWS Lambda**
* REST API exposure via **API Gateway**
* API Key-based authentication
* Request validation at gateway level
* External API integration
* Static frontend (HTML contact form)
* Fully scalable, pay-per-use architecture

The project reflects modern **cloud-native design principles** including stateless execution, event-driven architecture, and infrastructure abstraction.

---

## 🏗️ Architecture Overview

![Image](https://beehiiv-images-production.s3.amazonaws.com/uploads/asset/file/9859d271-50a1-4edb-9c68-a76889346142/Face-blurring_serverless_architecture.png?t=1697379415)

### Flow:

1. User submits form via `contactus.html`
2. API Gateway receives request
3. API Key authentication & validation executed
4. Request forwarded to AWS Lambda
5. Lambda processes data & integrates with external API
6. Response returned to client
7. Redirect to `success.html`

---

## 🔐 Security & Best Practices

* ✅ API Key authentication enforced at API Gateway
* ✅ Request schema validation
* ✅ Environment variable configuration for secrets
* ✅ Principle of least privilege IAM roles
* ✅ Stateless Lambda execution
* ✅ Separation of frontend and backend

---

## 🛠️ Tech Stack

| Layer                | Technology           |
| -------------------- | -------------------- |
| Cloud Platform       | AWS                  |
| Compute              | AWS Lambda           |
| API Layer            | Amazon API Gateway   |
| Language             | Python               |
| Frontend             | HTML                 |
| Authentication       | API Key              |
| External Integration | Third-party REST API |

---

## 📂 Project Structure

```plaintext
aws-lambda-project/
│
├── contactus.html         # HTML contact form interface
├── lambda_function.py     # AWS Lambda Python handler
├── success.html           # Success confirmation page
└── README.md
```

---

## 📌 File Descriptions

### `lambda_function.py`

* Contains Lambda handler function
* Processes incoming JSON payload
* Validates request body
* Calls external API (if configured)
* Returns structured HTTP response

### `contactus.html`

* Static contact form interface
* Sends POST request to API Gateway endpoint
* Includes API key header (if required)

### `success.html`

* Displayed after successful form submission
* Provides confirmation message to user

---

## ⚙️ Deployment Guide

### 1️⃣ Deploy Lambda Function

* Navigate to AWS Console → Lambda
* Create new function (Python runtime)
* Upload `lambda_function.py`
* Configure:

  * Handler: `lambda_function.lambda_handler`
  * Execution role with necessary IAM permissions
* Set environment variables (if required)

---

### 2️⃣ Create API Gateway

* Create new REST API
* Add POST method
* Integrate with Lambda function
* Enable:

  * API Key Required
  * Request validation
* Deploy to stage (e.g., `prod`)

You will receive an endpoint such as:

```
https://xxxx.execute-api.region.amazonaws.com/prod
```

---

### 3️⃣ Configure API Key

* Generate API Key in API Gateway
* Attach to Usage Plan
* Associate with deployed stage

---

### 4️⃣ Update Frontend

Modify `contactus.html`:

```html
<form action="https://your-api-id.execute-api.region.amazonaws.com/prod" method="POST">
```

If required, include API key in request headers via JavaScript.

---

## 🔄 Request Flow Example

### Sample JSON Payload

```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "message": "Hello, this is a test message."
}
```

### Lambda Response

```json
{
  "statusCode": 200,
  "body": "Message processed successfully"
}
```

---

## 📈 Scalability Advantages

* Automatic scaling with AWS Lambda
* No server provisioning required
* Pay-per-execution pricing model
* High availability by default
* Minimal operational overhead

---

## 🧠 Cloud-Native Design Principles Demonstrated

* Event-driven architecture
* Managed infrastructure
* Stateless compute
* Secure API gateway layer
* Decoupled frontend/backend
* External API integration

