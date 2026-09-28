# Microsoft SharePoint Code Injection (CVE-2026-65660) — Plan of Action & Milestones

| Field | Details |
|---|---|
| **Case Study ID** | CS-ITOT-2026-09-003 |
| **Risk Register Cross-Reference** | RR-084 |
| **Date** | 2026-09-28 |
| **Author** | Blaise Kingko |
| **CISA KEV Remediation Due Date** | 2026-09-28 — **elapsed as of publication.** All items below with a target date on or before today should be treated as overdue-emergency actions, not scheduled work. |

---

## 6. Plan of Action & Milestones

### 6.1 Immediate Actions (0–7 Days)

| POAM ID | Weakness | Framework Ref | Remediation Action | Resources Required | Milestone/Target Date | Status | Owner |
|---|---|---|---|---|---|---|---|
| POAM-CS003-01 | Unpatched on-premises SharePoint Server vulnerable to CVE-2026-65660 code injection | NIST 800-53 SI-2; CIS 7.4; CSF PR.PS-06 | Emergency-patch all SharePoint Enterprise Server 2016, SharePoint Server 2019, and SharePoint Server Subscription Edition farms to the fixed builds (16.0.5565.1001+ / 16.0.10417.20198+ / 16.0.19725.20522+) under emergency change approval | Emergency change-approval authority; SharePoint farm administrators; maintenance window | 2026-09-30 (overdue relative to KEV due date; treat as immediate) | Not Started | IT Infrastructure / SharePoint Platform Team |
| POAM-CS003-02 | Unknown whether any SharePoint farm was compromised prior to patching | NIST 800-53 AU-6, RS.AN-03 (CSF) | Perform IoC review of SharePoint application/web front-end server logs, audit logs, and any anomalous authenticated-user activity for the period preceding patch deployment, before treating patched systems as trusted | Incident response team; SharePoint audit log access; EDR/SIEM tooling | 2026-10-01 | Not Started | Security Operations / Incident Response |
| POAM-CS003-03 | Population of external guest/partner accounts with SharePoint access not currently inventoried | NIST 800-53 AC-2; CIS 6.1/6.2; CSF ID.AM-02 | Inventory all SharePoint sites granting external guest or partner/vendor access; identify accounts that would satisfy this CVE's low-privilege authentication precondition | Identity/access management team; SharePoint site-collection administrators | 2026-10-03 | Not Started | Identity & Access Management |

### 6.2 Short-Term Actions (8–30 Days)

| POAM ID | Weakness | Framework Ref | Remediation Action | Resources Required | Milestone/Target Date | Status | Owner |
|---|---|---|---|---|---|---|---|
| POAM-CS003-04 | Least-privilege enforcement on SharePoint site permissions not systematically reviewed | NIST 800-53 AC-6; ISO A.5.15; CSF PR.AA-05 | Conduct least-privilege review of SharePoint site and library permissions, with priority on sites granting external/guest access identified in POAM-CS003-03; remove unnecessary elevated permissions | Site collection administrators; access review tooling; business unit sign-off on access changes | 2026-10-20 | Not Started | Identity & Access Management / Business Unit Owners |
| POAM-CS003-05 | Detection coverage for anomalous authenticated SharePoint activity is limited | NIST 800-53 SI-4, AU-6; CSF DE.CM-01/DE.CM-03; CIS 8.5 | Implement or tune SIEM/monitoring use cases for anomalous authenticated-user behavior on SharePoint (e.g., low-privilege or guest accounts performing administrative or bulk-access actions) | SOC/detection engineering; SIEM platform; SharePoint audit log ingestion | 2026-10-25 | Not Started | Security Operations |
| POAM-CS003-06 | Prior July 2026 SharePoint remediation (machine-key theft case) not confirmed complete across all farms | NIST 800-53 SI-2; CSF ID.RA-01 | Cross-reference remediation status of the July 2026 SharePoint machine-key-theft finding (2026-07-CISA-KEV-SharePoint-MachineKeyTheft) against current SharePoint farm inventory; close any outstanding gaps, including machine-key rotation | SharePoint platform team; prior POAM tracking records | 2026-10-15 | Not Started | IT Infrastructure / SharePoint Platform Team |
| POAM-CS003-07 | Backup/recovery procedures do not explicitly account for pre-detection compromise risk | NIST 800-53 CP-9; ISO A.5.30 | Update SharePoint backup and recovery runbooks to require compromise-verification checks before restoring from backups taken during the exposure window, consistent with 03_BIA.md §3 RPO guidance | Business continuity / disaster recovery team; backup administrators | 2026-10-28 | Not Started | IT Infrastructure / Business Continuity |

### 6.3 Strategic Recommendations (30–90 Days)

| Recommendation | Framework Reference | Business Rationale |
|---|---|---|
| Establish a standing emergency-patch SLA specifically for KEV-listed findings affecting SharePoint Server, shorter than the general application-patching SLA | NIST 800-53 SI-2; CSF GV.RM-04 | This is the program's second-or-third SharePoint on-premises KEV finding in 2026; a platform-specific accelerated SLA is a proportionate response to demonstrated recurring targeting rather than treating each incident as a first-time surprise. |
| Establish a recurring (e.g., quarterly) governance review of SharePoint external guest/partner access, independent of any specific CVE | NIST 800-53 AC-2; CIS 6.1/6.2 | The PR:L precondition in this finding — and the likely precondition in future SharePoint findings, given the platform's exploitation history — makes guest-access governance a standing control need, not a one-time cleanup triggered by this incident. |
| **Evaluate migration from on-premises SharePoint Server to SharePoint Online / Microsoft 365 as a strategic risk-reduction measure, for any organization still running SharePoint Server on-premises.** | CSF GV.RM-04 (risk appetite); ISO A.5.30 | This program has now logged multiple distinct on-premises SharePoint Server KEV findings within a single calendar year — this case, the July 2026 machine-key-theft case, and the earlier-2026 disclosure batch in which a third of four related SharePoint CVEs were confirmed exploited. That recurrence is itself a data point worth weighing: SharePoint Online is not affected by this CVE or the July 2026 finding, and Microsoft-operated cloud services shift a significant share of platform-level patching and infrastructure-hardening burden away from the organization. This program is presenting migration as a **considered strategic option for leadership evaluation, not an absolute mandate** — legitimate constraints (data residency requirements, deep on-premises customization, offline/air-gapped operational needs, cost, or migration complexity) may make continued on-premises operation the right near-term choice for some organizations or some workloads. The recommendation is that this evaluation happen deliberately, with full business and technical input, rather than being deferred indefinitely while the platform continues to accumulate exploitation history. Organizations that determine on-premises SharePoint Server remains necessary should, at minimum, adopt the accelerated-SLA and guest-access-governance recommendations above as compensating standing controls. |

### 6.4 OT-Specific Controls

Not applicable in the general case — SharePoint Server is enterprise IT collaboration software with no direct OT/ICS exposure (see 01_Threat_Intelligence.md §2.3). Organizations that use an on-premises SharePoint farm to host OT-adjacent documentation (engineering drawings, vendor manuals, maintenance/change-management workflows for plant environments) should extend POAM-CS003-03 and POAM-CS003-04 above to explicitly inventory and review access to those specific site collections, since compromise there would expose sensitive operational documentation even though it does not touch OT systems directly.

---

## Status Legend

`Not Started` | `In Progress` | `Blocked` | `Complete` — status values above reflect this report's publication date (2026-09-28) and should be updated by item owners as remediation proceeds.

---

## References

| Source | URL |
|---|---|
| NVD, CVE-2026-65660 | https://nvd.nist.gov/vuln/detail/CVE-2026-65660 |
| MSRC, CVE-2026-65660 update guide | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2026-65660 |
| Previdian, "CVE-2026-65660: Previdian Observes Two-Stage SharePoint Exploitation Attempts" | https://blog.previdian.com/cve-2026-65660-previdian-observes-two-stage-sharepoint-exploitation-attempts/ |
| CISA Known Exploited Vulnerabilities Catalog | https://www.cisa.gov/known-exploited-vulnerabilities-catalog |
