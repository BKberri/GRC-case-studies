# POA&M / Remediation Plan, CVE-2026-76504 (Cisco SD-WAN Manager Auth Bypass)

**Case ID:** 2026-10-CISA-KEV-Cisco-SDWAN-HexEncodingBypass

| # | Weakness | Action | Resource | Milestone / Due Date | Status |
|---|---|---|---|---|---|
| 1 | Authentication bypass via hex-encoded URI on SD-WAN Manager (CVE-2026-76504) | Collect admin-tech diagnostic files from every Manager (including cluster members and DR sites) before any upgrade | Network Operations | Within 24 hours | Open, Emergency |
| 2 | Same as above | Upgrade all SD-WAN Manager instances to the first fixed release in their train (20.9.10.1 / 20.12.8.2 / 20.15.6.1 / 20.18.4.1 / 26.1.2.1 / 26.2.1) | Network Operations | Within 72 hours | Open, Emergency |
| 3 | Unknown prior-exploitation exposure | Open Cisco TAC case referencing CVE-2026-76504; submit admin-techs for compromise scanning | Network Operations + Vendor (Cisco TAC) | Concurrent with upgrade | Open |
| 4 | Potential undetected prior access | Review `/var/log/nms/containers/service_proxy/serviceproxy-access.log` and `/var/log/nms/vmanage-server.log` for encoded `j_security_check` requests, particularly against `viptela-reserved-*` service accounts | SOC / IR team | Within 72 hours | Open |
| 5 | Configuration drift during exposure window | Audit current SD-WAN routing/policy configuration against last-known-good baseline post-upgrade | Network Operations | Within 5 business days of upgrade | Planned |
| 6 | Releases earlier than 20.9 train | Plan and execute migration to a supported release train | Network Engineering | Per migration plan (30 days) | Planned |

**Specific Patch Reference:** Fixed releases 20.9.10.1, 20.12.8.2, 20.15.6.1, 20.18.4.1, 26.1.2.1, 26.2.1 per Cisco advisory cisco-sa-sdwan-webauth-xr8beuuU. No workaround exists.

**Owner of Record:** Blaise Kingko (Program POA&M Owner) | **Last Updated:** 2026-10-05
