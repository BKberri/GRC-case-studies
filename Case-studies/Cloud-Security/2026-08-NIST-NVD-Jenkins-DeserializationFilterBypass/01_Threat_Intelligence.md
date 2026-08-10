# Threat Intelligence Report
## 2026-08-NIST-NVD-Jenkins-DeserializationFilterBypass
**Date:** 2026-08-10 | **Source:** Jenkins Security Advisory 2026-08-05 | **Severity:** Critical (primary finding) | **Category:** Cloud-Security

## Executive Overview
Jenkins uses a Remoting library (`agent.jar`/`remoting.jar`) to exchange serialized Java objects between the controller and its build agents. To prevent deserialization attacks, Jenkins enforces the JEP-200 class filter on objects received over a Remoting channel. Jenkins Security Advisory 2026-08-05 disclosed that in Remoting 3384.v60d89463d9e0 and earlier (bundled with Jenkins 2.575 and earlier, LTS 2.568.1 and earlier), a fallback code path in the deserialization implementation is not covered by the JEP-200 filter. Agent processes, code running on an agent, or any attacker holding Agent/Connect permission can exploit this fallback path to execute code on the Jenkins controller using classes on the Jenkins core classpath that are not on the pre-JEP-200 deny list.

## Technical Details
- **CVE ID (primary):** CVE-2026-70426 / SECURITY-3911 — CVSS 3.1: 9.0 (Critical) — AV:N/AC:H/PR:N/UI:N/S:C/C:H/I:H/A:H
- **Companion findings (same advisory, same affected system):**
  - CVE-2026-70427 / SECURITY-3930 (High) — unsafe handling of symbolic links with effectively-empty names during `.tar`/`.tar.gz` extraction allows attackers who control agent processes to write files to arbitrary controller filesystem locations — an incomplete fix of an earlier advisory (SECURITY-3657, 2026-03-18)
  - CVE-2026-70428 / SECURITY-3927 (High) — improper path-traversal identification in file parameter names allows attackers with Item/Configure and Item/Build permission to write files to arbitrary controller filesystem locations
- **Affected Vendor/Product/Version:** Jenkins weekly up to and including 2.575; Jenkins LTS up to and including 2.568.1; fixed in weekly 2.576 / LTS 2.568.2 (Remoting fallback path fix also lands in 2.576/2.568.2)
- **Vulnerability Type:** Deserialization filter bypass (CWE class consistent with unsafe deserialization) for the primary finding; arbitrary file write / path traversal for the two companions — all three converge on the same practical outcome: writing a malicious script to `JENKINS_HOME/init.groovy.d/` or deploying a malicious plugin to `JENKINS_HOME/plugins/`, both of which execute with controller privileges
- **Exploitation Status:** No confirmed in-the-wild exploitation reported. All three issues were responsibly disclosed via the Jenkins Bug Bounty Program, sponsored by the European Commission.
- **Threat Actor Attribution:** Not applicable — responsible disclosure, no attributed threat-actor campaign
- **MITRE ATT&CK Technique IDs:** T1195.002 (Supply Chain Compromise — Compromise Software Supply Chain, applicable given CI/CD controller compromise), T1210 (Exploitation of Remote Services), T1055 (general code-execution-via-deserialization pathway)
- **IOCs:** None published; monitor for unexpected file writes to `JENKINS_HOME/init.groovy.d/` or `JENKINS_HOME/plugins/`, and unexpected agent-to-controller Remoting traffic patterns
- **Remediation Guidance:** Upgrade to Jenkins weekly 2.576 or LTS 2.568.2; a workaround is available for organizations unable to upgrade immediately (published to the jenkinsci-cert/SECURITY-3911-3930 GitHub repository)

## Affected Technology Context
Jenkins controllers are the trust anchor for CI/CD pipelines: they typically hold credentials for source-code repositories, artifact registries, cloud deployment targets, and production infrastructure access. Because all three findings converge on controller-level code execution — and two of the three require only agent-level access or specific item-level permissions rather than full administrative access — this advisory is a meaningful reminder that the traditional trust boundary between "build agent" and "controller" in Jenkins is narrower than many organizations assume. Any environment running untrusted or third-party build agents, or granting broad Item/Configure permissions to development teams, should treat this class of finding as directly relevant to its threat model, independent of whether external attackers can reach the environment at all.

## Intelligence Source Links
- Jenkins Security Advisory 2026-08-05: https://www.jenkins.io/security/advisory/2026-08-05/
- Workaround repository: https://github.com/jenkinsci-cert/SECURITY-3911-3930/
- CyberSecurityNews coverage: https://cybersecuritynews.com/jenkins-code-execution-vulnerability/
- GBHackers coverage: https://gbhackers.com/new-critical-jenkins-vulnerabilities/
- NVD record: https://nvd.nist.gov/vuln/detail/CVE-2026-70426
