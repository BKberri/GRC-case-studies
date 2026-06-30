# Risk Assessment
## Case: CISA KEV 2026-03 — Hikvision & Rockwell Automation Dual Listing
**Date:** 2026-03-10 | **Analyst:** Blaise Kingko | **Methodology:** NIST SP 800-30 Rev. 1

---

## 1. Methodology

This assessment applies the NIST SP 800-30 Rev. 1 framework for risk determination, evaluating threat source, vulnerability, likelihood, and impact for each finding.

## 2. Risk Identification

| Threat Source | Vulnerability | Likelihood | Impact | Risk Rating |
|---|---|---|---|---|
| Advanced Persistent Threat (APT) | CVE-2017-7921 — Hikvision authentication bypass | High | High | **Critical** |
| Cyber Criminal / Ransomware | CVE-2021-22681 — Rockwell credential exposure | Medium | Very High | **Critical** |

## 3. Vulnerability Analysis

### 3.1 CVE-2017-7921 (Hikvision)
- **Architectural Weakness:** Improper authentication (CWE-287).
- **Attack Vector:** Network-based.
- **Exploitation:** Allows an unauthenticated attacker to impersonate an administrator and gain full access to camera feeds and device configuration.
- **Pivot Potential:** High — these cameras frequently sit on dual-homed networks or have phone-home behavior that can bypass firewall segmentation.

### 3.2 CVE-2021-22681 (Rockwell Automation)
- **Architectural Weakness:** Insecure credential storage and transmission.
- **Attack Vector:** Local / adjacent network.
- **Exploitation:** Attackers can extract credentials to manipulate PLC (Programmable Logic Controller) logic directly.
- **Safety Implications:** Manipulation of industrial control logic can lead to mechanical failure or hazardous material release — this is a life-safety risk, not just a data risk.

## 4. Control Effectiveness Assessment

Standard enterprise controls (antivirus, monthly IT patch cycles) are not effective against either finding, because:
- OT devices do not support traditional EDR agents.
- Hikvision physical security devices were found to be outside the scope of the existing automated vulnerability scanner — an asset-visibility gap, not a scanning-frequency gap.

## 5. Residual Risk

Even after network segmentation is applied, residual risk remains **Medium** until firmware updates are verified across 100% of the affected device inventory. Segmentation alone does not close the gap — it buys time for the patch/firmware cycle to complete.

---

*Risk scoring per program 5×5 Likelihood × Impact methodology.*
