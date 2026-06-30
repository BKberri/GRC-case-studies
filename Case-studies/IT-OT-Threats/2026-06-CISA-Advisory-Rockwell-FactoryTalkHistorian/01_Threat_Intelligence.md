# Threat Intelligence Report — Rockwell Automation FactoryTalk Historian SE Multiple Vulnerabilities

## CVE Details

| Field | Value |
|---|---|
| **CVE IDs** | CVE-2025-13036, CVE-2025-44019, CVE-2025-36539 |
| **Vulnerability Name** | Rockwell Automation FactoryTalk Historian SE — Multiple Vulnerabilities (Deserialization, Hardcoded Credentials, Improper Access Control) |
| **Affected Vendor/Product** | Rockwell Automation FactoryTalk Historian SE (Site Edition) — versions per vendor advisory |
| **CVSS Scores** | CVE-2025-13036: 9.8 (Critical) — Insecure deserialization; CVE-2025-44019: 8.4 (High) — Hardcoded/embedded credentials; CVE-2025-36539: 7.5 (High) — Improper access control |
| **CISA Advisory ID** | ICSA-26-167-02 |
| **Advisory Publication Date** | 2026-06-16 |
| **Exploitation Type** | Remote code execution via insecure deserialization; credential-based unauthorized access; access control bypass |
| **Known Exploitation** | Not currently listed in CISA KEV; no confirmed in-the-wild exploitation reported as of this advisory, but vulnerability class (insecure deserialization) is a well-established high-value ICS attack vector |

## Exploitation Summary
Rockwell Automation's FactoryTalk Historian SE — a widely deployed industrial data historian used to collect, store, and analyze OT/ICS process data — contains three chained vulnerabilities disclosed in CISA Advisory ICSA-26-167-02. The most severe, CVE-2025-13036, is an insecure deserialization flaw that could permit unauthenticated remote code execution against the historian server. CVE-2025-44019 involves hardcoded credentials embedded in the product, and CVE-2025-36539 involves improper access control that could allow privilege escalation. Combined, these vulnerabilities could give an attacker with network access to the historian a path to full server compromise and potentially a pivot point into the broader OT/ICS environment.

## Why This Matters for OT/ICS Environments
FactoryTalk Historian servers are typically deployed at the IT/OT boundary, aggregating process data from PLCs, SCADA systems, and other ICS infrastructure for business reporting and analytics. A compromised historian server represents both a direct OT environment foothold and a recurring target for IT-to-OT lateral movement given its bridging role.

## Framework Mapping
- **NIST CSF 2.0:** PR.PS-04 (Software maintained/updated), PR.AA-01 (Identity/credential management), DE.CM-09 (Computing hardware/software monitored)
- **NIST 800-53 Rev 5:** SI-2 (Flaw Remediation), IA-5 (Authenticator Management — hardcoded credentials), AC-3 (Access Enforcement)
- **IEC 62443:** SR 1.1 (Human user identification/authentication), SR 3.1 (Communication integrity), SR 7.6 (Network/security configuration settings)
- **ISO/IEC 27001:2022 Annex A:** A.8.8 (Management of Technical Vulnerabilities), A.8.5 (Secure Authentication)

## Recommended Immediate Action
Apply Rockwell Automation's vendor patches/mitigations for all three CVEs; rotate any hardcoded/default credentials per vendor guidance; review network segmentation between FactoryTalk Historian servers and the OT/ICS network to limit lateral movement potential.

## Risk Rating
**High** — chained vulnerabilities with one critical-severity RCE component (CVSS 9.8), affecting infrastructure at the IT/OT boundary; rated High rather than Critical pending confirmation of active exploitation, but treated as a priority OT patch.
