# Business Impact Analysis, CVE-2026-104935 (Ivanti Connect Secure Authentication Bypass)

**Case ID:** 2026-10-CISA-KEV-Ivanti-ConnectSecure-AuthBypass | **Scope:** Illustrative mid-size to large enterprise with remote-access VPN infrastructure

## 1. Affected Business Function

Remote-access SSL VPN connectivity for employees, contractors, and third parties; the trust boundary between the public internet and the internal corporate network. Connect Secure is frequently deployed as the sole remote-access path for a distributed or hybrid workforce.

## 2. Impact Categories

| Category | Impact if Exploited |
|---|---|
| **Confidentiality** | Attacker gains a foothold with visibility into internal network traffic and credential material transiting or cached on the gateway |
| **Integrity** | Attacker-controlled command execution on the gateway can be used to alter its configuration, disable logging, or stage further lateral movement |
| **Availability** | A compromised or disabled VPN gateway can cut off legitimate remote access for the entire remote/hybrid workforce |
| **Regulatory** | A confirmed network-perimeter compromise affecting regulated data (PHI, cardholder data, PII) may trigger breach-notification obligations under HIPAA, state breach laws, or sector-specific rules |
| **Reputational** | Remote-access VPN compromises are a recurring, well-publicized intrusion vector; a disclosed breach via this path invites direct scrutiny of patch-management maturity |

## 3. Recovery Time / Point Objectives (Illustrative)

- **RTO (Recovery Time Objective):** 4-8 hours for emergency patch deployment across all internet-facing Connect Secure appliances; longer if a compromise investigation is required before the appliance can be trusted again.
- **RPO (Recovery Point Objective):** Not directly applicable; the concern is unauthorized access during the exposure window, not a data-loss point in time. Any session or credential activity on the gateway between first plausible exposure and remediation should be treated as potentially attacker-visible.

## 4. Dependency Mapping

Connect Secure typically sits as the sole or primary ingress path for remote users into internal directory services, file shares, and line-of-business applications. A compromise at this layer has organization-wide blast-radius potential rather than being contained to a single business unit, because the gateway itself is a trust anchor for everything behind it.

## 5. Criticality Determination

**Critical business function.** Remote-access connectivity is rated Tier 1 for any organization with a meaningful remote or hybrid workforce, and a compromised VPN gateway additionally functions as a pivot point into the broader internal environment, not merely an availability concern.
