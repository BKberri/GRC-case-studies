# Risk Assessment, CVE-2026-76519 (Cisco Secure Email Gateway Path Traversal)

**Case ID:** 2026-10-CISA-KEV-Cisco-SecureEmailGateway-PathTraversal | **Date:** 2026-10-14

## 1. Risk Statement

An unauthenticated attacker can deliver a crafted email attachment that exploits a path-traversal flaw in Secure Email Gateway's own security-scanning function, planting files and executing commands as root on the appliance, with no login, no workaround, and no user interaction beyond the appliance's normal automatic mail processing.

## 2. Likelihood Assessment, Score: 5 (Actively Exploited in the Wild)

Cisco PSIRT confirmed in-the-wild exploitation attempts before disclosure, and CISA's KEV listing confirms active exploitation. The attack vector, an ordinary inbound email attachment, is trivially deliverable to any internet-facing mail gateway with no attacker authentication required.

## 3. Impact Assessment, Score: 5 (Full System Compromise)

Successful exploitation grants root-level command execution on a perimeter mail security appliance that processes all inbound mail for the organization. An attacker with root access can read, modify, or redirect mail, disable the very security scanning the appliance exists to provide, and use the appliance as a pivot point into the internal network.

## 4. Risk Scoring

| Factor | Score | Basis |
|---|---|---|
| Likelihood | 5 | Confirmed active exploitation, pre-auth, delivered via ordinary email, no user interaction |
| Impact | 5 | Root command execution on perimeter mail gateway; no workaround exists |
| **Risk Score (L×I)** | **25** | |
| **Risk Rating** | **Critical** | 20-25 band |

## 5. Current Controls (Pre-Remediation)

Standard perimeter firewalling and TLS do not mitigate this flaw, since the vulnerable logic is inside the appliance's own attachment-scanning feature, a feature that is itself a security control. Disabling File Reputation (AMP) scanning removes the vulnerable code path but also removes the malware-scanning protection it provides, making it an unattractive compensating control relative to simply applying the fix, since the fix requires no reboot.

## 6. Residual Risk (Post-Patch)

**Low-Medium.** The Content Scanner Tools update closes the vulnerable path without requiring a reboot, and is independent of the AsyncOS upgrade cycle, meaning remediation can be applied immediately. Residual risk centers on confirming no prior compromise occurred on exposed appliances during the disclosure window.

## 7. Business Risk Translation (for Executive Audience)

This is the equivalent of the mail scanner at the front desk, the tool meant to catch malicious attachments, itself being turned into the attacker's way in, with full administrative control of the machine and no way to block the attack other than fixing the scanner itself.
