# 💉 SQL Injection Assessment

> **Objective:** Assess database-backed functionality for SQL Injection indicators and evaluate how the application handles malformed database queries.

---

## Overview

SQL Injection testing was performed to evaluate how OWASP Juice Shop processes user-supplied input within database-backed functionality. The assessment focused on identifying SQL-related error messages, observing server responses, and documenting application behavior when malformed input was submitted.

Testing was conducted using **Burp Suite Community Edition** and **cURL**.

---

## Testing Methodology

The following activities were performed:

- Identified database-backed REST API endpoints.
- Sent modified requests to selected endpoints.
- Observed HTTP status codes.
- Analyzed server responses.
- Documented SQL-related error messages.

---

## Endpoints Assessed

| HTTP Method | Endpoint | Purpose |
|-------------|----------|---------|
| POST | `/rest/user/login` | User Authentication |
| POST | `/api/Addresss` | Address Management |
| GET | `/rest/products/search` | Product Search |

---

## Testing Observations

### Address Management

Repeated requests to the Address Management endpoint resulted in the following response:

```http
HTTP/1.1 500 Internal Server Error
```

Observed error:

```text
SQLITE_CONSTRAINT:
FOREIGN KEY constraint failed
```

---

### Product Search

Testing the product search endpoint produced the following SQLite error:

```text
SQLITE_ERROR:
near "'%'": syntax error
```

The response revealed details about the underlying SQLite database implementation.

---

## Security Observations

- SQLite error messages were exposed to the client.
- Database constraint errors were returned in HTTP responses.
- Verbose error handling disclosed backend implementation details.
- No confirmed SQL Injection vulnerability was identified during the assessment.

---

## Assessment Result

⚠️ Verbose database error messages observed.

⚠️ Database implementation details disclosed.

✅ No confirmed SQL Injection vulnerability demonstrated within the assessment scope.

---

## Skills Demonstrated

- SQL Injection Assessment
- Burp Suite Analysis
- cURL Request Testing
- HTTP Response Analysis
- Error Handling Assessment

---

## Screenshots

Store supporting screenshots in:

```
screenshots/sql/
```

Suggested screenshots:

- Product Search Request
- HTTP 500 Response
- SQLite Error Message
- Burp HTTP History
- cURL Output

---

➡️ **Next:** [09-Final-Findings.md](09-Final-Findings.md)
