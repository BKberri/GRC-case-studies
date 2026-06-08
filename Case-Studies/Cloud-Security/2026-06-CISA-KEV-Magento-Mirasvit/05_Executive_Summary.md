# Executive Summary
## Magento/Adobe Commerce Extension — Active Attack in Progress (CVE-2026-45247)

**Audience:** CISO / Board | **Date:** 2026-06-08 | **Risk Rating:** Critical

---

**What happened:**
The U.S. government's cybersecurity agency (CISA) confirmed that criminals are actively breaking into online stores right now using a flaw in a popular add-on for Magento and Adobe Commerce — the software platforms many retailers use to run their websites. The attackers don't need a password; they can take full control of a server simply by sending it a malicious request.

**Why it matters:**
Any storefront running this add-on without the fix is exposed to complete takeover today — not hypothetically, but in active, ongoing attacks. The most likely follow-on outcome is theft of customers' payment-card information directly from the checkout page, which carries severe financial penalties from payment-card companies, mandatory forensic investigations, customer-notification costs, and lasting brand damage.

**What we're doing:**
We are updating the affected add-on to the fixed version on every storefront immediately — a same-day action — and, in parallel, searching every server for any sign that an attacker has already gotten in (such as planted malicious files). If we find any such sign, we will immediately activate our incident-response process, including engaging a payment-industry forensic specialist, as required by card-brand rules.

**Bottom line for leadership:**
This is the most urgent item identified this week — active exploitation, no authentication required, and direct exposure of customer payment data. The fix itself takes minutes to apply; the cost of delay is measured in months of recovery and millions in potential losses. We recommend this be treated as a same-day, all-hands patch action, with a forensic sweep completed within 48 hours.
