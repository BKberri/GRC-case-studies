# Risk Assessment, CVE-2026-76504 (Cisco SD-WAN Manager Auth Bypass)

**Case ID:** 2026-10-CISA-KEV-Cisco-SDWAN-HexEncodingBypass | **Date:** 2026-09-30

## 1. Risk Statement

An unauthenticated, remote attacker can bypass authentication on Cisco Catalyst SD-WAN Manager using a simple URI hex-encoding trick, gaining full administrative access to the system that centrally manages routing, policy, and configuration for an organization's entire SD-WAN fabric. Compromise of the management plane can cascade into compromise or disruption of every edge device it controls.

## 2. Likelihood Assessment, Score: 5 (Actively Exploited in the Wild)

Cisco's own PSIRT discovered this vulnerability through a real-world TAC support case involving active exploitation, not through proactive research, meaning attacker activity preceded public disclosure. No workaround exists, only an upgrade, so the exposure window for unpatched systems remains open until the organization completes the upgrade.

## 3. Impact Assessment, Score: 5 (Full System Compromise)

Admin-level access to SD-WAN Manager is equivalent to admin-level access to the organization's entire wide-area network control plane. An attacker can alter routing policy, exfiltrate network topology and configuration data, pivot to connected edge devices, or disrupt WAN connectivity across every site the fabric serves, a single point of compromise with organization-wide blast radius.

## 4. Risk Scoring

| Factor | Score | Basis |
|---|---|---|
| Likelihood | 5 | Confirmed active exploitation discovered via real-world TAC case; no workaround available |
| Impact | 5 | Full administrative compromise of the WAN management plane; cascades to all managed edge devices |
| **Risk Score (L×I)** | **25** | |
| **Risk Rating** | **Critical** | 20–25 band |

## 5. Current Controls (Pre-Remediation)

Standard network segmentation protects edge devices from direct exposure, but SD-WAN Manager itself is frequently reachable from internal management networks or, in some deployments, more broadly, and the authentication bypass defeats the one control (login) that would otherwise prevent unauthorized administrative access.

## 6. Residual Risk (Post-Patch)

**Low-Medium**, once upgraded to a fixed release, the specific authentication-bypass path is closed. Organizations should still complete the recommended TAC-assisted compromise review, since the vulnerability was actively exploited before disclosure and some instances may already be compromised independent of patch status.

## 7. Business Risk Translation (for Executive Audience)

This is the equivalent of someone finding an unlocked side door into the system that controls how every office location in the company connects to the network and to each other, and that door required no key at all.
