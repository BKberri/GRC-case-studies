# Citrix NetScaler ADC/Gateway Zero-Day RCE Chain — Framework Control Mapping

| Field | Details |
|---|---|
| **Case Study ID** | CS-ITOT-2026-09-001 |
| **Risk Register Cross-Reference** | RR-079 |
| **Date** | 2026-09-28 |
| **Author** | Blaise Kingko |

---

## 3. Framework Impact Analysis

### 3.1 NIST CSF 2.0 Mapping

| CSF Function | Subcategory | Gap or Finding |
|---|---|---|
| **GOVERN** | GV.RM-04, GV.RM-05 | No evident pre-approved emergency-change process for internet-facing perimeter appliances; risk-response decisions (patch now vs. IoC-review-first) require pre-established governance, not ad hoc determination during an active KEV window. |
| **IDENTIFY** | ID.AM-01, ID.RA-01, ID.RA-05 | Asset inventory must positively confirm NetScaler ADC/Gateway version and build against the fixed versions (14.1-73.37 / 13.1-64.23 and FIPS/NDcPP equivalents) before this finding can be closed; organizations lacking accurate version-level inventory cannot confirm exposure. |
| **PROTECT** | PR.PS-04 (log/config management), PR.AA-01 (identity mgmt), PR.AA-05 (access enforcement), PR.PS-02 (secure configuration) | Improper input validation on an unauthenticated interface reflects a gap in secure-by-default configuration and hardened exposure of the management/gateway interface; PR.AA controls are the layer this vulnerability bypasses entirely (no authentication required). |
| **DETECT** | DE.CM-01 (network monitoring), DE.CM-09 (detection of unauthorized activity), DE.AE-02 (event analysis) | Organizations need positive confirmation, via Citrix's IoC guidance and NetScaler Console review, that exploitation did not occur during the zero-day exposure window — this is a DETECT-function gap independent of whether PROTECT-layer patching has occurred. |
| **RESPOND** | RS.MA-01 (incident response execution), RS.AN-03 (forensic analysis) | Citrix's explicit warning that patching before IoC review destroys forensic evidence is a RESPOND-function sequencing requirement; a RESPOND plan that doesn't account for "investigate before you remediate" on this device class will lose evidence. |
| **RECOVER** | RC.RP-01 (recovery plan execution) | Recovery planning should assume potential appliance downtime during emergency patching (Citrix/CISA both note updates "can be complex and may require downtime") and should have a tested failover or degraded-access plan for the remote-access function. |

### 3.2 NIST SP 800-53 Rev 5 Control Mapping

| Control Family | Control ID | Control Name | Finding |
|---|---|---|---|
| System and Information Integrity | **SI-2** | Flaw Remediation | Core control gap — unpatched firmware is the direct root cause; SI-2 requires timely remediation, and CISA's 3-day KEV due date is a binding SI-2 timeliness benchmark for federal and federally-aligned entities, and a strong best-practice benchmark for all others. |
| Risk Assessment | **RA-5** | Vulnerability Monitoring and Scanning | Organizations must confirm their vulnerability-scanning tooling can positively identify affected NetScaler builds; generic scan coverage may not distinguish sub-versions (e.g., 13.1-64.22 vs. 13.1-64.23). |
| System and Communications Protection | **SC-7** | Boundary Protection | NetScaler is itself a boundary-protection component; its compromise represents a boundary-protection control failure at the architecture's outermost layer. |
| Identification and Authentication | **IA-2** | Identification and Authentication (Organizational Users) | The vulnerability's defining characteristic — unauthenticated RCE — is a direct bypass of IA-2 expectations for any function normally gated by authentication. |
| Incident Response | **IR-4** | Incident Handling | Citrix's IoC-review-before-patch guidance should be incorporated into IR-4 playbooks specific to perimeter-appliance incidents. |
| Configuration Management | **CM-6** | Configuration Settings | Post-incident configuration validation (confirming no unauthorized changes were made during the exposure window) is a CM-6 verification requirement, not merely a patch-and-move-on action. |
| Contingency Planning | **CP-2** | Contingency Plan | Loss of the NetScaler-mediated remote-access path during emergency patching should be a scenario covered in contingency planning, given its role as a single point of failure (§4.3, 02_Risk_Assessment.md). |

### 3.3 ISO 27001:2022 Annex A Mapping

| Annex A Clause | Control | Finding |
|---|---|---|
| **A.8.8** | Management of Technical Vulnerabilities | Direct finding — this is precisely the control this vulnerability tests; organizations need a documented, working technical-vulnerability-management process capable of a 3-day emergency response. |
| **A.8.20** | Networks Security | NetScaler's role as a boundary/network-security control means its compromise is itself a network-security control failure, independent of any downstream impact. |
| **A.5.37** | Documented Operating Procedures | Emergency patching of a perimeter appliance, including the IoC-review-before-patch sequencing, should be a documented operating procedure available to on-call staff, not improvised during the incident. |
| **A.5.24** | Information Security Incident Management Planning and Preparation | Supports the RESPOND-function finding above — incident planning should explicitly address perimeter-appliance compromise scenarios. |
| **A.8.16** | Monitoring Activities | Ongoing monitoring of NetScaler logs/telemetry post-patch is necessary to confirm no residual attacker activity, consistent with Citrix's guidance to check the NetScaler Console for IoCs. |

### 3.4 CIS Controls v8 Mapping

| CIS Control | Safeguard | Finding / Remediation |
|---|---|---|
| **CIS Control 7 — Continuous Vulnerability Management** | 7.1, 7.5, 7.6 | Requires an established vulnerability-management process able to identify affected NetScaler builds and drive remediation within the compressed KEV timeline; 7.6 (automated scanning of internet-facing assets) is particularly relevant given the exposure vector. |
| **CIS Control 12 — Network Infrastructure Management** | 12.1, 12.6 | NetScaler is core network infrastructure; 12.6 (use of secure network management and communication protocols) bears directly on hardening the management interface this vulnerability exploits. |
| **CIS Control 4 — Secure Configuration of Enterprise Assets and Software** | 4.1 | Baseline secure configuration of the NetScaler management plane (minimizing unauthenticated-reachable surface) is a preventive layer independent of the underlying code fix. |
| **CIS Control 17 — Incident Response Management** | 17.4 | Supports the IoC-review-before-patch sequencing as a formal incident-response procedure for this device class. |

### 3.5 IEC 62443 — Applicability Note

IEC 62443 is this program's standard reference for ICS/OT-specific control mapping. It is **not directly applicable** to this finding as scoped: Citrix NetScaler ADC/Gateway is enterprise IT infrastructure, not an industrial automation and control system (IACS) component, and mapping this finding into IEC 62443 zones/conduits terminology would overstate its OT relevance. Where a specific organization's NetScaler instance mediates remote access into an OT environment, the relevant IEC 62443 consideration is narrow and indirect — IEC 62443-3-3 SR 1.13 / SR 2.6 (remote access control into the IACS environment) — but this applies to the access *path*, not to the NetScaler vulnerability itself, and should be assessed only where that specific deployment pattern exists. This program is deliberately not forcing a broader IEC 62443 mapping onto a finding that is, at its core, an enterprise IT perimeter-security issue.

---

## References

| Source | URL |
|---|---|
| CISA Alert (2026-09-27) | https://www.cisa.gov/news-events/alerts/2026/09/27/critical-zero-day-vulnerabilities-exploited-citrix-netscaler-adc-gateway |
| NVD, CVE-2026-88771 | https://nvd.nist.gov/vuln/detail/CVE-2026-88771 |
| Citrix Security Bulletin CTX697096 | https://support.citrix.com/support-home/kbsearch/article?articleNumber=CTX697096 |
