# Threat Intelligence Report — Cisco Unified Communications Manager Static Credential / RCE

## CVE Details

| Field | Value |
|---|---|
| **CVE ID** | CVE-2026-20384 |
| **Vulnerability Name** | Cisco Unified Communications Manager (Unified CM) — Static Default Credential Leading to Root-Level RCE |
| **Affected Vendor/Product** | Cisco Unified Communications Manager (Unified CM) and Unified CM Session Management Edition |
| **CVSS Score** | 10.0 (Critical) |
| **Date Added to KEV** | 2026-06-24 |
| **Exploitation Type** | Authentication bypass via undocumented static credentials, enabling root-level command execution |
| **CISA Remediation Due Date** | 2026-06-27 (3-day mandate, BOD 26-04) |

## Exploitation Summary
CVE-2026-20384 stems from a static, undocumented credential present in affected Cisco Unified CM releases. An attacker who obtains or guesses this credential can authenticate as a privileged user and execute arbitrary commands with root-level privileges on the underlying operating system. Unified CM is Cisco's core enterprise VoIP/call-control platform; root-level compromise grants an attacker the ability to intercept, redirect, or record voice communications, manipulate call routing, and pivot into the broader voice/UC network. CISA confirmed active exploitation and applied the expedited 3-day mandate.

## Why This Matters
Unified CM is deployed as the central call-control system for enterprise VoIP across large organizations, including regulated sectors (financial services, healthcare, government). A static-credential authentication bypass leading to root access on the call-control platform represents both a confidentiality risk (call interception/eavesdropping) and an availability risk (denial of voice services), with direct relevance to organizations subject to wiretap/communications-privacy regulations.

## Framework Mapping
- **NIST CSF 2.0:** PR.AA-01 (Identities and credentials managed), PR.PS-04 (Software maintained/updated), DE.CM-01 (Networks monitored)
- **NIST 800-53 Rev 5:** IA-5 (Authenticator Management), SI-2 (Flaw Remediation), AC-6 (Least Privilege)
- **ISO/IEC 27001:2022 Annex A:** A.8.5 (Secure Authentication), A.8.8 (Management of Technical Vulnerabilities)
- **CIS Controls v8:** Control 5 (Account Management), Control 7 (Continuous Vulnerability Management)

## Recommended Immediate Action
Apply Cisco's patch removing/rotating the static credential immediately; audit Unified CM authentication logs for use of the affected credential, and restrict management-plane access to trusted internal networks only.

## Risk Rating
**Critical** — CVSS 10.0, static credential authentication bypass, root-level command execution, confirmed active exploitation, direct impact to enterprise voice communications confidentiality and availability.
