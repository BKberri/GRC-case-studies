# Plan of Action & Milestones (POA&M) — Remediation Plan
## Case: CVE-2026-45247 — Mirasvit Full Page Cache Warmer Unauthenticated RCE
**Risk ID:** RR-008 | **Opened:** 2026-06-08 | **Target Closure:** 2026-06-10 (expedited — active exploitation)

| # | Action Item | Specific Task | Owner | Start | Due | Status |
|---|---|---|---|---|---|---|
| 1 | Emergency inventory | Identify every Magento 2 / Adobe Commerce instance with the Mirasvit Full Page Cache Warmer extension installed, and record current version | Application Security / E-commerce Engineering | 2026-06-08 | 2026-06-08 (same day) | Open |
| 2 | Emergency patch | Update extension to **v1.11.12 or later** on all identified instances; where update cannot be completed same-day, disable/remove the extension entirely | E-commerce Platform Engineering | 2026-06-08 | 2026-06-09 | Open |
| 3 | Compensating control | Deploy WAF signature(s) published by Imperva (or equivalent vendor) blocking known exploitation request patterns for CVE-2026-45247 on any instance not yet patched | Application Security / Network Security | 2026-06-08 | 2026-06-09 | Open |
| 4 | Forensic sweep | Conduct a web-shell and unauthorized-file scan across `pub/media/`, `var/`, `app/code/`, and custom module directories on all affected servers; diff against known-good FIM baselines | Incident Response / Application Security | 2026-06-09 | 2026-06-10 | Open |
| 5 | Credential rotation (conditional) | If any indicator of compromise is found, immediately rotate all admin/API/database credentials for affected instances and engage incident response | Incident Response / Identity & Access Management | Trigger-based | Immediate upon IOC discovery | Contingent |
| 6 | PCI scope assessment (conditional) | If compromise is confirmed, engage PCI Forensic Investigator (PFI) and assess card-brand notification obligations per PCI-DSS v4.0 | Compliance / Legal / GRC (Blaise Kingko) | Trigger-based | Within 24 hrs of IOC confirmation | Contingent |
| 7 | Closure verification & reporting | Confirm patch deployed fleet-wide and forensic sweep returned clean; brief executive leadership and close the risk-register entry | GRC / Security Architecture (Blaise Kingko) | 2026-06-10 | 2026-06-10 | Open |

### Specific Patch Reference
- Mirasvit Full Page Cache Warmer → update to **version 1.11.12** (vendor-released fix; verify via Magento Marketplace or Mirasvit's official changelog)

### Escalation Trigger
Any discovery of unauthorized files, unfamiliar admin accounts, or anomalous outbound traffic during the forensic sweep (Action #4) immediately escalates this case to **active incident** status — notify CISO, legal/compliance, and initiate the PCI breach-response chain (Actions #5–6) without waiting for the standard POA&M cadence.
