# POA&M / Remediation Plan, Storm-3168 Agentic Azure Attack

**Case ID:** 2026-10-MSRC-Storm3168-AgenticAzureAttack

| # | Weakness | Action | Resource | Milestone / Due Date | Status |
|---|---|---|---|---|---|
| 1 | Credentials exposed in public repository (including via edit/revision history) | Run a credential-scanning sweep that explicitly checks version-control history, not only current file state, across all public and semi-public repositories | AppSec / DevSecOps | Within 7 days | Open |
| 2 | Any credential confirmed or suspected exposed | Rotate immediately; treat "removed" secrets in edit history as compromised regardless of current visibility | Identity & Access Management | Within 24 hours of discovery | Open |
| 3 | Service principals with broader-than-necessary RBAC scope | Audit and reduce service-principal permissions to least privilege required for function | Cloud Platform Team | Within 30 days | Planned |
| 4 | Backup/recovery protection locks removable by the same credentials used elsewhere | Restrict modification of Backup protection locks and Site Recovery configuration to a separate, more tightly controlled privilege tier | Cloud Platform Team | Within 30 days | Planned |
| 5 | Detection timeline may not match attacker automation speed | Evaluate and deploy real-time anomaly detection (e.g., Defender for Resource Manager/Storage/Key Vault) capable of alerting within minutes, not via batch log review | SOC | Within 60 days | Planned |
| 6 | Long-lived service principal secrets | Evaluate migration to managed identities where feasible, reducing reliance on long-lived credentials that can be exposed | Cloud Platform Team | Within 90 days | Planned |

**Owner of Record:** Blaise Kingko (Program POA&M Owner) | **Last Updated:** 2026-10-05
