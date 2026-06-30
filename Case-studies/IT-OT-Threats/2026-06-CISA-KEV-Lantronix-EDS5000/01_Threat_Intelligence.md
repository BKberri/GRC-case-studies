# Threat Intelligence Report — Lantronix EDS5000 Code Injection

## CVE Details

| Field | Value |
|---|---|
| **CVE ID** | CVE-2025-67038 |
| **Vulnerability Name** | Lantronix EDS5000 Series — OS Command Injection (HTTP RPC Module) |
| **Affected Vendor/Product** | Lantronix EDS5000 console servers — EDS5008, EDS5016, EDS5032; firmware 2.1.0.0R3 and earlier |
| **CVSS Score** | 9.8 (Critical) |
| **Date Added to KEV** | 2026-06-23 |
| **Exploitation Type** | Unauthenticated OS command injection → root-level remote code execution |
| **CISA Remediation Due Date** | 2026-06-26 (3-day mandate, BOD 26-04) |

## Exploitation Summary
The EDS5000's HTTP RPC module writes a log entry on failed authentication attempts by concatenating the submitted username directly into a shell command, with no input sanitization. An attacker can inject arbitrary OS commands into the username parameter of an unauthenticated login request; the injected commands execute with root privileges. CISA confirmed active exploitation against internet-facing and network-accessible EDS5000 devices prior to KEV listing.

## Why This Matters
The EDS5000 is an industrial-grade device server that bridges legacy serial OT equipment — PLCs, RTUs, sensors, and other field devices that predate IP networking — onto IP networks. A root-level, pre-authentication command injection on this class of device gives an attacker a direct foothold at the IT/OT boundary, with no credentials and no user interaction required. Devices of this type are frequently deployed in industrial, utility, and remote-monitoring environments and are often exposed for remote management.

## Framework Mapping
- **NIST CSF 2.0:** PR.PS-04 (Software maintained/updated), DE.CM-09 (Computing hardware/software monitored), PR.IR-01 (Network integrity protected)
- **NIST 800-53 Rev 5:** SI-2 (Flaw Remediation), SI-10 (Information Input Validation), SC-7 (Boundary Protection), IA-2 (Identification and Authentication)
- **ISO/IEC 27001:2022 Annex A:** A.8.8 (Management of Technical Vulnerabilities), A.8.9 (Configuration Management), A.8.16 (Monitoring Activities)
- **CIS Controls v8:** Control 7 (Continuous Vulnerability Management), Control 4 (Secure Configuration of Enterprise Assets)
- **IEC 62443:** Zone/Conduit model — device sits at the serial-to-IP boundary between OT field devices and the IT network

## Recommended Immediate Action
Upgrade all EDS5000 series devices (EDS5008/5016/5032) to firmware 2.2.0.0R1 immediately; pending patch, remove devices from direct internet exposure and restrict management interface access to a dedicated out-of-band management network.

## Risk Rating
**Critical** — CVSS 9.8, confirmed active exploitation, unauthenticated root-level RCE on a device class that sits directly at the IT/OT boundary.
