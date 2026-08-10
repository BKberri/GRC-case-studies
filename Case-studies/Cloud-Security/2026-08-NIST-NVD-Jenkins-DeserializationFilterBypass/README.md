# 2026-08-NIST-NVD-Jenkins-DeserializationFilterBypass
**Date:** 2026-08-10 | **Source:** Jenkins Security Advisory / NIST NVD | **Category:** Cloud-Security | **Risk Rating:** High

## Summary
Jenkins Security Advisory 2026-08-05 disclosed 22 vulnerabilities across Jenkins core and 15 plugins. The most severe, CVE-2026-70426 (SECURITY-3911, CVSS 3.1: 9.0, Critical), is a JEP-200 deserialization class-filter bypass in the Remoting library used for controller-agent communication: a fallback code path in Remoting's deserialization implementation is not covered by the class filter, allowing agent processes, code running on agents, or an attacker with Agent/Connect permission to execute code on the Jenkins controller. Two companion High-severity findings compound the risk: CVE-2026-70427 (arbitrary file write via unsafe symlink handling in `.tar`/`.tar.gz` extraction) and CVE-2026-70428 (path traversal in file parameters), both of which independently enable writing malicious scripts to `JENKINS_HOME/init.groovy.d/` for controller code execution. All three were responsibly disclosed via the Jenkins Bug Bounty Program (sponsored by the European Commission); no confirmed in-the-wild exploitation has been reported. Jenkins is one of the most widely deployed CI/CD orchestration platforms in enterprise environments, and controller compromise cascades into every pipeline, credential, and deployment target the controller manages.

## Artifact Index
| File | Description |
|---|---|
| 01_Threat_Intelligence.md | Full technical threat intelligence report |
| 02_Risk_Assessment.md | Risk scoring and control gap analysis |
| 03_BIA.md | Business impact analysis |
| 04_Control_Mapping.md | Framework control mapping |
| 05_Executive_Summary.md | Board/CISO-level summary |
| 06_POAM_Remediation.md | Plan of Action & Milestones |

## Key Facts
- **CVE/Advisory ID:** CVE-2026-70426 (primary); CVE-2026-70427, CVE-2026-70428 (companion findings, same advisory)
- **CVSS Score:** 9.0 (Critical, CVE-2026-70426); 7.x-range High for the two companion findings
- **Affected Technology:** Jenkins core (weekly up to 2.575, LTS up to 2.568.1); fixed in Jenkins weekly 2.576 / LTS 2.568.2
- **Frameworks Applied:** NIST CSF 2.0, NIST 800-53 Rev 5, ISO 27001:2022, CIS Controls v8
- **Exploitation Status:** No confirmed in-the-wild exploitation; responsibly disclosed via Jenkins Bug Bounty Program (European Commission-sponsored)
- **Disclosure Date:** 2026-08-05

## Related Cases
No direct prior Jenkins entries in this register. First CI/CD-platform-specific finding logged this quarter; relevant to the same "Container and CI/CD platforms" watch category referenced in the monitoring program's NVD sweep criteria alongside Kubernetes, GitHub Actions, and comparable pipeline orchestration tooling.
