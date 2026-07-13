# 🛒 Business Logic Testing

> **Objective:** Evaluate the application's business workflow to determine whether critical operations could be manipulated or bypassed.

---

## Overview

Business Logic Testing was performed to understand how OWASP Juice Shop processes user actions throughout the purchasing workflow. The assessment focused on validating the sequence of operations required to complete an order and identifying any weaknesses in the application's business processes.

The complete workflow was observed and analyzed using **Burp Suite Community Edition** by monitoring the REST API requests exchanged between the client and the server.

---

## Business Workflow

The application follows the workflow shown below:

```
User Login
     │
     ▼
Browse Products
     │
     ▼
Add Product to Basket
     │
     ▼
Create Delivery Address
     │
     ▼
Select Delivery Method
     │
     ▼
Add Payment Card
     │
     ▼
Checkout
     │
     ▼
Order Confirmation
```

---

## Workflow Analysis

The following sequence was observed during testing:

| Step | Action | Endpoint |
|------|--------|----------|
| 1 | User Login | `POST /rest/user/login` |
| 2 | Product Search | `GET /rest/products/search` |
| 3 | Add Product | `POST /api/BasketItems` |
| 4 | Add Address | `POST /api/Addresss` |
| 5 | Retrieve Delivery Options | `GET /api/Deliverys` |
| 6 | Add Payment Card | `POST /api/Cards` |
| 7 | Checkout | `POST /rest/basket/{id}/checkout` |

---

## Basket Management

Products were successfully added to the shopping basket through the application's REST API.

### Observation

- Products were associated with the authenticated user.
- Basket contents were retrieved dynamically.
- Basket operations required authentication.

---

## Address Management

Delivery addresses were created before checkout.

### Endpoint

```http
POST /api/Addresss
```

### Observation

Address information was accepted during normal workflow testing.

During repeated testing, the endpoint returned:

```
HTTP/1.1 500 Internal Server Error

SQLITE_CONSTRAINT:
FOREIGN KEY constraint failed
```

This behavior was documented as part of the assessment.

---

## Payment Card Management

Payment information was successfully submitted before checkout.

### Endpoint

```http
POST /api/Cards
```

### Observation

- Payment cards were linked to the authenticated user.
- Payment details were available during checkout.

---

## Delivery Selection

Delivery options were retrieved successfully.

### Endpoint

```http
GET /api/Deliverys
```

### Observation

The application required a delivery method before allowing checkout.

---

## Checkout

The checkout workflow required:

- Delivery Address
- Payment Card
- Delivery Method

### Endpoint

```http
POST /rest/basket/{id}/checkout
```

### Observation

The checkout completed successfully and generated an order confirmation.

---

## Security Observations

- Business operations followed the intended sequence.
- Authentication was required throughout the checkout workflow.
- No business workflow bypass was identified.
- REST APIs enforced the expected order of operations.

---

## Assessment Result

✅ Checkout workflow successfully completed.

✅ Business workflow sequence was enforced.

✅ No business logic bypass was identified.

---

## Skills Demonstrated

- Business Logic Assessment
- REST API Analysis
- Workflow Mapping
- Burp Suite HTTP Analysis
- Web Application Security Testing

---

## Screenshots

Store supporting screenshots in:

```
screenshots/business-logic/
```

Suggested screenshots:

- Shopping Basket
- Address Request
- Payment Card Request
- Delivery Selection
- Checkout Request
- Order Confirmation
- Burp HTTP History

---

➡️ **Next:** [06-Input-Validation.md](06-Input-Validation.md)
