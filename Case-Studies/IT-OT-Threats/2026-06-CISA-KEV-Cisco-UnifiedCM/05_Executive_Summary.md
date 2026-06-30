# Executive Summary — Cisco Unified Communications Manager Static Credential Flaw (CVE-2026-20384)

## What Happened
A hidden, built-in password in Cisco's enterprise phone/call-control system was discovered and is being actively exploited, letting attackers take full control of the system without needing a legitimate account.

## Why It Matters
If we use Cisco Unified Communications Manager for company phone systems, this flaw could let an attacker listen in on calls, redirect calls, or take our phone system offline entirely — including potential impact to call centers handling customer data.

## What We're Doing
We are applying Cisco's patch to remove the hidden credential, reviewing call logs for any signs of unauthorized access, and restricting management access to trusted internal networks.

## Recommended Executive Actions
1. **Apply Cisco's security patch** to all Unified CM clusters — Owner: IT/Telecom Engineering — Target: within the federal 3-day deadline.
2. **Review authentication and call logs** for signs of unauthorized access during the exposure window — Owner: Security Operations — Target: this week.
3. **Determine if any call interception occurred** involving regulated customer data (payment, health) — Owner: Legal/Compliance — Target: this week.
4. **Restrict Unified CM management access** to internal/VPN networks only — Owner: Network Engineering — Target: 48 hours.
