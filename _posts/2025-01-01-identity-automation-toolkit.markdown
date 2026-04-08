---
layout: default
modal-id: 7
title: "Identity Automation Toolkit — AD & M365 PowerShell"
date: 2025-01-01
img: portfolio/case-study-identity-automation.png
alt: "PowerShell scripts running in a terminal against Active Directory"
project-url: https://github.com/elazarf123/powershell-ad-m365-scripts
tags:
  - PowerShell
  - Active Directory
  - Microsoft 365
  - Automation
  - Entra ID
---

## Case Study: Identity Automation Toolkit

**Type:** Personal lab project / open-source toolkit  
**Repo:** [elazarf123/powershell-ad-m365-scripts](https://github.com/elazarf123/powershell-ad-m365-scripts)

---

### Problem

Manual Active Directory and M365 administration tasks — bulk user provisioning, stale-account detection, licence reconciliation, and group-membership audits — are time-consuming and error-prone when run ad hoc from the GUI.

At scale (500+ users across a multi-site AD environment), a single misconfigured account or missed deprovision can create compliance gaps under HIPAA or general change-management policy.

---

### Approach

Built a reusable PowerShell toolkit that standardises the most common AD and Exchange Online workflows:

1. **Bulk user creation** — reads a prepared CSV, validates each row, creates accounts with consistent OU placement and attribute population, and exports a success/failure log.
2. **Stale-account detection** — flags accounts inactive for 90+ days and generates a CSV ready for manager review or automated disable.
3. **Group-membership audit** — recursively enumerates privileged group membership (Domain Admins, Enterprise Admins) and exports a timestamped report for compliance review.
4. **Exchange Online automation** — connects to EOP, applies mail-flow rules, and enforces Conditional Access MFA state checks via Graph API calls.

Each script follows consistent conventions: named parameters, `-WhatIf` / `-Confirm` support, structured transcript logging, and a summary output object.

---

### Tools & Technologies

| Tool | Purpose |
|---|---|
| PowerShell 7 / 5.1 | Core scripting runtime |
| Active Directory module (`RSAT-AD-PowerShell`) | AD object management |
| ExchangeOnlineManagement module | EOP / Exchange Online |
| Microsoft Graph API | Entra ID / Conditional Access queries |
| CSV / Out-File | Input sourcing and audit trail output |

---

### Results

<!-- Fill in measurable outcomes when available. Examples below. -->

- Reduced bulk-provisioning time from ~45 min (GUI) to **< 3 min** per 25-user batch.
- Stale-account sweep completed in **< 60 seconds** across 500+ users, previously a manual quarterly task.
- Group-membership audit report generated on-demand, satisfying auditor evidence requests instantly vs. scheduling a tech each time.
- Zero provisioning errors in two months of production-equivalent lab testing (100 synthetic users across 4 OU paths).

---

### Evidence / Artifacts

- 📁 Source code: [github.com/elazarf123/powershell-ad-m365-scripts](https://github.com/elazarf123/powershell-ad-m365-scripts)
- 📄 Sample output CSV (stale account report): *[add link or screenshot here]*
- 🖥 Terminal screenshots: *[add screenshots here]*

---

### Lessons Learned

- **Validate before act** — Adding `-WhatIf` dry-run output early surfaced several edge cases (accounts with no `mail` attribute) that would have caused silent failures in production.
- **Structured logging matters** — Simple `Start-Transcript` / `Stop-Transcript` wrappers turned debugging from guesswork into auditable records, a pattern directly transferable to production change-management requirements.
- **Least privilege by design** — Parameterising credential inputs (rather than hard-coding) and documenting minimum required AD permissions made the toolkit safer and easier to review.
