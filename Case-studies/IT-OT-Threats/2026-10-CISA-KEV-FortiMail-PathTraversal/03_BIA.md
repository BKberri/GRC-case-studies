# Business Impact Analysis, CVE-2026-104286 (FortiMail Path Traversal)

**Case ID:** 2026-10-CISA-KEV-FortiMail-PathTraversal | **Scope:** Illustrative mid-size enterprise mail infrastructure

## 1. Affected Business Function

Enterprise email security gateway, inbound/outbound mail filtering, anti-phishing, DLP enforcement, and (where configured) Identity-Based Encryption for sensitive correspondence. Email remains the primary channel for business communication, vendor invoicing, password-reset flows, and, in regulated environments, PHI/PCI-adjacent correspondence.

## 2. Impact Categories

| Category | Impact if Exploited |
|---|---|
| **Confidentiality** | Full visibility into all mail transiting the gateway; attacker-controlled backdoor can exfiltrate messages indefinitely |
| **Integrity** | Attacker can modify, redirect, or inject mail (enabling downstream BEC/invoice-fraud campaigns against customers and vendors) |
| **Availability** | Gateway can be used as a pivot point or disabled entirely, interrupting all organizational email |
| **Regulatory** | If PHI or cardholder-adjacent correspondence transits the gateway, a confirmed compromise may trigger breach-notification obligations (HIPAA Breach Notification Rule, state breach laws) |
| **Reputational** | A mail-gateway compromise enabling BEC against customers/vendors causes direct financial and relationship damage beyond the organization's own loss |

## 3. Recovery Time / Point Objectives (Illustrative)

- **RTO (Recovery Time Objective):** 4 hours for interim workaround deployment (IBE disable + management-interface isolation); full recovery confidence requires forensic sweep before the gateway is trusted again.
- **RPO (Recovery Point Objective):** Not directly applicable to a gateway compromise of this kind, the concern is ongoing interception, not data loss at a point in time; any mail processed between initial exposure and remediation must be treated as potentially viewed by the attacker.

## 4. Dependency Mapping

FortiMail typically sits upstream of the mail store (Exchange/M365/Google Workspace) and downstream of the public MX record, meaning every inbound message is exposed to the gateway before reaching end users. A compromise here has blast radius across the entire organization, not a single system or business unit.

## 5. Criticality Determination

**Critical business function.** Email is rated Tier 1 (cannot sustain >4 hours of compromise without material business impact) for any organization using FortiMail as its primary inbound/outbound mail security control.
