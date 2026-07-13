# 🔑 Authorization Testing

> **Objective:** Verify that the application properly restricts access to protected resources using JWT-based authorization.

---

## Overview

Authorization testing was performed to evaluate whether authenticated users could access protected resources only after successful login. The assessment focused on verifying the implementation of JSON Web Token (JWT) based authorization and ensuring that sensitive API endpoints required valid authentication.

HTTP requests were intercepted and analyzed using **Burp Suite Community Edition**.

---

## Testing Methodology

The following authorization components were evaluated:

- JWT-Based Authorization
- Protected REST API Endpoints
- Authorization Headers
- User-Specific Resource Access

---

## Authorization Workflow

```
User Login
     │
     ▼
JWT Issued
     │
     ▼
Authorization Header Added
     │
     ▼
Protected API Request
     │
     ▼
Server Validates JWT
     │
     ▼
Access Granted
```

---

## Protected Endpoints Observed

| HTTP Method | Endpoint | Purpose |
|-------------|----------|---------|
| GET | `/api/Addresss` | Retrieve Addresses |
| POST | `/api/Addresss` | Create Address |
| GET | `/api/Cards` | Retrieve Payment Cards |
| POST | `/api/Cards` | Add Payment Card |
| GET | `/api/Deliverys` | Retrieve Delivery Methods |
| POST | `/rest/basket/{id}/checkout` | Checkout |

---

## Observations

- Protected endpoints required a valid JWT.
- Authenticated requests contained the `Authorization: Bearer <token>` header.
- User-specific resources were accessible only after successful authentication.
- JWT validation was consistently enforced during testing.

---

## Assessment Result

✅ JWT-based authorization was successfully implemented.

✅ Protected endpoints required authentication.

✅ No authorization bypass was observed during the assessment.

---

## Skills Demonstrated

- Authorization Testing
- JWT Analysis
- REST API Security Testing
- Burp Suite Request Analysis
- Access Control Verification

---

## Screenshots

Store supporting screenshots in:

```
screenshots/authorization/
```

Recommended screenshots:

- Authorization Header
- Protected API Request
- JWT Token in Burp Suite
- Address API Request
- Checkout Request

---

➡️ **Next:** [05-Business-Logic-Testing.md](05-Business-Logic-Testing.md)
