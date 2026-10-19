# Risk Assessment, CVE-2026-104935 (Ivanti Connect Secure Authentication Bypass)

**Case ID:** 2026-10-CISA-KEV-Ivanti-ConnectSecure-AuthBypass | **Date:** 2026-10-13

## 1. Risk Statement

An unauthenticated, remote attacker can bypass Connect Secure's authentication controls and execute arbitrary commands on an internet-facing SSL VPN gateway, gaining a foothold directly inside the trusted network perimeter. The attack was already in use against a limited set of victims before Ivanti's disclosure, and the observed intrusion chain also leverages a second, still-unpatched privilege-escalation flaw, meaning patching this CVE alone may not fully remove an existing attacker's access.

## 2. Likelihood Assessment, Score: 5 (Actively Exploited in the Wild)

CISA's KEV listing and Volexity's independent telemetry confirm pre-disclosure, in-the-wild exploitation against real victims. The flaw requires no authentication and no user interaction, and the appliance class (internet-facing remote-access VPN) is a long-standing, high-value target for both opportunistic and targeted threat actors.

## 3. Impact Assessment, Score: 5 (Full System Compromise)

Exploitation yields command execution on a perimeter remote-access gateway, the system explicitly trusted to broker access into the internal network for remote employees. An attacker who compromises Connect Secure can harvest credentials, pivot into internal systems, and, per Volexity's reporting, chain to a privilege-escalation weakness Ivanti has not yet patched, extending the potential blast radius beyond the appliance itself.

## 4. Risk Scoring

| Factor | Score | Basis |
|---|---|---|
| Likelihood | 5 | Confirmed pre-disclosure active exploitation, unauthenticated, no user interaction |
| Impact | 5 | Command execution on perimeter VPN gateway; chainable to unpatched privilege escalation |
| **Risk Score (L×I)** | **25** | |
| **Risk Rating** | **Critical** | 20-25 band |

## 5. Current Controls (Pre-Remediation)

Standard network firewalling does not mitigate this flaw, since the vulnerable logic sits inside the VPN gateway's own authentication path, which is intentionally exposed to the internet to serve remote users. Organizations without emergency out-of-cycle patching processes have no protection until the vendor fix is applied.

## 6. Residual Risk (Post-Patch)

**Medium-High.** Applying the vendor patch closes the authentication-bypass path, but the companion privilege-escalation flaw used in the observed attack chain remains unpatched, and any appliance exploited before 2026-10-13 may already host attacker persistence that a patch alone will not remove.

## 7. Business Risk Translation (for Executive Audience)

This is equivalent to an attacker walking through the remote-access front door used by every traveling or remote employee, without a key, and without anyone being alerted, then potentially using a second unlocked door further inside the building that the landlord has not yet fixed.
