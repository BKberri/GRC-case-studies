# Executive Summary — F5 BIG-IP APM OAuth Authorization Server RCE (CVE-2026-94127)

**Case Study ID:** CS-CLOUD-2026-09-002 | **Risk Register Entry:** RR-082 | **Date:** 2026-09-28

---

## The Situation

CISA added CVE-2026-94127 to its Known Exploited Vulnerabilities catalog on September 22, 2026, with a three-day remediation deadline. The flaw is a heap-based buffer overflow in F5 BIG-IP's Access Policy Manager module. When APM is configured as an OAuth Authorization Server, an attacker with no credentials and no prior access can send crafted network traffic and execute code on the device. CVSS rates it 9.3, Critical. CISA's inclusion in KEV means this is not a theoretical flaw; it is being actively exploited right now.

BIG-IP APM is the device many organizations place in front of VPN access, single sign-on, and OAuth-based application access. It is the gate, not a room behind the gate. That distinction is what makes this finding serious: a compromised gate does not put one application at risk, it puts every application trusting that gate at risk simultaneously.

One scoping detail matters for how fast this moves internally. F5 confirms the vulnerability applies only to instances configured as an OAuth Authorization Server. Instances used strictly as an OAuth Client or Resource Server are not affected. The first move is not a blanket patch order across every BIG-IP box in the estate; it is a fast inventory to confirm which instances actually carry the Authorization Server configuration, so remediation effort lands where the exposure actually is.

## The Business Risk

An unauthenticated attacker who gets code execution on the authentication chokepoint can forge or intercept OAuth tokens and SSO sessions for every application that trusts it. That is credential theft at the source, not at the edge. It can also serve as a launch point into whatever internal network segment the device bridges.

This program rates the finding Critical: likelihood 5, because CISA's KEV listing confirms active exploitation, not just possibility; impact 5, because the target is the identity infrastructure the rest of the application portfolio depends on. Risk score 25 out of 25. The financial, operational, and reputational exposure scales with how many applications and how much sensitive data sit behind the affected instance, and for regulated environments, this finding lands directly on access-control and authentication compliance obligations, not adjacent to them.

CISA's own remediation deadline, September 25, has already passed as of this report's publication date. For any organization with an unpatched, in-scope instance, that is not a looming deadline anymore. It is a missed one.

## What We Are Doing

- Inventorying every BIG-IP APM instance to confirm which ones have an OAuth Authorization Server profile actually configured, so scope is based on fact rather than assumption.
- Applying F5's hotfix builds to every confirmed in-scope instance, prioritized by network reachability: internet-facing first, internally reachable second.
- Restricting network access to affected virtual servers as an interim compensating control anywhere patching cannot happen within hours.
- Treating OAuth tokens and sessions issued during the exposure window as untrusted and rotating them, since the vulnerability targets the device that issues and validates those tokens.
- Mapping this finding into the framework controls this program tracks: NIST CSF 2.0, NIST 800-53 Rev 5, ISO 27001:2022, and CIS Controls v8, with the specific control gaps and owners documented in the accompanying POA&M.

## What We Need From Leadership

Authorize emergency-change approval for the BIG-IP hotfix deployment outside the standard change window; the standard cycle is too slow for a vulnerability CISA has confirmed is under active exploitation with a deadline that has already elapsed. Confirm ownership for the OAuth Authorization Server inventory task if it is not already assigned, since scoping accuracy determines whether the rest of the remediation effort is well-targeted or wasted on instances that were never exposed. And where in-scope instances cannot be patched within the target window because of operational constraints, we need a documented risk acceptance from the appropriate owner, not silence, since silence is what turns a known, tracked gap into an unmanaged one.
