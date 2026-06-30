# Business Impact Analysis — CVE-2026-20384 (Cisco Unified Communications Manager)

## Affected Business Function
Enterprise voice communications and call-control infrastructure, including any call center, executive communications, or emergency call routing dependent on the affected Unified CM deployment.

## Impact Categories

| Impact Type | Assessment |
|---|---|
| **Confidentiality** | Critical — root access enables interception/recording of voice communications, including calls containing PII or sensitive business discussions |
| **Integrity** | High — attacker can manipulate call routing, voicemail, or directory configurations |
| **Availability** | Critical — compromise or destructive action could disable enterprise-wide voice communications, including potentially emergency call routing |
| **Regulatory/Compliance** | High — potential wiretapping/communications-privacy implications under GLBA, HIPAA, or state law if interception occurred |
| **Reputational** | High — a confirmed voice-communications breach involving customer interactions carries significant reputational and legal exposure |

## Recovery Time Objective (RTO) / Recovery Point Objective (RPO)
- **RTO:** Patch and credential rotation within the federal 3-day window (2026-06-27); activate voice-communications continuity plan if Unified CM must be taken offline for remediation.
- **RPO:** Review call detail records (CDRs) and authentication logs for the full exposure window to identify any unauthorized access or interception.

## Dependency Mapping
Call centers handling regulated customer data (payment card, health information) and any emergency call routing dependent on the affected Unified CM cluster should be prioritized for both technical remediation and downstream compliance review.
