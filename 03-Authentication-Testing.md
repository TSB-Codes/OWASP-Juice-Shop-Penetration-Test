# 🔐 Authentication Testing

> **Objective:** Assess the application's authentication mechanism, user registration process, login workflow, and session management.

---

## Overview

Authentication testing was performed to evaluate how OWASP Juice Shop verifies user identity before granting access to protected resources. The assessment included user registration, login functionality, JSON Web Token (JWT) generation, and session handling.

HTTP requests and responses were captured and analyzed using **Burp Suite Community Edition**.

---

## Testing Methodology

The following authentication components were evaluated:

- User Registration
- User Login
- JWT Generation
- Session Management
- Authentication Headers

---

## Registration Testing

A new user account was successfully created using the registration form.

**Observed Endpoint**

```http
POST /api/Users
```

### Observation

- Registration completed successfully.
- User details were accepted by the server.
- A successful response confirmed account creation.

---

## Login Testing

The login functionality was tested using the registered account.

**Observed Endpoint**

```http
POST /rest/user/login
```

### Observation

- Valid credentials authenticated successfully.
- The application returned a JSON Web Token (JWT).
- Authenticated requests included the JWT in the `Authorization` header.

---

## JWT Analysis

After successful authentication, the application generated a JWT that was used to authorize subsequent API requests.

Example header:

```http
Authorization: Bearer <JWT_TOKEN>
```

The token remained valid for authenticated operations throughout the assessment.

---

## Security Observations

- JWT-based authentication was implemented.
- Authentication requests used JSON payloads.
- Protected resources required a valid JWT.
- Session state was maintained through bearer token authentication.

---

## Assessment Result

✅ User registration functioned correctly.

✅ Login authentication was successful.

✅ JWT tokens were issued and accepted by protected endpoints.

✅ No authentication bypass was identified during the assessment.

---

## Skills Demonstrated

- HTTP Request Analysis
- Burp Suite Interception
- JWT Analysis
- REST API Testing
- Session Management

---

## Screenshots

Store supporting screenshots in:

```
screenshots/authentication/
```

Suggested screenshots:

- Registration Request
- Login Request
- JWT Response
- Burp HTTP History
- Authorization Header

---

➡️ **Next:** [04-Authorization-Testing.md](04-Authorization-Testing.md)
