# Changelog

> AI-generated document; see the warning in [README.md](README.md).

## Update 13 – 22 Oct 2026, 10:20 UTC

- **Linux section restored to one row per release** (Distribution / PHP / Status / Fix type) and all package versions put in code formatting. The Debian row was broken: GitHub rendered the text between the `~` in `8.4.27-1~deb13u1` … `8.2.35-1~deb12u1` as strikethrough
- **New section 5 "Monitoring and IT automation"**: Checkmk (Werk #19262, Docker image and appliance 1.7.25 fixed), Zabbix (Docker `*-latest` rebuilt; pinned tags may still ship PHP 8.5.11), Centreon (notice: PHP comes from the OS), GLPI (host PHP must be patched; Cloud patched), Nagios XI/Core, Icinga Web 2, Cacti, LibreNMS (no statement); Ansible/AWX/AAP, Rundeck and Semaphore contain no PHP
- **Status changes since update 12:** Fortinet moved FortiClient EMS (and more products) to "not impacted"; Oracle Linux 8 fixed (ELSA-2026-87080); HestiaCP released fixed hestia-php; F5 lists APM/SSLO additionally under Configuration utility (7.5); Alpine statuses verified from pkgs.alpinelinux.org (3.24 fixed, 3.23 partly, 3.22 not); CloudLinux post now contradicts its earlier version
- Unchanged at 10:10 UTC: CISA KEV (not listed), CISA SSVC, Red Hat VEX rev 3, Palo Alto (no fixes), Cisco v1.1, Citrix (notice only), SUSE, Debian, Ubuntu, Rocky, CIQ, Amazon, AWS bulletin, Docker Official Image

## Update 12 – 22 Oct 2026, 06:32 UTC

- **Enterprise focus:** new sections for WAF/IPS/scanner content, cloud platforms and government advisories; hosting panels, NAS and hobby distros condensed into section 5
- **Exploitation status rewritten** from primary sources (Amazon: first attempt 17 Oct, broad exploitation; Cloudflare: attack traffic observed). CISA KEV/SSVC, NVD and the BSI notice added
- **New vendors / platforms:** Citrix (portal notice), Ivanti (login-gated KB), WatchGuard (not affected), Zscaler (assessing), Siemens, Microsoft Azure WAF, Imperva, Cloudflare, AWS WAF, Cloud Armor, Tenable/Qualys/Rapid7; Freexian ELTS fixes
- **Palo Alto:** added PAN's own scoring (CVSS-B 8.7, availability only) and scope (mgmt UI/XML API only)
- **Red Hat:** status now from the official CSAF VEX; added RHSA-2026:87073 (RHEL 8 php:8.2) and :87414 (Hardened Images); RHEL 9 php:8.4 affected without fix
- **Rocky Linux community fixed** (RLSAs from 22 Oct ~00:05 UTC). The earlier "pending" status applied only to CIQ RLC Pro
- **Own errors from update 11 corrected:**
  - SUSE patch name `…-2026-4844` from the original PDF was correct and is restored
  - The PDF's "minimal source backports for 7.4, 8.0, 8.1" was correct (CERT-EU)
  - Unit 42 only reports PoC, not exploitation in the wild
  - Wrong check timestamps fixed
  - Unverified DirectAdmin "7.3 and older not patched" removed

## Update 11 – 22 Oct 2026, approx. 06:05 UTC

- Added Netgate pfSense, OPNsense, Trend Micro, QNAP, Synology, hosting panels (Plesk, cPanel, DirectAdmin, HestiaCP, ISPConfig, CloudLinux/TuxCare), Docker Official Images, AWS, Google Cloud, Azure, Amazon Linux, Oracle Linux, Alpine, Arch, sury.org
- RHEL 10 and RHEL 9 default stream marked fixed (were "not found yet" in update 10)
- F5 verified via browser, Plesk via the Zendesk API
- Note: several "corrections" in this update were based on tool-generated summaries and were reverted in update 12

## Update 10 (initial publication) – 22 Oct 2026

- Converted from the original PDF status snapshot (approx. 05:30 UTC) to Markdown, marked as AI-generated
- Corrected the truncated CVE ID in the verification command, the Debian package example, the Rocky/CIQ status and the Fortinet virtual-patch note; repaired broken links
