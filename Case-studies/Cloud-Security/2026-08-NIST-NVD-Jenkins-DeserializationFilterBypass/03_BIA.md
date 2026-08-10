# Business Impact Analysis
## 2026-08-NIST-NVD-Jenkins-DeserializationFilterBypass

## Illustrative Organization Profile
A technology organization running a shared Jenkins controller serving multiple development teams, with a mix of internally-managed and third-party/contractor-operated build agents, and broad developer access to configure and trigger builds across several production-deployment pipelines.

## Impact Assessment
| Impact Category | Description | Severity |
|---|---|---|
| Operational | Controller compromise threatens every pipeline it orchestrates — build integrity, deployment targets, and CI/CD availability for all dependent teams | Critical |
| Financial | Incident response, controller rebuild, and full credential rotation across every pipeline and deployment target the controller touched | High |
| Reputational | A compromised CI/CD controller is a classic software-supply-chain attack vector; disclosure could raise concerns among customers about the integrity of software the organization ships | High |
| Regulatory/Legal | If controller compromise led to tampering with software artifacts later distributed to customers, software-supply-chain-integrity obligations (increasingly referenced in vendor security questionnaires and some regulatory frameworks) may be implicated | Medium |
| Data | Controller-level access exposes every credential (source control, artifact registries, cloud deployment) configured in Jenkins — the scope is bounded by what the controller was set up to access, which for a shared/central controller is typically broad | Critical |

## Recovery Objectives
| Objective | Target |
|---|---|
| RTO (Recovery Time Objective) | 8 hours (patch controller, restart pipelines) |
| RPO (Recovery Point Objective) | 24 hours (last known-good pipeline/job configuration backup) |
| MTTR (Mean Time to Recover) | 2-3 business days including permission-scoping review and, if compromise is suspected, full credential rotation across all managed pipelines |

## Regulatory Exposure
If forensic review determines an attacker used controller-level access to tamper with a build or deployment pipeline that produced customer-facing software, this should be evaluated as a potential software-supply-chain integrity incident, which increasingly carries customer-notification and contractual obligations even absent a specific statutory trigger, particularly for organizations serving regulated industries (financial services, healthcare, government) that impose software-integrity attestation requirements on their vendors.

## Business Continuity Considerations
Because Jenkins controllers are frequently a single point of orchestration for many independent teams' pipelines, planned remediation (patching, permission review) should be scheduled to minimize disruption to active deployment windows, but should not be delayed given the Critical CVSS rating of the primary finding. Compensating controls during remediation should include tightening Agent/Connect and Item/Configure/Item/Build permission scope immediately (a configuration change, not a patch, and thus deployable faster) while the version upgrade is scheduled.
