# Executive Summary — Joomla Website Plugin Vulnerabilities (4 Critical Flaws)

## What Happened
In a single week, four different, unrelated add-on components for Joomla — a popular website-building platform — were each found to have the same kind of critical flaw: an attacker with no login can upload a malicious file and take over the website. All four are already being actively exploited.

## Why It Matters
These add-ons are commonly used for things like page design, event registration, and website contact forms — meaning any public-facing Joomla site using one of them could be silently taken over, used to host malware, or defaced. The fact that four separate, unconnected plugins had the identical flaw in the same week suggests attackers (or researchers) are actively hunting for this exact weakness across many Joomla add-ons — not just these four.

## What We're Doing
We are identifying every Joomla website in our environment and cataloging which add-on components are installed, patching the four affected components immediately, and scanning for signs that any site was already compromised.

## Recommended Executive Actions
1. **Identify every Joomla website and its installed add-on components** — Owner: Web/IT Operations — Target: within 48 hours.
2. **Patch SP Page Builder, Joomlack Page Builder, iCagenda, and Balbooa Forms wherever installed** — Owner: Web/IT Operations — Target: 2026-07-10 to 2026-07-13 (staggered federal deadlines).
3. **Scan all Joomla sites for unauthorized files, regardless of which add-ons are installed** — Owner: Security Operations — Target: this week.
4. **Commission a full add-on/extension inventory across all Joomla sites as a standing control** — Owner: Web/IT Operations — Target: next 30 days.
