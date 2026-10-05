# Control Mapping, Storm-3168 Agentic Azure Attack

**Case ID:** 2026-10-MSRC-Storm3168-AgenticAzureAttack

## NIST AI RMF

| Function | Category | Application |
|---|---|---|
| MAP | MAP 1.1, Context of AI-relevant risks is established | Recognizing automation/agentic tooling as an attacker capability multiplier, not only a defensive one |
| MANAGE | MANAGE 4.1, Risk treatment includes identified risks from third-party or adversarial AI use | Response planning must account for attacker timelines compressed by automation |
| GOVERN | GOVERN 1.2, Accountability structures for AI-related risk | Applies to the defending organization's own use of AI-assisted detection/response tooling |

## NIST CSF 2.0

| Function | Subcategory | Application |
|---|---|---|
| GOVERN | GV.OC-01, Organizational context informs cybersecurity risk management | Credential-hygiene policy must explicitly address version-control history exposure, not just current file state |
| PROTECT | PR.AA-05, Access permissions and authorizations are managed, least privilege enforced | Root-cause control, service principal held broader RBAC scope than needed |
| DETECT | DE.CM-01, Networks and network services are monitored | Defender for Resource Manager/Storage/Key Vault anomaly detection |
| RESPOND | RS.MI-02, Incidents are mitigated | Immediate credential rotation and RBAC scoping on detection |

## NIST SP 800-53 Rev 5

| Control | Title | Application |
|---|---|---|
| AC-6 | Least Privilege | Service principal RBAC scope exceeded operational need |
| IR-4 | Incident Handling | Required given confirmed destructive real-world incident |
| CP-9 | System Backup | Backup protection locks were directly targeted by the actor |
| CP-10 | System Recovery and Reconstitution | Recovery infrastructure integrity must be independently verified post-incident |

## ISO/IEC 42001:2023

| Clause | Title | Application |
|---|---|---|
| 8.4 | AI system impact assessment | Applicable both to assessing attacker use of automation and to governance of the defending organization's own AI-assisted response tooling |

## CIS Controls v8

| Control | Safeguard | Application |
|---|---|---|
| Control 6 | 6.8, Define and Maintain Role-Based Access Control | Service principal least-privilege scoping |
| Control 11 | 11.3, Protect Recovery Data | Direct application, recovery/backup locks were the attacker's specific target |
| Control 13 | 13.1, Centralize Security Event Alerting | Rapid, parallelized operations require real-time alerting, not batch log review |
