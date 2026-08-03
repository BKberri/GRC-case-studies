# Executive Summary
## 2026-08-CISA-KEV-Cisco-FMC-HardcodedPassword
**Date:** 2026-08-03 | **Prepared by:** GRC Intelligence Program | **Classification:** High

## What Happened
The vendor platform we use to centrally manage our firewalls was shipped with a built-in, undocumented login account. Attackers are actively using this account right now to gain unauthorized access to firewall management systems industry-wide.

## Why It Matters
Even though this account has limited privileges on its own, it exposes our firewall rules, network layout, and security event history to anyone who uses it — information that materially helps an attacker plan a bigger attack. The vendor has also confirmed it can be combined with other flaws to gain full administrative control.

## What We Are Doing About It
- Apply the vendor's security patch to all affected firewall management systems immediately (Network Engineering, target: within 48 hours)
- Rotate all credentials, certificates, and keys managed by the affected system out of caution (IT Operations, target: concurrent with patching)
- Review recent firewall policy change history for any unauthorized modifications (Security Operations, target: within 3 business days)
- Enable enhanced monitoring of administrative logins to the management platform going forward (Security Operations, target: within 5 business days)

## Bottom Line
This is a vendor-introduced credential weakness, not something we could have prevented through our own controls — but the response speed matters: the longer this stays unpatched, the more attackers with access can learn about how our network is segmented.
