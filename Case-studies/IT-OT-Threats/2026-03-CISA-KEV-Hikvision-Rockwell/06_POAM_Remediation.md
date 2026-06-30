# Plan of Action & Milestones (POA&M)
## Case: CISA KEV 2026-03 — Hikvision & Rockwell Automation Dual Listing
**Date:** 2026-03-10 | **Analyst:** Blaise Kingko | **Risk Rating:** Critical

---

| Field | Value |
|---|---|
| **Weakness** | CVE-2017-7921 (Hikvision auth bypass) and CVE-2021-22681 (Rockwell credential exposure) |
| **Vendor Patch** | Available for both — firmware update (Hikvision) and credential vault migration (Rockwell) |
| **Treatment Path** | Asset discovery → segmentation → patch/remediate → validate |
| **CISA KEV Listed** | 2026-03-06 |

---

## Milestones

| ID | Action Item | Owner | Priority | Start | End | Status |
|---|---|---|---|---|---|---|
| PM-01 | Identify all Hikvision/Rockwell assets via Nmap / passive discovery | IT Ops | Critical | 2026-03-07 | 2026-03-08 | Completed |
| PM-02 | Isolate vulnerable OT assets from internet-facing VLANs | Network Security | High | 2026-03-08 | 2026-03-09 | In Progress |
| PM-03 | Apply firmware patch v4.x to Hikvision fleet | Field Ops | Critical | 2026-03-09 | 2026-03-14 | Not Started |
| PM-04 | Migrate Rockwell credential store to MFA / encrypted vault | Identity Lead | High | 2026-03-09 | 2026-03-16 | In Progress |
| PM-05 | Final audit and vulnerability scan validation | GRC Analyst | Medium | 2026-03-17 | 2026-03-18 | Not Started |
| PM-06 | Executive risk report and incident closure | GRC Lead | Low | 2026-03-19 | 2026-03-20 | Not Started |

---

## Success Metrics

| Metric | Target |
|---|---|
| Asset inventory complete (Hikvision + Rockwell) | 100% by March 8 |
| OT assets removed from internet-facing VLANs | 100% by March 9 |
| Firmware/credential remediation complete | 100% by March 16 |
| Closure validation scan passed | By March 18 |
