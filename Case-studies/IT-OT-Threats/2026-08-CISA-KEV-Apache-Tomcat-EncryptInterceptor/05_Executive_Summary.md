# Executive Summary
## 2026-08-CISA-KEV-Apache-Tomcat-EncryptInterceptor
**Date:** 2026-08-10 | **Prepared by:** GRC Intelligence Program | **Classification:** Critical

## What Happened
A widely-used web server platform (Apache Tomcat) has a flaw where an earlier security fix accidentally broke a different security feature — the encryption that was supposed to protect traffic between clustered servers silently stopped working. Attackers, reportedly using AI tools to speed up their attack, are actively exploiting this to plant remote-access backdoors on vulnerable servers.

## Why It Matters
Any team that assumed cluster traffic was encrypted because the feature was turned on needs to know that assumption is currently false. Combined with the observed follow-on attack (deploying a backdoor), a successful compromise here can lead to full server takeover, not just eavesdropping.

## What We Are Doing About It
- Patch all Apache Tomcat servers to the fixed version (11.0.21 / 10.1.54 / 9.0.117 depending on branch) immediately (Application/Infrastructure Engineering, target: within 48 hours)
- Verify — don't just assume — that cluster traffic encryption is actually working after patching, via a network traffic check (Security Operations, target: within 3 business days)
- Scan all Tomcat cluster servers for signs of unauthorized remote-access backdoors (Security Operations, target: within 3 business days)
- Segment cluster network traffic so it isn't reachable from untrusted parts of the network regardless of encryption status (Network Engineering, target: within 1 week)

## Bottom Line
This is a case where "we already fixed that" turned out to be wrong because of an unrelated later patch — a good reminder to verify security controls actually work, not just that they're configured. Given the reported use of AI tools by attackers to exploit this quickly, we should treat the patch window as shorter than usual.
