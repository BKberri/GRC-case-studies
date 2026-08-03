# Risk Assessment
## 2026-08-CISA-KEV-Cisco-FMC-HardcodedPassword

## Risk Scoring
| Method | Score | Rating |
|---|---|---|
| Likelihood × Impact Matrix | 5 × 4 = 20 | Critical |
| CVSS Base Score (Cisco Security Impact Rating) | 8.9 | High |
| FAIR Qualitative | High loss exposure given confirmed active exploitation against firewall management infrastructure | High |

## Risk Narrative
Likelihood is scored at the maximum (5) because Cisco has confirmed active zero-day exploitation, not a theoretical or PoC-only vulnerability. Impact is scored at 4 rather than 5 because the initial foothold the hard-coded account provides is low-privileged rather than full administrative control — but Cisco's own guidance that this account is chainable with other FMC vulnerabilities to achieve privilege escalation means the realistic end-state impact approaches full management-plane compromise for a determined attacker. The most probable attack path is direct authentication to an internet-reachable or otherwise-exposed FMC web interface using the hard-coded credential, followed by reconnaissance of firewall policy and event data, and potential chaining toward a privilege-escalation vulnerability to gain full administrative control of the fleet's security policy.

## Framework Control Gaps
- **NIST 800-53 IA-5 (Authenticator Management):** The core defect is a vendor-shipped static credential — a direct violation of the principle that authenticators must be unique, managed, and not embedded in product code or configuration.
- **NIST 800-53 AC-2 (Account Management):** Organizations had no visibility into or ability to disable this account prior to Cisco's disclosure, illustrating the need for periodic vendor-account audits on management-plane appliances.
- **NIST CSF 2.0 PR.AA-01 (Identities and credentials are issued, managed, verified, revoked, and audited):** No customer-side control existed to detect or rotate this credential before the vendor patch.
- **CIS Control 5 (Account Management):** Reinforces the need to inventory and monitor all accounts — including vendor-embedded service accounts — on critical security infrastructure.

## Residual Risk Statement
After applying Cisco's fix (upgrade to 7.0.9+, 7.2.11+, or 7.4.6+ depending on branch) and rotating all credentials, certificates, and keys managed by the affected FMC instance, residual risk drops to Low-Medium. Because Cisco explicitly recommends credential rotation on suspected compromise, any FMC instance that was internet-reachable during the exposure window should be treated as potentially compromised until that rotation and a review of firewall policy for unauthorized changes is complete.
