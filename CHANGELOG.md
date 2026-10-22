# Changelog

> AI-generated document; see the warning in [README.md](README.md).

## Update 17 – 22 Oct 2026, 20:19 UTC

Completes the re-check: update 16 had skipped section 2 (WAF/IPS/scanners), BSI and several stable rows. All of them are now re-read; fast-moving sources checked again around 20:15 UTC.

- **New since update 16:** Citrix plans NetScaler fixes for **27 Oct 2026**; CloudLinux native OS php now **fixed in stable for every affected version** (19:50 UTC); Fortinet moved FortiADC, FortiADC Manager, FortiEndpoint, FortiSIEM, FortiMonitor to *not impacted*; Barracuda moved WAF/ADC, WaaS, Vulnerability Manager to *not affected* and added Firewall Insights, Message Archiver; Pantheon resolved, Acquia restored all services; Fedora 43/45 builds in testing
- **Key facts:** public PoCs exist (Rapid7: multiple, none broadly reliable; BSI v1.2: PoC public; CCCS; Imunify360: exploit tool requests reached 3,600+ servers by 21 Oct 11:00 UTC). Still not in KEV, SSVC still "none"
- **Corrections:** BSI notice is BITS-H 2026-297981-1232 v1.2 (was given as …-1132 v1.1); A10 latest advisory is from 30 Sep 2025 (not Mar 2025); Progress WS_FTP article no longer mentions exposed older versions; Qualys QID 5019895 no longer listed; Talos SIDs 67359/67360/67375 all in Community Ruleset; Imunify360 row now sourced (it had no provenance entry) and notes that no rule covers the OOM path yet
- **Verified now:** sury php8.0 `8.0.30-25` changelog contains the backport; Progress LoadMaster KB 000307378; DirectAdmin note on PHP 8.1 build failures
- Check Point's automatic mitigation is announced for before 22 Oct 21:00 GMT; not yet re-checked after that time

## Update 16 – 22 Oct 2026, 15:33 UTC

Re-sweep of sections 1 and 3–7 (section 2 WAF/IPS content and BSI not re-read), focused on vendors without a statement. Method change: searched each vendor's **support/KB portal for the CVE ID**, not only PSIRT/advisory indexes; used the NCSC-NL list as a lead source.

- **Newly found vendor statements (previously "no statement"):** Citrix NetScaler **affected** (Tech Zone post by NetScaler Product Security; NSIP/SNIP/Cluster IP GUI, no fix yet); **Quest KACE** SMA/SDA **affected** (KB 4385046, no patch); **QNAP** QSA-26-18 **affected**, fixing; **Synology** SA-26:14 **resolved** (PHP 7.3 no fix); **Broadcom/VMware** KB 459989: VCF not affected; **Ivanti** Service Manager / Neurons ITSM/ITAM not impacted (KB 000109782); **Azure App Service** Linux images patched (Standard/Latest channels); **Zabbix** statement pr912
- **Corrections:** Ivanti "Assessment-and-…" article was about Apache Tomcat, not PHP; Icinga: NCSC-NL's cited post does not mention the CVEs; HPE community reply is a personal post, not an official statement
- **Updated:** Cisco v1.2 (Meraki, Splunk added under investigation; BPA, CPS, PCF, SMI not vulnerable); Fortinet (FortiPortal not impacted, FortiGuard dropped, OT IPS refs); Sophos v4 (IPS signatures); Trend (exposure tool); Checkmk 2.3.0p51; Rocky RL8 php:8.2 (RLSA-2026:87073); Oracle Linux 9 php:8.2/8.3 and OL8 php:8.2; Alpine 3.22/3.23 all fixed; HestiaCP bullseye; KEV/SSVC unchanged; NCSC-NL last commit
- **Added:** PHP PaaS row (Pantheon, Upsun, Acquia, Heroku, Scalingo), Nextcloud (AIO v14.4.1), ISPConfig, aaPanel, Gentoo GLSA 202610-02
- **Not verified:** Ivanti Connect Secure KB (login), WP Engine (JS-only status page), Adobe Commerce (no Adobe statement found)

## Update 15 – 22 Oct 2026, 15:16 UTC

- **Check Point: correction.** The row said "No product statement"; Check Point published [sk1000302](https://support.checkpoint.com/results/sk/sk1000302) on 21 Oct in its support KB (not on the IPS advisory site that was checked). Firewall web portals (Mobile Access, SNX, SAML Remote Access, Identity Awareness Captive Portal) on R80–R82.20 and Spark are **affected**; fix planned for 11 Nov 2026; automatic mitigation announced for before 22 Oct 21:00 GMT; manual `cp-httpd.conf` mitigation documented
- **SUSE:** SLES 15 SP4/SP5/SP6 LTSS, SLES for SAP 15 SP4–SP7 and HPC LTSS/ESPOS are now fixed (patches 4843, 4852, 4853); SP7 php7 (Legacy module) fixed. Row "SP4–SP6 incl. LTSS: no fix" was outdated
- **CloudLinux: correction.** "Fixed" applied only to alt-php/ea-php. Native OS php is only partly in stable (status-page correction 22 Oct 09:21 UTC); the row is now split
- Next: full re-sweep of every row without a vendor statement (update 16)

## Update 14 – 22 Oct 2026, 11:15 UTC

- Previously blocked vendor pages read with a headed browser: **Sophos** advisory verified (v3; adds the 11 Aug first-report date, the 1 Aug look-back recommendation and the PHP 8.5 `fatal_error_backtraces=0` mitigation), **Barracuda** advisory added (product table), **Progress** KB statements added (LoadMaster, MOVEit, WS_FTP), **Akamai** WAF rule 3000991 added, **Broadcom/VMware** and **A10** checked (no advisory)
- **CloudLinux contradiction resolved:** the KB article (updated 22 Oct) confirms all fixed alt-php/ea-php builds are in the stable repos since approx. 01:00 UTC 22 Oct; the blog post is outdated
- Zabbix forum: only community posts, no vendor statement
- Known gaps reduced to Ivanti KB, Azure App Service, QNAP/Synology, TuxCare ELS details

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
