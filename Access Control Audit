# 🔎 Access Control Audit — Payroll Incident Investigation

An access control assessment based on a real-world payroll fraud scenario, applying event log analysis and employee directory cross-referencing to identify threat actors and recommend mitigations.

---

## 📋 Overview

A suspicious deposit was made from a business to an unknown bank account. This project documents the investigation — reviewing event logs, identifying access control failures, and recommending mitigations to prevent recurrence.

---

## 🏢 Business Context

| Factor | Details |
|---|---|
| Business size | Small/growing (first cybersecurity hire) |
| Incident type | Unauthorized payroll deposit to unknown bank account |
| System affected | Shared cloud drive (company-wide resource management) |
| Investigation method | Event log review + employee directory cross-reference |

---

## 🚨 Incident Summary

A deposit was initiated from the business to an unknown external bank account. The finance manager confirmed they did not authorize the transaction. The payment was stopped before completion. An audit of the event log was conducted to identify the threat actor and the access control gaps that enabled the incident.

---

## 📝 Access Control Worksheet

### Notes — Event Log Observations

> 1. The event log shows the action was performed outside of normal business hours, which is inconsistent with expected activity from a legitimate finance employee and suggests the account may have been accessed by an unauthorized party.

> 2. The IP address recorded in the event log does not match the IP addresses associated with known company devices or office locations, indicating the access likely occurred remotely from an unrecognized source.

---

### Issues — Access Control Failures

> 1. **Overprivileged shared access:** All employees share access to the same cloud drive, meaning users outside the finance department had unnecessary access to sensitive payroll and banking files. The principle of least privilege was not applied.

> 2. **No offboarding or access revocation process:** Cross-referencing the event log with the employee directory revealed that the user associated with the event may no longer be an active employee, suggesting their credentials were never deactivated after leaving the company.

---

### Recommendations — Access Control Mitigations

#### ✅ Recommendation 1 — Implement Role-Based Access Control (RBAC)
Restrict access to sensitive financial files to only the employees whose roles require it (e.g. finance manager, payroll administrator). No other staff should have read or write access to payroll or banking records on the shared drive.

**Why it helps:** Limits the blast radius of any compromised account and removes the opportunity for unauthorized users to interact with sensitive systems.

#### ✅ Recommendation 2 — Establish a Formal Offboarding / Access Revocation Process
Create a documented procedure that immediately deactivates credentials and revokes cloud drive access when an employee leaves the company. This should be a required step in the HR offboarding checklist.

**Why it helps:** Eliminates the risk of former employees — or attackers using their credentials — accessing company systems after their employment ends.

#### ✅ Bonus Recommendation — Enable Multi-Factor Authentication (MFA) + Login Anomaly Alerts
Require MFA for all accounts with access to financial systems, and configure alerts for logins from unrecognized IP addresses or outside business hours.

**Why it helps:** Even if credentials are stolen, MFA prevents unauthorized access. Anomaly alerts allow the security team to respond before damage occurs.

---

## 🔍 Investigation Methodology

```
1. Review Event Log
   └── Note: Event time, IP address, user identity, action taken

2. Cross-Reference Employee Directory
   └── Compare: Active employees vs. user in log
   └── Identify: Access level vs. role requirements

3. Identify Access Control Gaps
   └── Overprivileged accounts
   └── Stale / unrevoked credentials

4. Recommend Mitigations
   └── RBAC implementation
   └── Offboarding procedures
   └── MFA + anomaly detection
```

---

## 🛡️ Key Takeaways

- **Shared drives without access controls are a major liability.** Every employee having access to every file is not a security model — it's a vulnerability.
- **Offboarding is a security event.** Failing to revoke access is as dangerous as never setting access controls in the first place.
- **Event logs are only useful if someone reviews them.** Proactive monitoring and anomaly alerts turn logs from a forensic tool into a prevention tool.

---

## 📚 Framework Reference

| Concept | Application |
|---|---|
| Least Privilege | Finance files restricted to finance roles only |
| Authentication Controls | MFA for sensitive system access |
| Authorization Controls | RBAC on shared cloud drive |
| Access Revocation | Formal offboarding checklist |
| Audit Logging | Event log review for anomaly detection |

---

## 📁 Repo Structure

```
cybersecurity-portfolio/
├── README.md                        ← Portfolio homepage
├── risk-register/
│   └── README.md                    ← Bank risk assessment
├── data-leak-analysis/
│   └── README.md                    ← Least privilege / data leak
└── access-control-audit/
    └── README.md                    ← This file
```

---

*Activity based on the Google Cybersecurity Certificate curriculum — Access Controls & Authentication module.*
