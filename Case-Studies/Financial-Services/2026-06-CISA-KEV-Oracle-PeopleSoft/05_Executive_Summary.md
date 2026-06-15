# Executive Summary
## Case: CVE-2026-35273 — Oracle PeopleSoft Enterprise PeopleTools Unauthenticated RCE
**Date:** 2026-06-15 | **Prepared by:** Blaise Kingko | **Audience:** CISO, CFO, General Counsel, Board Risk Committee

---

## The Situation

A critical security flaw in Oracle PeopleSoft — the HR and finance software used by thousands of large organizations, universities, and government agencies — was discovered to have been exploited by cybercriminals before Oracle was even aware the flaw existed. Beginning May 27, 2026, a financially motivated hacking group known as ShinyHunters (UNC6240) used this vulnerability to break into PeopleSoft systems, steal sensitive data, and demand ransom payments from victims. CISA added this vulnerability to its list of actively exploited threats on June 12, 2026, and Oracle issued an emergency patch on the same day.

The flaw required no password and no help from any employee to exploit. An attacker on the internet could walk straight into a PeopleSoft system and take it over completely. The severity rating is 9.8 out of 10 — the highest category of risk.

## What's at Stake

PeopleSoft contains some of the most sensitive data in any organization: employee Social Security numbers, salary information, bank account details for direct deposit, health benefits data, and in universities, student records protected by federal law. A successful breach exposes the organization to identity theft claims, regulatory fines, class action lawsuits, and potential SEC disclosure obligations for public companies.

ShinyHunters' documented approach is to steal data and sell it on criminal markets even when victims pay. This means paying a ransom does not prevent data from appearing publicly.

## What We Are Doing

1. All internet-facing access to PeopleSoft has been restricted immediately while the emergency patch is prepared for deployment.
2. Oracle's emergency patch is being prioritized for deployment within the next 72 hours.
3. A threat hunt is underway across PeopleSoft environments to look for signs of compromise during the May 27 – June 9 window when the attack was active but undetected.
4. Legal and compliance teams have been briefed on notification obligations that will activate if compromise is confirmed.

## What Leadership Should Know

- **This is not theoretical.** Organizations are being actively attacked right now.
- **The federal government's remediation deadline is July 3, 2026.** We have set an internal target of June 22, 2026.
- **If we find evidence of compromise,** we are required to notify regulators. The SEC 4-day rule for material incidents, GLBA data breach obligations, and state breach notification laws may apply depending on what data was accessed.
- **Our cyber insurance carrier has been notified** of the active campaign in our sector.

## Decision Required

If the threat hunt identifies indicators of compromise, a decision will be required from the CISO and General Counsel within 24 hours on whether to activate the full incident response plan and engage external forensics support (estimated cost: $200K–$500K for initial IR engagement).

**Current Risk Level: CRITICAL — Active exploitation in sector. Emergency response in progress.**
