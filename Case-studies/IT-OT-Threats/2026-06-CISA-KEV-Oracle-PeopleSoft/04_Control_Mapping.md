# Control Mapping Matrix
## Case: CVE-2026-35273 — Oracle PeopleSoft Enterprise PeopleTools Unauthenticated RCE
**Date:** 2026-06-15 | **Analyst:** Blaise Kingko

---

## Cross-Framework Control Mapping

| Control Domain | NIST CSF 2.0 | NIST 800-53 Rev 5 | ISO 27001:2022 Annex A | CIS Controls v8 | Gap / Finding |
|---|---|---|---|---|---|
| **Patch Management** | PR.PS-04 | SI-2 (Flaw Remediation) | A.8.8 (Technical Vulnerability Mgmt) | Control 7.4 | Emergency patch cycle required; standard monthly cadence insufficient for CVSS 9.8 zero-day |
| **Authentication & Access** | PR.AA-01 | IA-2, AC-3, AC-17 | A.5.15 (Access Control), A.8.5 (Secure Auth) | Control 6.3, 6.7 | PeopleSoft must enforce authentication at all API endpoints; zero-trust network access model for ERP |
| **Input Validation** | PR.DS-02 | SI-10 (Information Input Validation) | A.8.28 (Secure Coding) | Control 16.13 | Application-level input validation gap in EMHub API; vendor code defect |
| **Network Segmentation** | PR.IR-01 | SC-7 (Boundary Protection), SC-2 | A.8.22 (Segregation of Networks) | Control 12.2 | Internet-facing PeopleSoft portals should be restricted to authenticated VPN users only |
| **Audit Logging** | DE.CM-01, DE.CM-03 | AU-2, AU-6, AU-12 | A.8.15 (Logging), A.8.16 (Monitoring) | Control 8.2, 8.5 | EMHub API access logs must be captured and reviewed; zero-day window (May 27–June 9) requires retrospective analysis |
| **Incident Response** | RS.AN-03, RS.MI-02, RS.CO-02 | IR-4, IR-5, IR-6 | A.5.26 (IR), A.5.24 (IR Planning) | Control 17.4, 17.6 | Activate IR plan; engage external IR retainer if IOCs found; brief legal/comms on SEC disclosure obligations |
| **Vulnerability Scanning** | ID.RA-01 | RA-5 | A.8.8 | Control 7.1, 7.5 | Zero-day predates scanner signatures; post-patch rescan required to verify remediation |
| **Data Protection** | PR.DS-01, PR.DS-02 | SC-28, MP-4 | A.8.12 (Data Leakage Prevention) | Control 3.3, 3.11 | PeopleSoft data stores require DLP controls; monitor for exfiltration of HR/financial data |
| **Supply Chain / Vendor Risk** | GV.SC-06, GV.SC-07 | SR-3, SR-8 | A.5.21 (ICT Supply Chain), A.5.22 (Vendor Monitoring) | Control 15.1 | Oracle out-of-band patch requires expedited vendor trust verification; confirm patch authenticity |
| **Configuration Management** | PR.PS-02, PR.PS-03 | CM-2, CM-6, CM-8 | A.8.9 (Configuration Management) | Control 4.1, 4.2 | Document emergency change record for patch deployment; update CMDB post-patch |

---

## Financial Services Regulatory Control Overlay

| Regulatory Requirement | Control Obligation | Status |
|---|---|---|
| **GLBA Safeguards Rule (FTC)** | Encrypt financial PII at rest and in transit; implement access controls; incident response procedures | Partial — depends on org maturity |
| **SEC Cybersecurity Disclosure (17 CFR §229.106)** | Material incident disclosure within 4 business days of determining materiality | Active obligation if breach confirmed |
| **NYDFS Part 500.17** | Notify NYDFS Superintendent within 72 hours of cybersecurity event | Active obligation for covered entities in NY |
| **SOX Section 302/404** | Ensure adequacy of ICFR — breach of financial system must be assessed for material weakness | Active obligation for public companies |
| **PCI-DSS v4.0 Req 6.3.3** | Patch critical/high vulnerabilities within defined SLAs | Superseded by emergency priority here |

---

## Control Gap Analysis

| Gap | Severity | Recommended Control Enhancement |
|---|---|---|
| No zero-trust access model for PeopleSoft ERP | High | Implement BeyondCorp / ZTNA architecture; require MFA + device posture check for all PeopleSoft access |
| Insufficient emergency patch procedures | Medium | Define emergency patch SLA for CVSS >= 9.0 zero-days: 24-hour compensating control, 72-hour patch |
| No behavioral monitoring on PeopleSoft application tier | High | Deploy UEBA or application-layer monitoring; alert on anomalous API patterns from EMHub |
| ERP data not covered by DLP policy | Medium | Extend DLP policy to cover PeopleSoft database queries and export functions |
| Retrospective log analysis gap | Medium | Establish 13-month SIEM log retention for all enterprise application tier events |
