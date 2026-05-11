# 🔌 USB Baiting Attack Analysis — Parking Lot Exercise

> **Category:** Attack Vector Analysis | Social Engineering | Threat Modeling | **Status:** ✅ Complete

---

## 📋 Scenario

As a security team member at **Rhetorical Hospital**, a USB drive bearing the hospital's logo was found in the parking lot. Using a **virtualized, isolated workstation** (not connected to the hospital network), the drive was safely examined to assess its contents and potential threat.

---

## 🗂️ Contents

The USB drive belonged to **Jorge Bailey**, the hospital's Human Resources Manager. It contained a mixture of **personal and work-related files**, including:

| File Type | Examples |
|---|---|
| Personal | Family photos, pet photos |
| Work — HR | New hire letter, employee shift schedule |
| Identifying info | Name, job title, workplace |

The drive contained **personally identifiable information (PII)** alongside sensitive HR documents — creating a dual risk to both the individual and the organization.

> **In 2–3 sentences:** The USB drive contained a mix of personal files (family/pet photos) and sensitive work documents (new hire letters, shift schedules) belonging to the HR manager. This combination of PII and internal HR data creates a significant exposure, as it identifies a high-value employee and reveals organizational structure and staffing details.

---

## 🧠 Attacker Mindset

An attacker who found this drive before hospital staff would immediately recognize Jorge as an HR manager — a privileged role with access to employee records, payroll, and onboarding systems. The personal photos could be used to craft **highly convincing spear-phishing emails**, impersonating Jorge to trick colleagues into opening malicious attachments. The shift schedule could also help an attacker time a physical or cyber intrusion when certain staff are absent.

> **Additionally**, the drive itself could have been **deliberately planted** — containing hidden malware designed to execute the moment someone curious plugs it into a hospital workstation, establishing a backdoor into clinical or administrative systems.

---

## ⚠️ Risk Analysis

### Technical Risks

| Risk | Description |
|---|---|
| Malware delivery | Drive could contain trojans, ransomware, or keyloggers that auto-execute on plug-in |
| Hardware attack | Specially crafted USB devices (e.g., USB Killers) can fry connected hardware |
| Data exfiltration | PII and HR data can be harvested to enable spear-phishing or credential attacks |
| Backdoor installation | Malicious payload could silently open remote access to the hospital's network |

### Risk Summary

Even without malicious code, this USB drive posed a serious risk. The HR data and PII it contained could enable targeted spear-phishing against Jorge or hospital staff. If found by a threat actor, the shift schedule and new hire documents could support both cyber and physical intrusions. Had the drive been infected and plugged into an unprotected workstation, ransomware or a backdoor could have compromised the entire hospital network — including patient records and critical clinical systems.

---

## 🛡️ Recommended Controls

### Technical Controls
- **Disable USB auto-run/auto-execute** on all hospital workstations via Group Policy
- **Endpoint Detection & Response (EDR)** to flag and quarantine unknown USB devices
- **Data Loss Prevention (DLP)** tools to restrict what can be copied to removable media
- **USB allowlisting** — only approved, registered drives permitted on hospital systems

### Operational Controls
- **Mandatory USB security training** for all staff, covering USB baiting awareness
- **Clear reporting procedures** — any found device must be handed to IT/security, never plugged in
- **Physical security review** of parking lots and entry points (CCTV, access control)

### Managerial Controls
- **Acceptable Use Policy (AUP)** explicitly prohibiting personal USB use on work systems
- **Incident response playbook** for discovered or suspicious removable media
- **Regular security awareness campaigns** targeting social engineering tactics

---

## 🔑 Key Takeaways

- ✅ Virtualization was used correctly — the drive was never plugged into a live network system
- ✅ No files were opened — correct first-response behavior
- ⚠️ Even "clean" USB drives are dangerous — the data alone enables multiple attack vectors
- ⚠️ Found USB drives should **always** be handed to the security team, never plugged in out of curiosity

---

## 📚 References

- [CISA — Security Tips: Using Caution with USB Drives](https://www.cisa.gov/news-events/news/using-caution-usb-drives)
- Google Cybersecurity Certificate — Course 2: Play It Safe: Manage Security Risks

---

*Part of my [Cybersecurity Portfolio](../README.md)*
