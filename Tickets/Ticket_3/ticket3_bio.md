# Ticket #3 — Controlled Network Troubleshooting Simulation

**Status:** Resolved
**Priority:** High
**Category:** Network / Connectivity
**System:** Windows VM (UTM)
**Scenario:** Controlled troubleshooting simulation

## Issue

User reported that most websites were working, but one specific website would not load.

## Troubleshooting

1. Ran `ipconfig` to check the system's network configuration.

   * IPv4 address, subnet mask, and default gateway were present.

2. Pinged the default gateway.

   * Successful. This confirmed the computer could communicate with the local network.

3. Pinged `8.8.8.8`.

   * Successful. This confirmed Internet connectivity was working.

4. Ran `nslookup example.com`.

   * Successful. DNS was working for other domains.

5. Tested the affected website in Microsoft Edge.

   * Website failed to load while other websites continued to work.

6. Ran `nslookup` on the affected website.

   * The domain was resolving to an incorrect address.

7. Ran:
   `ipconfig /flushdns`

   * DNS cache was cleared, but the website still failed to load.

8. Checked the system's DNS configuration.

   * Found that the DNS configuration was returning an incorrect address for the affected website.

9. Corrected the DNS configuration.

10. Ran `nslookup` again.

    * The affected website now resolved to the expected address.

11. Opened the website in Edge again.

    * Website loaded successfully.

## Root Cause

Incorrect DNS configuration caused the affected website's domain name to resolve to the wrong address.

## Resolution

Corrected the DNS configuration and cleared the DNS cache.
