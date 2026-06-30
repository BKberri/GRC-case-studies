# Plan of Action & Milestones (POA&M) — Remediation Plan
## Case: CVE-2026-35273 — Oracle PeopleSoft Enterprise PeopleTools Unauthenticated RCE
**Date:** 2026-06-15 | **Analyst:** Blaise Kingko | **Risk Rating:** Critical

---

## POA&M Summary

| Field | Value |
|---|---|
| **Weakness / Vulnerability** | CVE-2026-35273 — Missing authentication in Oracle PeopleSoft PeopleTools EMHub API enabling unauthenticated RCE |
| **Risk Rating** | Critical (CVSS 9.8) |
| **System / Asset** | Oracle PeopleSoft (PeopleTools 8.61, 8.62) |
| **Responsible Party** | Enterprise Application Engineering / Cloud Security Architecture |
| **Scheduled Completion** | June 22, 2026 (patch); July 3, 2026 (federal hard deadline) |
| **CISA KEV Due Date** | July 3, 2026 (BOD 26-04) |

---

## Remediation Milestones

| Milestone | Action | Owner | Due Date | Status |
|---|---|---|---|---|
| **M1 — Emergency Access Restriction** | Restrict all internet-facing PeopleSoft portals to VPN/internal access only at perimeter firewall. Document as emergency change record. | Cloud Security Arch / Network Engineering | 2026-06-15 (TODAY) | Immediate |
| **M2 — Patch Acquisition & Validation** | Download Oracle emergency patch for CVE-2026-35273. Verify patch authenticity via Oracle support portal hash validation. Stage in patch management system. | Enterprise App Engineering | 2026-06-16 | In Progress |
| **M3 — Patch Deployment — Dev/Test** | Deploy patch to non-production PeopleSoft environments. Validate no service disruption. Run regression tests on HR and Finance workflows. | Enterprise App Engineering | 2026-06-17 | Pending |
| **M4 — Threat Hunt — Retrospective Analysis** | Review EMHub API access logs from 2026-05-20 through 2026-06-12 for: anomalous API calls, unusual process spawning from PeopleSoft service accounts, unexpected outbound connections from PeopleSoft hosts. Use IOCs from Mandiant June 11, 2026 report. | SOC / Threat Intelligence | 2026-06-18 | Pending |
| **M5 — Patch Deployment — Production** | Deploy Oracle patch to all production PeopleSoft instances (HR, Finance, Student Admin). Coordinate maintenance window with business units. | Enterprise App Engineering | 2026-06-22 | Pending |
| **M6 — Post-Patch Vulnerability Scan** | Run authenticated vulnerability scan against all patched PeopleSoft instances to confirm remediation. Validate CVE-2026-35273 no longer detected. | Vulnerability Management | 2026-06-23 | Pending |
| **M7 — CMDB Update** | Update CMDB/asset inventory with new PeopleTools version for all patched instances. Document emergency change completion. | IT Asset Management | 2026-06-24 | Pending |
| **M8 — Legal / Compliance Determination** | If M4 threat hunt finds IOCs: brief CISO + GC within 24 hours; determine materiality for SEC disclosure; engage external IR retainer; initiate regulatory notification triage. | CISO / General Counsel / Compliance | By 2026-06-19 if IOCs found | Pending |
| **M9 — Restore Normal Access** | Re-enable internet-facing access to PeopleSoft portals only after patch is confirmed deployed and no IOCs found. Implement additional WAF rules for EMHub API endpoints. | Cloud Security Arch / Network Engineering | 2026-06-23 (post-scan) | Pending |
| **M10 — Control Improvement — ZTNA** | Initiate project to implement zero-trust network access (ZTNA) for all ERP applications, replacing legacy VPN-based access. Define project scope, budget, and timeline. | Cloud Security Architecture | 2026-08-15 | Planned |

---

## Compensating Controls (Active Until Patch Deployed)

| Control | Implementation | Effectiveness | Remove After |
|---|---|---|---|
| Perimeter firewall restriction of PeopleSoft internet access | Block all direct internet routes to PeopleSoft portal URLs | High — eliminates remote attack vector | After M5 (patch deployed) |
| WAF rule blocking anomalous EMHub API calls | Update WAF signatures based on Mandiant IOC report | Moderate — may not block novel attack variants | After M5 |
| SIEM alert on PeopleSoft service account anomalies | Create detection rule: alert on PeopleSoft service account accessing non-PeopleSoft resources | Moderate — detective, not preventive | Retain permanently as SOC runbook |

---

## Emergency Escalation Path

| Condition | Escalation | Timeline |
|---|---|---|
| IOCs found in threat hunt | Brief CISO + GC; activate IR plan; engage external IR (Mandiant / CrowdStrike retainer) | Within 24 hours of IOC confirmation |
| Ransomware activity detected | Invoke BC/DR plan; isolate PeopleSoft segment; notify cyber insurance carrier immediately | Within 1 hour of detection |
| Confirmed data exfiltration | Legal assessment of materiality; initiate SEC 8-K drafting process; notify state AG offices | Within 24 hours of confirmation |

---

## Success Metrics

| Metric | Target |
|---|---|
| Patch deployment completion | 100% of PeopleSoft instances by June 22, 2026 |
| Post-patch scan clear rate | 0 instances showing CVE-2026-35273 after M5 |
| Threat hunt completion | 100% of environments reviewed by June 18 |
| IOC escalation response time | < 24 hours if IOCs found |
| Time to restore normal access | By June 23, 2026 |
