# POA&M / Remediation Plan, CVE-2026-102764 (BeyondTrust Remote Support Authentication Bypass)

**Case ID:** 2026-10-CISA-KEV-BeyondTrust-RemoteSupport-AuthBypass

| # | Weakness | Action | Resource | Milestone / Due Date | Status |
|---|---|---|---|---|---|
| 1 | Authentication bypass in BeyondTrust Remote Support (CVE-2026-102764) | Confirm patch status on all self-hosted Remote Support and PRA instances; apply the vendor fix immediately if not already covered by automatic updates | IT Service Desk / Infrastructure team | Within 24 hours (emergency, confirmed nation-state exploitation) | Open, Emergency |
| 2 | Unknown scope of nation-state compromise since late August | Engage an independent forensic review of every internet-reachable instance that ran a vulnerable version, checking for SUID-permission changes, the Sawfly web shell, and Bareclaw tunneler artifacts per Mandiant's published indicators | IR / Third-Party Forensics | Within 5 business days | Open, Emergency |
| 3 | Wiped logs limiting forensic certainty | Treat the full confirmed exploitation window (late August 2026 onward) as potentially affected in the absence of reliable logs, and review for anomalous administrator account activity on every system Remote Support was used to access | SOC / IR team | Within 10 business days | Open |
| 4 | Potential credential compromise | Rotate credentials for any administrator accounts used on or through a vulnerable Remote Support instance | IAM team | Within 5 business days of confirmed compromise | Planned |
| 5 | Recurring exposure of privileged remote-access tooling | Implement centralized, off-box audit log forwarding for all privileged remote-access/support tooling so future log-wiping attempts do not erase the only detection trail | Security Architecture | Within 30 days | Planned |
| 6 | Third-party/client exposure (managed-service context) | If this tool is used to support client environments, assess and disclose exposure to affected clients per contractual and regulatory notification obligations | Legal / Client Management | Within applicable notification window | Planned |

**Specific Patch / Configuration Reference:** BeyondTrust Remote Support 26.2.3 and earlier are affected; apply the vendor-released fix per BeyondTrust advisory BT26-05. SaaS customers were patched by the vendor on 2026-10-08; self-hosted customers must patch manually unless automatic updates are enabled.

**Owner of Record:** Blaise Kingko (Program POA&M Owner) | **Last Updated:** 2026-10-19
