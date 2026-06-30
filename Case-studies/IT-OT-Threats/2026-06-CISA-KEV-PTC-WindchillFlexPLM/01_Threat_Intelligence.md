# Threat Intelligence Report — PTC Windchill/FlexPLM Remote Code Execution

## CVE Details

| Field | Value |
|---|---|
| **CVE ID** | CVE-2026-12569 |
| **Vulnerability Name** | PTC Windchill / FlexPLM — Unauthenticated Remote Code Execution |
| **Affected Vendor/Product** | PTC Windchill PLM and FlexPLM platforms |
| **CVSS Score** | 9.8 (Critical) |
| **Date Added to KEV** | 2026-06-23 |
| **Exploitation Type** | Unauthenticated remote code execution against internet-facing Windchill/FlexPLM application servers |
| **CISA Remediation Due Date** | 2026-06-28 (3-day mandate, BOD 26-04) |

## Exploitation Summary
CVE-2026-12569 is a critical, unauthenticated remote code execution vulnerability in PTC's Windchill and FlexPLM product lifecycle management (PLM) platforms. CISA confirmed active exploitation and applied the accelerated 3-day remediation mandate under BOD 26-04 given the severity and confirmed in-the-wild attacks. PLM systems of this kind typically store sensitive intellectual property: engineering designs, bills of materials, supplier data, and product specifications — making this a high-value target for industrial espionage and intellectual-property theft in addition to standard ransomware/extortion risk.

## Why This Matters
Windchill and FlexPLM are widely used by manufacturers, aerospace/defense contractors, and industrial product companies to manage engineering and product data throughout its lifecycle. Unauthenticated RCE on an internet-facing PLM instance gives an attacker direct access to an organization's most sensitive intellectual property and design data, with downstream risk to supply chain partners who exchange data through the same platform.

## Framework Mapping
- **NIST CSF 2.0:** PR.PS-04 (Software maintained/updated), PR.DS-01 (Data-at-rest protected), DE.CM-01 (Networks monitored)
- **NIST 800-53 Rev 5:** SI-2 (Flaw Remediation), SC-7 (Boundary Protection), AC-3 (Access Enforcement)
- **ISO/IEC 27001:2022 Annex A:** A.8.8 (Management of Technical Vulnerabilities), A.8.12 (Data Leakage Prevention), A.5.23 (Information Security for Use of Cloud Services, where Windchill is cloud-hosted)
- **CIS Controls v8:** Control 7 (Continuous Vulnerability Management), Control 3 (Data Protection)

## Recommended Immediate Action
Apply PTC's available patch for CVE-2026-12569 to all Windchill/FlexPLM instances immediately; for any instance that cannot be patched within the federal deadline, remove direct internet exposure and restrict access to a VPN-gated administrative network pending remediation.

## Risk Rating
**Critical** — CVSS 9.8, unauthenticated RCE, confirmed active exploitation, direct exposure of high-value intellectual property and engineering data, accelerated federal remediation timeline.
