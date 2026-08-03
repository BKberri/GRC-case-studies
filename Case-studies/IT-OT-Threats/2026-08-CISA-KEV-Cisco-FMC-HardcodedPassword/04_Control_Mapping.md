# Control Mapping
## 2026-08-CISA-KEV-Cisco-FMC-HardcodedPassword

## Applicable Frameworks
NIST CSF 2.0 and NIST 800-53 Rev 5 for enterprise risk management and control specificity; ISO 27001:2022 Annex A for ISMS-aligned organizations; CIS Controls v8 for prioritized remediation guidance. HIPAA Security Rule referenced for the illustrative healthcare BIA context.

## Control Mapping Table
| Framework | Control ID | Control Name | Applicability | Gap / Status |
|---|---|---|---|---|
| NIST 800-53 | IA-5 | Authenticator Management | Prohibits static/hard-coded credentials in production systems | Gap (vendor-shipped) |
| NIST 800-53 | AC-2 | Account Management | Requires inventory, review, and disable capability for all accounts including vendor service accounts | Gap |
| NIST 800-53 | CM-6 | Configuration Settings | Baseline configuration should not include undocumented accounts | Gap (vendor-shipped) |
| NIST CSF 2.0 | PR.AA-01 | Identities and credentials are issued, managed, verified, revoked, and audited | No customer-facing control existed to audit this account pre-disclosure | Gap |
| NIST CSF 2.0 | DE.CM-03 | Personnel activity is monitored | Admin login activity to FMC should be monitored for anomalies | Partial |
| ISO 27001 | A.5.17 | Authentication Information | Governs management and protection of authentication credentials | Gap |
| ISO 27001 | A.8.5 | Secure Authentication | Requires secure authentication procedures for all system access | Gap |
| CIS Controls | CIS 5.1 | Establish and Maintain an Inventory of Accounts | Vendor/service accounts on critical infrastructure should be inventoried | Gap |
| HIPAA Security Rule | §164.312(a)(1) | Access Control | Applies to systems, including firewall management infrastructure, that protect access to ePHI-adjacent network segments | Partial |

## Control Narrative
This finding is a textbook credential-management control gap rather than an exploitation-technique flaw: the vendor shipped a static, undocumented account into production management-plane software, which no customer-side control (IA-5, AC-2, CM-6) could have detected or disabled prior to disclosure. This is precisely why vendor-account auditing and configuration-drift detection on Tier-0 security infrastructure matters — a mature control environment periodically reviews the full account inventory on firewall management platforms (not just customer-created accounts) against vendor security advisories, and alerts on any authentication event that does not map to a known administrator.

Detective controls (DE.CM-03, monitoring admin activity on FMC) provide the practical safety net here: even without knowing the hard-coded credential existed, anomalous login patterns — logins from unexpected source IPs, at unusual hours, or from accounts not in the customer's own IAM inventory — should have been flagged. Organizations that had this detective control in place were positioned to catch exploitation attempts even before Cisco's disclosure; organizations without it are dependent entirely on the vendor patch and CISA's KEV deadline to close the exposure window.
