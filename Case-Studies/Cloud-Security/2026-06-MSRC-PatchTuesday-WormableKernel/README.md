# Case Study: CVE-2026-45657 / CVE-2026-47291 — Microsoft June 2026 Patch Tuesday: Wormable Windows Kernel & HTTP.sys RCE
## GRC Intelligence Program — Blaise Kingko
**Category:** Cloud-Security | **Sub-Category:** Windows Infrastructure / Cloud IaaS / Web-Facing Systems
**Run Date:** 2026-06-15 | **Report Period:** 2026-06-08 to 2026-06-15
**Multi-Category:** Yes — also filed under IT-OT-Threats (Windows endpoint/server infrastructure)

---

## Case Overview

Microsoft's June 10, 2026 Patch Tuesday — the largest in program history at 198–208 CVEs — includes two CVSS 9.8 vulnerabilities of critical enterprise concern:

**CVE-2026-45657 — Windows Kernel Use-After-Free RCE (Wormable)**
A use-after-free in the Windows Kernel allows unauthenticated remote attackers to achieve SYSTEM-level code execution via specially crafted TCP/IP packets with no user interaction. ZDI confirmed wormable characteristics comparable to EternalBlue (MS17-010). No confirmed exploitation at time of Patch Tuesday release, but exploit development timeline is measured in days to weeks.

**CVE-2026-47291 — Windows HTTP.sys Integer Overflow RCE**
An integer overflow in Windows HTTP Protocol Stack enables unauthenticated remote attackers to achieve full server RCE via a single malformed HTTP packet. Affects all IIS/HTTP.sys-exposed Windows servers. Registry mitigation available (MaxRequestBytes ≤ 65,534) as compensating control pending patch.

Additional notable critical vulnerabilities in same release: Hyper-V VM guest escape cluster (CVE-2026-47652, CVE-2026-45641, CVE-2026-45607), Remote Desktop Client RCE (CVE-2026-42985).

**CVSS v3.1 (both primaries):** 9.8 (Critical)
**Risk Rating (this program):** Critical (Likelihood 4 × Impact 5 = 20)

---

## Why This Matters to This Program

The wormable kernel CVE creates WannaCry/NotPetya-class risk for any organization with unpatched Windows estate. Cloud environments (Azure IaaS, AWS EC2 Windows) are explicitly in scope — customers are responsible for patching guest OS kernels. The Hyper-V escape CVEs add a second threat vector specific to cloud/virtualized environments. The HTTP.sys RCE directly threatens any internet-facing Windows web infrastructure.

---

## Artifacts Included

| File | Description |
|---|---|
| `01_Threat_Intelligence.md` | CVE details, wormable analysis, full June 2026 Patch Tuesday critical CVE table, framework mapping |
| `02_Risk_Assessment.md` | Dual-CVE risk scoring, cloud-specific risk factors, existing controls analysis |
| `03_BIA.md` | Worm/ransomware scenario impact, financial exposure, RTO/RPO analysis |
| `04_Control_Mapping.md` | Cross-framework mapping, cloud shared-responsibility matrix, gap analysis |
| `05_Executive_Summary.md` | CISO/Board brief — WannaCry analogy, emergency action framing |
| `06_POAM_Remediation.md` | 12-milestone emergency remediation plan with compensating controls and escalation criteria |

---

## Risk Register Entries

**CVE-2026-45657 — Risk ID:** RR-012 | Likelihood: 4 | Impact: 5 | Score: 20 | Rating: Critical
**CVE-2026-47291 — Risk ID:** RR-013 | Likelihood: 4 | Impact: 5 | Score: 20 | Rating: Critical

---

## Key Frameworks Applied

- NIST CSF 2.0 (PR.PS-04, PR.IR-01, DE.CM-09, RC.RP-01)
- NIST SP 800-53 Rev 5 (SI-2, CM-6, SC-7, CP-9, IR-4, RA-5)
- ISO 27001:2022 (A.8.8, A.8.9, A.8.22, A.8.13, A.5.29)
- CIS Controls v8 (Control 7, Control 4, Control 11, Control 12, Control 13)
- CISA BOD 26-04 (Tier 1 remediation priority per new risk-based directive)

---

## GRC Skills Demonstrated

- Emergency Patch Tuesday triage and prioritization for enterprise and cloud environments
- Wormable exploit risk assessment with historical precedent analysis (WannaCry/EternalBlue)
- Cloud shared-responsibility model application (Azure/AWS guest OS vs. hypervisor responsibility)
- Compensating control design for emergency interim risk reduction (MaxRequestBytes registry setting)
- BOD 26-04 compliance mapping under new CISA risk-based prioritization directive

---

*GRC Intelligence Program v2.1 | Case built: 2026-06-15 | Run: Weekly Monday sweep*
