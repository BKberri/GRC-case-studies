# Executive Summary, FortiMail Email Gateway Backdoor (CVE-2026-104286)

**Case ID:** 2026-10-CISA-KEV-FortiMail-PathTraversal | **Audience:** CISO / Board

## What Happened

Attackers are actively breaking into Fortinet's FortiMail email security product, the system many organizations use to filter and protect their email, using a flaw that requires no password. There is currently **no fix available from Fortinet**; only a temporary workaround exists.

## Why It Matters

If your organization runs FortiMail and it is reachable from the internet (the normal configuration for a mail gateway), an attacker can plant a permanent backdoor and begin reading or manipulating company email without needing any credentials. This is comparable to someone gaining a hidden copy of every piece of mail that passes through your front desk.

## What We're Doing

1. Confirming whether FortiMail is in use and, if so, its exposure to the internet.
2. Applying Fortinet's interim workaround immediately (disabling the vulnerable feature and removing direct internet access to the management interface) rather than waiting for a patch.
3. Reviewing recent mail-gateway logs for signs the backdoor may already have been planted.

## Business Risk in Plain Terms

A compromised mail gateway is a compromised front door to the business, it can expose password resets, confidential negotiations, and customer/vendor correspondence, and can be used to launch convincing fraud (invoice redirection, executive impersonation) against the people we do business with.

## Recommended Executive Action

Approve emergency change-control authority to apply the workaround outside the normal patch window, given the absence of a vendor fix and confirmed active exploitation.
