# Risk Assessment, CVE-2026-102764 (BeyondTrust Remote Support Authentication Bypass)

**Case ID:** 2026-10-CISA-KEV-BeyondTrust-RemoteSupport-AuthBypass | **Date:** 2026-10-16

## 1. Risk Statement

A suspected China-nexus espionage actor exploited an authentication-bypass flaw in BeyondTrust Remote Support for approximately seven weeks before public disclosure, escalating to root, deploying persistent web-shell and tunneling malware, wiping logs, and moving laterally using stolen administrator credentials. Because Remote Support is a privileged remote-access tool, a compromised instance gives an attacker a trusted channel directly into the networks of every organization and, potentially, every downstream customer that tool is used to support.

## 2. Likelihood Assessment, Score: 5 (Actively Exploited in the Wild)

Confirmed, attributed nation-state exploitation occurred for weeks before disclosure, with Mandiant and CrowdStrike independently tracking the actor. The flaw requires no authentication, and Shadowserver identifies over 1,400 internet-exposed instances, indicating a meaningful population remained reachable throughout the exploitation window.

## 3. Impact Assessment, Score: 5 (Full System Compromise)

The observed post-exploitation chain, root-level SUID escalation, persistent web-shell and tunneler deployment, log wiping, and lateral movement via stolen administrator credentials, represents a complete compromise of the appliance and a foothold for further intrusion into connected environments. Remote-support tools are, by design, trusted and often privileged, amplifying the blast radius of any compromise.

## 4. Risk Scoring

| Factor | Score | Basis |
|---|---|---|
| Likelihood | 5 | Confirmed nation-state exploitation sustained over roughly seven weeks, unauthenticated |
| Impact | 5 | Root-level compromise with persistent malware, log wiping, and credential-based lateral movement |
| **Risk Score (L×I)** | **25** | |
| **Risk Rating** | **Critical** | 20-25 band |

## 5. Current Controls (Pre-Remediation)

Standard perimeter controls provide limited protection for a trusted, often internet-facing remote-support tool whose entire purpose is to accept external connections; the authentication layer itself was the point of failure, and no compensating network control fully substitutes for it.

## 6. Residual Risk (Post-Patch)

**High.** Patching closes the authentication-bypass vector, but given roughly seven weeks of confirmed exploitation before disclosure and documented log-wiping by the attacker, any previously internet-reachable, vulnerable instance should be treated as compromised until an independent forensic review clears it; patch application alone does not establish that prior attacker access or persistence has been removed.

## 7. Business Risk Translation (for Executive Audience)

This is a trusted vendor tool, the one IT and support staff use to remotely access systems, having been silently controlled by a foreign intelligence-linked actor for nearly two months before anyone knew. Any system that tool touched should be assumed potentially exposed until checked.
