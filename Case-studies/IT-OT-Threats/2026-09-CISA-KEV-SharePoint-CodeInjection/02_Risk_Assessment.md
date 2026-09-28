# Microsoft SharePoint Code Injection (CVE-2026-65660) — Risk Assessment

| Field | Details |
|---|---|
| **Case Study ID** | CS-ITOT-2026-09-003 |
| **Risk Register Cross-Reference** | RR-084 |
| **Date** | 2026-09-28 |
| **Author** | Blaise Kingko |

---

## 4. Risk Assessment

### 4.1 Risk Scoring

| Dimension | Score | Rationale |
|---|---|---|
| **Likelihood** | 5 | Actively exploited in the wild — confirmed by CISA's KEV inclusion criteria, which require evidence of active exploitation before an entry is added. Previdian's independent research corroborates real-world exploitation attempts, including a reported two-stage attack pattern. This is a weaponized, currently-exploited flaw, not a theoretical one. |
| **Impact** | 4 | Full compromise (High/High/High across confidentiality, integrity, and availability) is achievable once exploited — code execution on the SharePoint server, exposure of hosted content, potential pivot to connected systems. Impact is scored 4 rather than 5 specifically because the CVSS vector's `PR:L` requirement (see rationale below) narrows the realistic blast radius relative to a fully unauthenticated, pre-auth RCE: the attacker must first hold some low-privilege authenticated foothold, which is a real but non-trivial precondition rather than "any anonymous internet actor." |
| **Risk Score** | 20 (5 × 4) | Falls at the numeric boundary between this program's High and Critical bands. |
| **Risk Rating** | **High** | See explicit banding-override rationale below. |

**Explicit rationale for rating this High rather than Critical, despite a raw score of 20.** Under this program's strict numeric banding (20–25 = Critical, 10–19 = High), a score of 20 would default to Critical. This program is deliberately overriding that default and rating CVE-2026-65660 as **High**, and is documenting why rather than applying the band silently:

1. **PR:L is a real, not cosmetic, precondition.** Microsoft's own CVSS vector (`AV:N/AC:L/PR:L/UI:N/S:U/C:H/I:H/A:H`) requires the attacker to already hold low-privilege authenticated access. This program's other September 2026 Critical-rated findings in this same reporting period (Citrix NetScaler CVE-2026-88771/88772, Check Point CVE-2026-85102/93616) are all `PR:N` — zero-precondition, fully unauthenticated RCE reachable by any anonymous internet actor. Collapsing a `PR:L` finding into the same Critical tier as those `PR:N` findings would blur a distinction that materially affects real-world likelihood and would dilute the signal value of "Critical" as a rating across this program's body of work.
2. **This is a considered exception, applied consistently, not a one-off.** This program is committing to apply this same PR:L-aware reasoning to any future finding that lands at the Critical/High numeric boundary primarily because of an authenticated-attacker precondition, so this override is a standing methodological position, not an ad hoc downgrade of this specific case.
3. **This does not reduce urgency.** Rating this High rather than Critical is a severity-taxonomy decision, not a prioritization signal to deprioritize remediation. The KEV due date (2026-09-28) has elapsed as of this report's publication — see §4.2 and 06_POAM_Remediation.md — and this finding is being treated as an overdue-emergency remediation item on the same operational timeline as this program's Critical-rated findings this reporting period, regardless of its taxonomy label.

### 4.2 Inherent vs Residual Risk

| Risk State | Rating | Notes |
|---|---|---|
| **Inherent Risk** | High (20) | Unpatched on-premises SharePoint Server with any population of authenticated users (employees, contractors, or external guest/collaboration accounts) able to reach the vulnerable code path; actively exploited per KEV. |
| **Residual Risk (post-mitigation, pre-patch)** | Medium–High (estimated 9–16) | Interim compensating controls — tightened site-permission review, disabling unused external sharing/guest access, enhanced monitoring for anomalous authenticated activity, WAF/reverse-proxy rules where feasible — reduce the realistic attacker population able to exploit the precondition, but the underlying code-level flaw remains present and exploitable by any account that still qualifies until the farm is patched. |
| **Residual Risk (post-patch)** | Low (estimated 1–4) | Once all SharePoint Server farms are updated to the fixed builds (16.0.5565.1001+ / 16.0.10417.20198+ / 16.0.19725.20522+) and post-patch verification confirms no prior compromise (see 06_POAM_Remediation.md for IoC-review guidance), residual risk returns to baseline levels consistent with routine on-premises collaboration-platform operation. |
| **Target Residual Risk** | Low (≤4) | Achieved once patching, account-hygiene review, and the control set in 04_Control_Mapping.md are fully implemented and validated. |

*Residual risk figures above are this program's qualitative estimate for tracking purposes pending organization-specific compensating-control validation; they are not derived from a vendor- or CISA-published residual score.*

### 4.3 IT/OT Specific Risk Factors

- [ ] Legacy OT systems with no patch support — **Not applicable.** SharePoint Server is enterprise IT collaboration software; this factor does not apply to the affected product itself.
- [ ] Air gap assumption violated by network connectivity — **Not applicable.** SharePoint Server is not deployed inside an OT network segment in typical architectures.
- [ ] Safety system (SIS) adjacent to affected system — **Not applicable.** No direct adjacency to safety instrumented systems.
- [ ] Single point of failure in critical process — **Conditionally relevant.** Where SharePoint hosts business-critical workflow automation (e.g., approval chains, document-controlled processes), the farm can be a single point of process failure, but this is a business-continuity factor rather than an OT/ICS one — see 03_BIA.md.
- [x] Long patch cycle due to operational continuity requirements — **Applicable.** On-premises SharePoint farms are frequently deprioritized for patching because of the operational disruption of taking a heavily used collaboration platform offline, and because organizations still running SharePoint Server on-premises (rather than SharePoint Online) often do so precisely because of legacy customization or integration dependencies that make patching riskier and slower to validate.
- [ ] No network segmentation between IT and OT zones — **Not applicable** to this finding directly.
- [x] Remote access enabled on OT/enterprise systems — **Conditionally applicable.** Where SharePoint sites are configured with external guest or partner/vendor access (a common on-premises extranet pattern), that externally reachable, lower-trust access is precisely the kind of low-privilege foothold the PR:L precondition contemplates.

**Assessment note:** This finding scores High primarily on the strength of confirmed active exploitation and the severity of full C/I/A compromise once triggered, tempered specifically by the authenticated-access precondition documented in §4.1. It is not an OT/ICS finding in the traditional sense; see 01_Threat_Intelligence.md §2.3 for the narrow, deployment-specific OT-adjacency scenario.

---

## 5. Risk Model Implications

### 5.1 How This Challenges Traditional Risk Models

A risk model that treats "CVSS 8.8, KEV-listed" as a single undifferentiated severity tier misses the operational difference between this finding and a `PR:N` unauthenticated RCE of the same numeric score band. The CVSS base score alone (8.8) does not on its own communicate that the attack requires a precondition an organization can actually influence — account hygiene, guest-access governance, and internal detection of anomalous authenticated behavior are all levers that reduce real-world exploitability of this specific finding in a way they would not for a zero-precondition flaw. A program that scores purely off the numeric CVSS/KEV signal, without reading the vector string, will treat this identically to a fully unauthenticated Critical finding and miss the specific compensating controls that actually move the needle here.

### 5.2 Where Traditional Controls Break Down

Standard external-perimeter controls — firewalling, WAF rules on internet-facing interfaces, network-layer access restriction — are necessary but insufficient for this finding, because the realistic attack path runs through an already-authenticated internal or guest account rather than an anonymous external request. Programs that treat "patch the internet-facing server" as the complete control set will miss the account-governance dimension: guest/external-sharing policy, least-privilege SharePoint site permissions, and behavioral monitoring for authenticated users acting outside their normal pattern. This is a recurring theme this program has flagged for identity-adjacent vulnerabilities generally — the control that matters most is often not at the network boundary.

### 5.3 Emerging Risk Pattern

This is now the program's second-or-third distinct SharePoint Server finding logged in 2026, following the July 2026 machine-key-theft case study (2026-07-CISA-KEV-SharePoint-MachineKeyTheft) and this program's own historical note that a third of four related SharePoint CVEs disclosed earlier in the year were confirmed exploited. Read together with this case, on-premises SharePoint Server has been a recurring, high-value exploitation target across multiple separate disclosure waves within a single calendar year — not an isolated incident. That repetition is itself a risk signal independent of any single CVE's severity score: it indicates sustained attacker interest in the platform and suggests organizations should treat "we run SharePoint Server on-premises" as a standing elevated-risk condition requiring its own governance posture (accelerated patch SLAs, guest-access review cadence, and a periodic strategic reassessment of the platform itself), rather than responding to each new SharePoint CVE as an unrelated one-off. This program's strategic recommendation on platform migration is set out in 06_POAM_Remediation.md.

---

## References

| Source | URL |
|---|---|
| NVD, CVE-2026-65660 | https://nvd.nist.gov/vuln/detail/CVE-2026-65660 |
| MSRC, CVE-2026-65660 update guide | https://msrc.microsoft.com/update-guide/vulnerability/CVE-2026-65660 |
| CISA KEV Catalog | https://www.cisa.gov/known-exploited-vulnerabilities-catalog |
