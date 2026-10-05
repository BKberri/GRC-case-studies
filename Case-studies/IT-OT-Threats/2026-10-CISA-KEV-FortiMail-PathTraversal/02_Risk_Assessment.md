# Risk Assessment, CVE-2026-104286 (FortiMail Path Traversal)

**Case ID:** 2026-10-CISA-KEV-FortiMail-PathTraversal | **Date:** 2026-10-01

## 1. Risk Statement

An unauthenticated, remote attacker can write arbitrary files to an internet-facing FortiMail secure email gateway, establishing persistent, password-free administrative access without any patch currently available from the vendor. This exposes the confidentiality of all mail flowing through the gateway, the integrity of mail-filtering/DLP controls, and provides a durable foothold into the perimeter network the gateway sits on.

## 2. Likelihood Assessment, Score: 5 (Actively Exploited in the Wild)

Confirmed active exploitation is already underway per CISA's KEV listing and independent researcher telemetry (SOCRadar, Techtimes). The vulnerability requires no authentication and no user interaction, and the only available defense is a configuration workaround, not a patch, meaning the population of exposed, vulnerable gateways will remain exploitable for an extended window.

## 3. Impact Assessment, Score: 5 (Full System Compromise)

A successful exploit yields a persistent, unauthenticated backdoor on a system that processes and can resend/inspect all inbound and outbound organizational email, including credentials sent in cleartext, password-reset flows, and any ePHI/PCI-scoped correspondence the gateway relays. Attackers can pivot from the compromised gateway deeper into the mail infrastructure and potentially achieve business email compromise (BEC) at scale.

## 4. Risk Scoring

| Factor | Score | Basis |
|---|---|---|
| Likelihood | 5 | Confirmed active exploitation, pre-auth, no patch available |
| Impact | 5 | Persistent backdoor on perimeter mail gateway; full confidentiality/integrity loss |
| **Risk Score (L×I)** | **25** | |
| **Risk Rating** | **Critical** | 20–25 band |

## 5. Current Controls (Pre-Remediation)

Standard perimeter firewalling and TLS do not mitigate this flaw, since the vulnerable logic is in the gateway's own HTTP request handling. Organizations relying solely on vendor patch cadence have no protection until the interim workaround (disabling IBE, removing internet exposure of the admin interface) is applied.

## 6. Residual Risk (Post-Workaround)

**High**, the interim workaround meaningfully reduces exposure (removing the unauthenticated attack surface) but is not a vendor-validated fix; residual risk remains elevated until Fortinet ships 8.0.2 / 7.6.7 / 7.4.9 and the gateway is confirmed free of any backdoor artifacts planted prior to remediation.

## 7. Business Risk Translation (for Executive Audience)

If exploited, this is not "a server needs a patch", it is an attacker reading the company's email in real time, including password resets and confidential business correspondence, with no visible sign of compromise until data loss or fraud is discovered downstream.
