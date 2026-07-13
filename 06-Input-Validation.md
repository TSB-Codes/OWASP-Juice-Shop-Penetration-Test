# 📝 Input Validation Testing

> **Objective:** Evaluate how the application validates user-supplied input and determine whether server-side validation is properly enforced.

---

## Overview

Input Validation Testing was performed to assess whether the OWASP Juice Shop application correctly validates user input before processing it. The assessment focused on identifying weaknesses in server-side validation by modifying intercepted HTTP requests using **Burp Suite Community Edition**.

The Customer Feedback functionality was selected because it accepts user-controlled input and stores submitted data.

---

## Testing Methodology

The following components were evaluated:

- Customer Feedback Form
- Rating Parameter
- Comment Field
- Server Response Validation

---

## Endpoint Assessed

```http
POST /api/Feedbacks
```

---

## Validation Tests Performed

### Test 1 – Rating Outside Expected Range

The `rating` parameter was modified from the expected value to:

```text
10
```

### Observation

- The server accepted the modified request.
- Response returned:

```http
HTTP/1.1 201 Created
```

---

### Test 2 – Negative Rating

The `rating` parameter was modified to:

```text
-1
```

### Observation

- The request was accepted successfully.
- No server-side validation prevented the negative value.

---

### Test 3 – Invalid Data Type

The numeric `rating` parameter was modified to:

```text
"Hello"
```

### Observation

- The application accepted a string value.
- The request completed successfully.
- No server-side type validation was observed.

---

## Summary of Results

| Test | Expected Result | Observed Result |
|------|-----------------|-----------------|
| Rating = 10 | Rejected | Accepted |
| Rating = -1 | Rejected | Accepted |
| Rating = "Hello" | Rejected | Accepted |

---

## Security Observation

The assessment indicates that server-side validation for the `rating` parameter was insufficient. Values outside the expected range and incorrect data types were processed successfully, suggesting that validation relied primarily on client-side controls.

---

## Assessment Result

⚠️ Insufficient server-side validation identified.

⚠️ Invalid input values were accepted.

⚠️ Additional validation should be implemented before processing user input.

---

## Skills Demonstrated

- Input Validation Testing
- Burp Suite Request Modification
- HTTP Request Analysis
- REST API Testing
- Web Application Security Assessment

---

## Screenshots

Store supporting screenshots in:

```
screenshots/input-validation/
```

Suggested screenshots:

- Customer Feedback Form
- Burp Intercept
- Modified Rating Requests
- HTTP 201 Responses
- Burp HTTP History

---

➡️ **Next:** [07-XSS-Testing.md](07-XSS-Testing.md)
