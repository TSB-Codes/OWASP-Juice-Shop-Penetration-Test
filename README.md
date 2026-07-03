# OWASP-Juice-Shop-Penetration-Test

## 📖 Project Overview

This repository documents a comprehensive penetration testing assessment conducted against the **OWASP Juice Shop** vulnerable web application in a controlled local lab environment.

The project demonstrates a structured web application penetration testing methodology, covering environment setup, reconnaissance, authentication analysis, authorization testing, API security assessment, and documentation of findings.

The objective of this project is to gain hands-on experience with industry-standard penetration testing tools while understanding the practical implementation of the **OWASP Top 10** and **OWASP API Security Top 10** concepts.

## 🎯 Objectives

The primary objectives of this project are:

- Deploy OWASP Juice Shop in a secure local laboratory environment using Docker.
- Perform reconnaissance and enumerate the target application using industry-standard tools.
- Analyze authentication and session management mechanisms.
- Evaluate authorization controls and object-level access restrictions.
- Understand common web application vulnerabilities based on the OWASP Top 10 and OWASP API Security Top 10.
- Develop a structured penetration testing methodology.
- Document findings in a professional penetration testing report.

## 🖥️ Lab Environment

The penetration testing lab was configured using the following environment:

| Component | Details |
|-----------|---------|
| Operating System | Kali Linux |
| Target Application | OWASP Juice Shop |
| Deployment Platform | Docker |

## 🛠️ Tools Used

The following tools were used throughout the penetration testing assessment:

| Tool | Purpose |
|------|---------|
| Docker | Deploy the OWASP Juice Shop application locally |
| Burp Suite Community Edition | Intercept, inspect, and modify HTTP requests and responses |
| Nmap | Network reconnaissance and service enumeration |
| Gobuster | Directory and endpoint enumeration |
| cURL | Manual HTTP request testing and header inspection |
| Burp Embedded Browser | Browser integrated with Burp Suite for capturing application traffic |

## 🔍 Testing Methodology

The assessment followed a structured penetration testing methodology to ensure a systematic evaluation of the target application.

The testing process included the following phases:

1. Environment Setup
2. Reconnaissance and Enumeration
3. Authentication Testing
4. Authorization Testing
5. Business Logic Testing
6. Input Validation Testing
7. Cross-Site Scripting (XSS) Testing
8. SQL Injection Testing
9. Documentation and Reporting

Each phase focuses on understanding the application's behavior, identifying potential security weaknesses, and documenting observations using industry-standard penetration testing practices.

## 📂 Repository Structure

```text
OWASP-Juice-Shop-Penetration-Test/
│
├── README.md
├── 01-Lab-Setup.md
├── 02-Reconnaissance.md
├── 03-Authentication-Testing.md
├── 04-Authorization-Testing.md
├── 05-Business-Logic-Testing.md
├── 06-Input-Validation.md
├── 07-XSS-Testing.md
├── 08-SQL-Injection.md
├── 09-Final-Findings.md
│
├── Report/
│   └── OWASP_Juice_Shop_VAPT_Report.pdf
│
└── screenshots/
    ├── lab-setup/
    ├── reconnaissance/
    ├── authentication/
    ├── authorization/
    ├── business-logic/
    ├── input-validation/
    ├── xss/
    └── sql-injection/
```


## ⚠️ Disclaimer

This project was conducted exclusively against a locally deployed instance of **OWASP Juice Shop** within a controlled and authorized laboratory environment.

The purpose of this project is educational—to develop practical web application penetration testing skills and document a structured assessment methodology.

No testing was performed against any system without explicit authorization.
| Proxy Tool | Burp Suite Community Edition |
| Web Browser | Burp Embedded Browser |
| Reconnaissance Tools | Nmap, Gobuster, cURL |
