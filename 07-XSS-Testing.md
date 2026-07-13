# 🛡️ Cross-Site Scripting (XSS) Testing

> **Objective:** Assess whether the application safely handles user-supplied input and prevents malicious script execution.

---

## Overview

Cross-Site Scripting (XSS) testing was performed to determine whether user-controlled input could be reflected or stored in a manner that allows arbitrary JavaScript execution.

The assessment focused on the application's search functionality and customer feedback feature. Browser Developer Tools and **Burp Suite Community Edition** were used to inspect how user input was processed and rendered within the application.

---

## Testing Methodology

The following areas were evaluated:

- Product Search
- Customer Feedback
- DOM Inspection
- Reflected User Input

---

## Endpoint Assessed

```http
GET /rest/products/search?q=
```

---

## Search Functionality Testing

User-controlled input was submitted through the search feature.

The reflected value was inspected using the browser's Developer Tools.

Example:

```html
<span id="searchValue">xsslearning123</span>
```

---

## Observation

The application reflected the search value inside the DOM.

However:

- Input was displayed as plain text.
- HTML tags were not interpreted.
- JavaScript execution was not observed.

This indicates that the application safely rendered the reflected input within the evaluated context.

---

## Customer Feedback Testing

The Customer Feedback functionality was also evaluated because it accepts and stores user-generated content.

### Observation

- Feedback submission completed successfully.
- Stored content was rendered without executing JavaScript during testing.
- No stored XSS behavior was observed within the scope of the assessment.

---

## Security Observations

- User input was reflected in the application's interface.
- Reflected values were rendered as text.
- No executable JavaScript was observed.
- No confirmed XSS vulnerability was identified during testing.

---

## Assessment Result

✅ Reflected input identified.

✅ Input rendered safely as plain text.

✅ No confirmed Cross-Site Scripting vulnerability observed.

---

## Skills Demonstrated

- Cross-Site Scripting Assessment
- DOM Inspection
- Browser Developer Tools
- Burp Suite Analysis
- Secure Rendering Verification

---

## Screenshots

Store supporting screenshots in:

```
screenshots/xss/
```

Suggested screenshots:

- Search Page
- Developer Tools DOM Inspection
- Burp Request
- Search Results
- Customer Feedback

---

➡️ **Next:** [08-SQL-Injection.md](08-SQL-Injection.md)
