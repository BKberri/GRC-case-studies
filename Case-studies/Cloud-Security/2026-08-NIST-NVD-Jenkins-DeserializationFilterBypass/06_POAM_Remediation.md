# Plan of Action & Milestones (POA&M)
## 2026-08-NIST-NVD-Jenkins-DeserializationFilterBypass
**Date Opened:** 2026-08-10 | **Source:** Jenkins Security Advisory | **Risk Rating:** High | **Target Closure:** 2026-08-17

## POA&M Table
| Item ID | Weakness / Finding | Affected System | Control Reference | Responsible Role | Planned Action | Milestone 1 | Milestone 2 | Milestone 3 | Target Date | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| POA-202608-022 | JEP-200 deserialization filter bypass (CVE-2026-70426) plus companion arbitrary-file-write findings (CVE-2026-70427, CVE-2026-70428) | Jenkins controller | NIST 800-53 SI-2 | DevOps/Platform Engineering Lead | Upgrade Jenkins to weekly 2.576 / LTS 2.568.2 | 2026-08-11: Confirm current Jenkins version and plan upgrade window | 2026-08-14: Apply upgrade in scheduled maintenance window | 2026-08-15: Validate pipeline functionality post-upgrade | 2026-08-15 | Open |
| POA-202608-023 | Overly broad Agent/Connect and Item/Configure/Item/Build permissions increase exploitable population | Jenkins controller permission model | NIST 800-53 AC-6 | Platform Engineering | Audit and tighten permission assignments | 2026-08-11: Export current permission matrix | 2026-08-13: Identify and remove unnecessary grants | 2026-08-14: Document updated least-privilege baseline | 2026-08-14 | Open |
| POA-202608-024 | Unknown whether any pre-patch exploitation occurred | Jenkins controller filesystem | NIST 800-53 AU-6, IR-4 | Security Operations | Check for unauthorized files in init.groovy.d/ and plugins/ directories | 2026-08-12: Pull directory listings and compare against known-good baseline | 2026-08-14: Complete review | 2026-08-15: Escalate to IR if unauthorized files found | 2026-08-15 | Open |

## Remediation Narrative
Upgrade Jenkins to weekly 2.576 or LTS 2.568.2, which applies the JEP-200 class filter to the previously-uncovered fallback deserialization path and fixes the two companion arbitrary-file-write findings. If immediate upgrade is not feasible, apply the workaround published to the jenkinsci-cert/SECURITY-3911-3930 GitHub repository. In parallel — and deployable immediately as a configuration change ahead of the version upgrade — audit and tighten Agent/Connect, Item/Configure, and Item/Build permission assignments to reduce the population of users/agents capable of reaching the vulnerable code paths.

## Compensating Controls
Until upgraded, restrict Agent/Connect permission to only fully-trusted, organization-managed build agents (removing or isolating any third-party/contractor-operated agents from direct controller connection where possible), and review Item/Configure and Item/Build grants for unnecessary breadth. Monitor `JENKINS_HOME/init.groovy.d/` and `JENKINS_HOME/plugins/` for unexpected file creation.

## Verification & Closure Criteria
Closure requires: (1) confirmed Jenkins version at or above the fixed release, or documented workaround applied; (2) completed permission audit with unnecessary Agent/Connect, Item/Configure, and Item/Build grants removed and a least-privilege baseline documented; (3) completed filesystem review of controller startup-script and plugin directories with no unauthorized files found, or an escalated incident record if compromise is confirmed. Evidence artifacts should be retained in the case file for audit purposes.
