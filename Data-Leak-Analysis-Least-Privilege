# 🔐 Data Leak Analysis — Least Privilege Assessment

A data privacy incident analysis based on NIST SP 800-53 AC-6 (Least Privilege), applied to an internal data leak at an educational technology company.

---

## 📋 Overview

This project documents the investigation of an accidental data leak caused by insufficient access controls. The analysis follows the **NIST Cybersecurity Framework (CSF)** and **NIST SP 800-53 AC-6** to identify control gaps and recommend improvements to protect information privacy.

---

## 🏢 Company Context

| Factor | Details |
|---|---|
| Industry | Educational technology |
| Product | Automated assignment grading application |
| Data handled | Student records, parent info, instructor data, internal business plans |
| Incident type | Accidental internal document exposure via shared link |
| Regulation reference | NIST SP 800-53 AC-6 (Least Privilege) |

---

## 🚨 Incident Summary

A customer success representative was granted access to a folder of internal documents by a manager. The folder contained confidential files related to a new product offering — including customer analytics and proprietary marketing materials. The manager forgot to revoke access after the meeting. During a later sales call, the representative intended to share only a link to the marketing materials but accidentally shared a link to the entire folder. The external business partner then posted that link publicly on social media.

---

## 📝 Data Leak Worksheet

### Issue(s)

> The data leak occurred because the manager failed to revoke folder access after the internal meeting, violating the principle of least privilege. The representative was given broader access than their role required and lacked the training to distinguish between sharing a specific file versus an entire folder. These two gaps — improper access duration and insufficient access scoping — combined to expose confidential business documents.

---

### Review — NIST SP 800-53: AC-6 (Least Privilege)

> NIST SP 800-53 AC-6 establishes that users should be granted only the minimum level of access necessary to perform their job functions, reducing the risk of accidental or malicious data exposure. The control includes enhancements such as restricting privileged accounts, auditing the use of elevated permissions, and preventing users from accessing resources beyond their defined scope. Organizations are expected to implement these controls consistently and review access rights regularly to ensure they remain appropriate.

---

### Recommendation(s)

Two AC-6 control enhancements that would have prevented this leak:

#### ✅ Enhancement 1 — AC-6(1): Authorize Access to Security Functions
> Restrict access to sensitive folders and documents so that only explicitly authorized roles can open, copy, or share them. The representative should have had read-only access to the specific marketing file — not write or share permissions on the entire folder.

**How it helps:** Prevents users from sharing resources they were never intended to distribute, regardless of whether the action is intentional.

#### ✅ Enhancement 2 — AC-6(3): Network Access to Privileged Commands
> Implement time-bound or session-scoped access grants. Folder access shared for a meeting should automatically expire after the session, requiring re-authorization for future access.

**How it helps:** Eliminates the "forgotten access" problem — the manager wouldn't need to remember to manually revoke access because the system would do it automatically.

---

### Justification

> Implementing role-scoped permissions (AC-6(1)) would have prevented the representative from being able to share the full folder in the first place, since sharing rights would be limited to the specific file they needed. Adding automatic access expiration (AC-6(3)) would have eliminated the risk created by the manager forgetting to revoke access after the meeting. Together, these controls enforce least privilege at both the permission level and the time dimension, significantly reducing the likelihood of similar incidents.

---

## 🔍 NIST SP 800-53 AC-6 Reference

| Enhancement | Name | Description |
|---|---|---|
| AC-6(1) | Authorize Access to Security Functions | Limit access rights to only the files/functions required for a user's role |
| AC-6(2) | Non-Privileged Access for Non-Security Functions | Ensure users operate with standard (non-elevated) accounts by default |
| AC-6(3) | Network Access to Privileged Commands | Restrict privileged commands to only those needed over the network |
| AC-6(9) | Log Use of Privileged Functions | Audit and log all actions taken with elevated permissions |
| AC-6(10) | Prohibit Non-Privileged Users from Executing Privileged Functions | Block users from escalating their own access rights |

> Full reference: [NIST SP 800-53 Rev. 5](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final)

---

## 🛡️ Key Takeaways

- **Least privilege must be enforced technically, not just as policy.** Relying on employees to remember to revoke access is insufficient.
- **Access scope and access duration are both critical.** A user can have the right file but the wrong folder, or the right access today but forgotten access tomorrow.
- **NIST SP 800-53 provides a customizable roadmap** — organizations can select and implement the enhancements most relevant to their risk profile.

---

## 📁 Files

```
├── README.md                  ← This file (full analysis)
└── data-leak-worksheet.md     ← Raw worksheet responses (optional export)
```

---

## 📚 Framework Reference

| Standard | Function | Control |
|---|---|---|
| NIST CSF | Protect (PR) | PR.AC — Identity Management & Access Control |
| NIST SP 800-53 | Access Control | AC-6 — Least Privilege |

---

*Activity based on the Google Cybersecurity Certificate curriculum — Data Privacy & Access Control module.*
