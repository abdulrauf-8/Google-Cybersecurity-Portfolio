# 🧵 PASTA Threat Model — Sneaker Marketplace App

> A complete threat modeling exercise using the **Process of Attack Simulation and Threat Analysis (PASTA)** framework, applied to a mobile sneaker buying and selling application.

---

## 📌 Overview

This project walks through all **seven stages of the PASTA framework** to assess the security posture of a fictional sneaker marketplace app before launch. The goal is to identify vulnerabilities, map potential attack vectors, and recommend security controls — the same process used by security teams in real software development lifecycles.

---

## 🗂️ Framework: PASTA (7 Stages)

| Stage | Name | Key Output |
|-------|------|------------|
| I | Define Business Objectives | Identified 3 core business goals |
| II | Define Technical Scope | Prioritized SQL, API, PKI, SHA-256 |
| III | Decompose the Application | Mapped authentication, payment, and messaging data flows |
| IV | Threat Analysis | Identified SQL injection & session hijacking threats |
| V | Vulnerability Analysis | Pinpointed missing input validation & weak encryption |
| VI | Attack Tree Modeling | Mapped attacker paths to root goal (data/fund access) |
| VII | Risk & Controls | Recommended 4 security controls |

---

## 🎯 Business Objectives (Stage I)

- **Seamless marketplace** — users can sign up, log in, buy, sell, message, and rate with minimal friction
- **Data privacy** — responsible handling of personal information to build user trust
- **Compliant payment processing** — multiple payment options with proper legal and financial safeguards

---

## 🛠️ Technology Scope (Stage II)

The app uses the following technologies, evaluated in priority order:

| Priority | Technology | Purpose | Risk Level |
|----------|------------|---------|------------|
| 🔴 1 | **SQL** | Stores user data, inventory, transactions | High — SQLi is OWASP Top 10 |
| 🟠 2 | **API** | Client-server communication, auth tokens | High — broad external attack surface |
| 🟡 3 | **PKI (AES + RSA)** | Encrypts payment data, secures key exchange | Medium — risk if misconfigured |
| 🟢 4 | **SHA-256** | Hashes passwords and sensitive fields | Low — industry-standard hash function |

> **SQL was prioritized** because it stores every category of sensitive data. A successful SQL injection attack would have the broadest blast radius of any single vulnerability in this application.

---

## 🔄 Data Flow Summary (Stage III)

**Authentication flow**
```
Mobile client → API → SQL database
Passwords hashed with SHA-256 · Session keys exchanged via RSA
```

**Payment flow**
```
Payment form → AES encryption → Third-party payment API → SQL transaction record
```

**Messaging flow**
```
Buyer message → API → SQL database → Retrieved by seller on demand
```

---

## ⚠️ Threat Analysis (Stage IV)

### 1. SQL Injection
Malicious SQL code submitted through unsanitized input fields (search bar, login form) to extract credentials, payment data, or wipe records. Internal logs showing unexpected query patterns are a key indicator.

### 2. Session Hijacking / Broken Authentication
Attackers intercept or steal session tokens via man-in-the-middle attacks, predictable token generation, or insecure mobile storage — allowing impersonation of legitimate users and fraudulent purchases.

---

## 🕳️ Vulnerability Analysis (Stage V)

### 1. Missing Input Validation (CWE-89 / OWASP A03:2021)
If the app concatenates raw user input directly into SQL queries instead of using parameterized statements, attackers can manipulate query logic to dump or corrupt the database.

### 2. Weak or Improperly Implemented Encryption (CWE-311 / OWASP A02:2021)
If payment forms don't enforce HTTPS/TLS end-to-end, or AES keys are hardcoded or weak, payment data can be intercepted in transit or extracted from device memory.

---

## 🌲 Attack Tree Summary (Stage VI)

```
Root Goal: Unauthorized access to user data or funds
│
├── SQL Injection via search/login input
│   └── Dump users table → extract credentials + payment data
│
├── Session Token Interception (MitM)
│   └── Impersonate user → initiate fraudulent purchase
│
└── Brute-force weak password
    └── Access account → retrieve stored payment method
```

---

## 🛡️ Security Controls (Stage VII)

| Control | What It Does |
|---------|-------------|
| **Prepared Statements** | Parameterized queries eliminate SQL injection — no raw user input in query logic |
| **Multi-Factor Authentication (MFA)** | Requires OTP at login, making stolen passwords alone insufficient |
| **TLS 1.3 + AES-256 Encryption** | Protects all data in transit; payment/PII data encrypted at rest with keys in a secure vault |
| **Principle of Least Privilege (PoLP)** | DB accounts get only the permissions they need (e.g. SELECT/INSERT, not DROP) — limits breach impact |

---

## 📁 Files in This Project

```
pasta-threat-model/
├── README.md               ← This file
├── PASTA_worksheet.pdf     ← Completed PASTA worksheet
├── data_flow_diagram.pdf   ← Application data flow diagram
└── attack_tree.pdf         ← Attack tree diagram
```

---

## 🔗 References

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [CVE List — MITRE](https://cve.mitre.org/cve/search_cve_list.html)
- [OWASP Vulnerability List](https://owasp.org/www-community/vulnerabilities/)
- [CWE-89: SQL Injection](https://cwe.mitre.org/data/definitions/89.html)
- [CWE-311: Missing Encryption](https://cwe.mitre.org/data/definitions/311.html)

---



*This project was completed as part of a cybersecurity portfolio. The sneaker app scenario is fictional and used for educational purposes.*
