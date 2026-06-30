# Business Impact Analysis (BIA)
## Case: CISA KEV 2026-03 — Hikvision & Rockwell Automation Dual Listing
**Date:** 2026-03-10 | **Analyst:** Blaise Kingko

---

## 1. Financial Impact (Quantified)

| Impact Category | Estimate |
|---|---|
| Production downtime (Rockwell impact, primary manufacturing facility) | ~$45,000 / hour |
| Regulatory fines (NERC-CIP / TSA critical infrastructure directives) | Up to $10,000 / day |
| Incident response cost (forensic cleanup, third-party validation) | ~$150,000 |

## 2. Operational Impact

- **Life Safety:** Potential for physical injury to staff if safety interlocks are bypassed via compromised Rockwell controllers.
- **Physical Security:** Loss of perimeter control and inability to audit facility access via compromised Hikvision camera feeds.

## 3. Legal & Reputational Impact

- **Contractual Breach:** Risk of failing "commercially reasonable security" clauses in customer SLAs.
- **Public Trust:** A breach involving surveillance footage carries outsized reputational exposure and risk of investor confidence loss, independent of the technical severity.

## 4. Recovery Objectives

| Metric | Target |
|---|---|
| Recovery Time Objective (RTO) — control logic | 4 hours |
| Recovery Point Objective (RPO) — configuration restore | 24 hours (from known-good backup) |

---

*BIA inputs feed the risk register's Impact scoring and the POA&M prioritization in `06_POAM_Remediation.md`.*
