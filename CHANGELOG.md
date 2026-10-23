# Changelog

> AI-generated document; see the warning in [README.md](README.md).

## Update 23 – 23 Oct 2026, follow-up to update 22

- **Correction (provenance):** update 22 stated 11:25 UTC, a time not yet reached when it was committed (11:21:09 UTC); status line, changelog header and two range endpoints corrected to recorded times.
- Render added to the PaaS row (Docker-only; customers rebuild). Trend Micro moved in Known gaps from "under investigation" to "affected, fix in development".
- NCSC-NL leads since 22 Oct 22:50 UTC: all 59 added rows reviewed. Adopted after reading the vendor page: Trend Micro, Delta Controls, WP Engine, Elastic Beanstalk, Render. Already covered: Cisco v1.4, Fortinet, F5, SUSE, Synology, Tenable, N-able, Azure App Service, Sophos MyUTM. **Not adopted** (developer tools / small hosting / single apps, outside enterprise scope, not verified): DDEV, Nixpkgs, Server Side Up images, UnoPim, TransIP, phpMyFAQ, Unraid 7.3.4.

## Update 22 – 23 Oct 2026, 11:21 UTC

Re-check of all 110 sources (curl diff 11:09–11:11 UTC, browser-only pages 11:13–11:19 UTC, feeds), plus new vendor statements found via NCSC-NL commits and verified at the vendor.

- **Palo Alto:** PAN-OS hotfix versions with ETAs 26–30 Oct published (none released yet); Panorama and WF-500 still TBD.
- **Trend Micro:** new KA-0024802 – Apex Central, Apex One on-prem, TMWS and Deep Discovery (DDI/DDAN/DDEI) **impacted**, mitigation in development; Apex One SaaS emergency maintenance 23 Oct; long not-impacted list.
- **Delta Controls** (building automation) added: enteliWEB patch for 4.29+, controller firmware patches in development.
- **Red Hat:** EUS/AUS/TUS php:7.4 errata for RHEL 8.4/8.6/8.8 and RHEL 10.0 E2S (RHSA-2026:88532/88533/88565/88561); RHEL 9 php:8.4 and RHEL 7 (109619) still unfixed.
- **Fortinet:** four more products not impacted; new IPS/endpoint/FortiWeb signature IDs.
- **WP Engine:** statement found (all sites patched) – removed from Known gaps.
- Smaller: Imunify360 ruleset 8.88, TuxCare "available now", Laravel Forge 5.6–8.5, Zabbix Docker issue closed, Elastic Beanstalk 4.13.13, Qualys QID 45110 and distro QIDs, CloudLinux `alt-php-internal` note, NCSC-UK wording.
- **Unchanged:** F5, Check Point (fix still due "by October 23, 17:00 GMT"), Citrix, Quest, Sophos, Broadcom, QNAP, Upsun, Kaseya, Siemens, KEV/SSVC/NVD.
- **Still not verified:** Ivanti ICS/EPMM/CSA KBs and Broadcom 39411/39421 (login); Adobe Commerce, Juniper, A10, Nagios, Icinga, Cacti, LibreNMS app (no statement); Sangoma (forum only).

## Update 21 – 23 Oct 2026, 04:16 UTC

- **Tenable Security Center and Tenable Enclave Security** added (section 5): patch SC-202610.1 (22 Oct) updates their bundled PHP to `8.2.35` (TNS-2026-28 / TNS-2026-29). Found in the Tenable FAQ diff of update 20 but missed there.
- **Correction (provenance):** several per-row check minutes in update 20 (README and VERIFICATION) were reconstructed after the fact, and some were out of order (e.g. Acquia/Plesk logged before the KEV batch they followed; CISA/SolarWinds/Kaseya logged after a later batch). All update-20 check times are now the ranges between recorded `date -u` calls (03:45–03:47, 03:47–03:51, 03:51–03:57, 03:57–03:58, 03:59–04:05, 04:05–04:12 UTC). No status claim changed.

## Update 20 – 23 Oct 2026, 04:13 UTC

Full re-check: all 100 previously fetched URLs re-downloaded 03:45–03:47 UTC and diffed against the 22 Oct 20:21 UTC copies, automated claim check re-run, JavaScript/bot-protected pages re-read in headless or headed Chrome (03:53–04:12 UTC), feeds re-queried; rows without a README link (Progress KBs, Ivanti KB, Arch, Cacti, LibreNMS, F5 signatures, Qualys, Upsun) re-checked separately. Then a deeper search for vendors without a statement: vendor portals and status pages (Juniper, A10, Siemens, Adobe, WP Engine, Sangoma/FreePBX, Broadcom, Ivanti), NCSC-NL commits since 22 Oct 15:04 UTC, web search as leads only.

**Status changes**
- **Cisco v1.4** (22 Oct 23:00 GMT): first products **vulnerable**: Expressway / Expressway Select (fix 15.5.21, TBD) and URWB (fix 27.1.1, Feb 2027, admin auth required). Many products moved to not vulnerable (ISE, Hypershield, ASA/FMC/FTD, IOS/XE/XR/NX-OS, …); 9 still under investigation. Splunk has its own advisory SVD-2026-1013 (no product known affected).
- **Broadcom Enterprise Security Group** (new): **Carbon Black App Control Server and Symantec Endpoint Protection Manager affected** (notification 39404; detail advisories login-gated).
- **Palo Alto**: WildFire WF-500 / WF-500-B affected (ETA TBD); WildFire Cloud remediated 22 Oct; XDR Broker VM, XCORE, Strata Cloud Manager not affected.
- **Check Point** (SK modified 23 Oct): new note "permanent fix … by October 23, 17:00 GMT"; the Solution field still says 11 Nov; the automatic-mitigation announcement was removed without a release confirmation.
- **Red Hat**: RHEL 7 not affected by 109618, affected by 109619 (no fix yet); RHEL 6 affected, out of support scope (was: under investigation).
- **SUSE**: SLES 16.0 fixed (`8.4.27-160000.1.1`); 16.1 affected; new SLES 12 php74 fix (`7.4.33-1.74.1`).
- **F5** (23 Oct): BIG-IP Next CNF not vulnerable; EOB and API Security LE added as not vulnerable; only AI Gateway still researching.
- **Ivanti**: Ivanti-employee forum answers: EPMM/Sentry and vTM/Services Director not affected; **Cloud Services Application needs a PHP update**; AOD WAF signature updates may be interrupted.
- **Barracuda**: Message Archiver not affected. **Quest**: SMA 15.0 CU5 / 15.1 CU2 in QA. **Citrix**: NetScaler WAF signature v186. **Siemens**: ProductCERT statement (evaluating). **Acquia**: incident resolved. **AWS**: WorkMail done, Beanstalk 8.2–8.5 fixed, AWS WAF PHP Managed Rule Group. **CloudLinux**: alt-php builds with PHP.net version numbers in stable.
- New rows: SolarWinds (Pingdom, compensating controls), Kaseya (investigating), TuxCare ELS (closes a known gap), LibreNMS Docker 26.10.2-r1, Fastly Next-Gen WAF virtual patch, Broadcom/Symantec detections, Corelight, Vercel WAF, Citrix WAF; Trend Micro TippingPoint filter 48534; Qualys QIDs 520310 and 389120; Splunk ESCU; CISA alert.
- Key facts: exploitation bullet rebalanced (Rapid7: no ITW observed, only attempts; Sansec: public exploits do not work against a default PHP installation; CISA: none observed at publication).

**Corrections**
- Amazon Threat Intelligence changed its wording from "is now being broadly exploited" to "is now seeing broad exploitation attempts in the wild"; quote updated.
- The Ivanti EPMM statement was posted by an Ivanti employee, not a community member.
- Upsun link pointed to the status home page, which no longer shows the incident; replaced with the incident permalink.

**Still not verified**: Ivanti Connect Secure / EPMM / CSA KBs and Broadcom advisories 39411 / 39421 (login), WP Engine, Adobe Commerce, Sangoma (forum only). No statement: Juniper, A10, Nagios, Icinga, Cacti, LibreNMS app.

## Update 19 – 22 Oct 2026, 21:02 UTC

- Check Point sk1000302 re-read at 21:02 UTC, after the announced deadline: the automatic mitigation is still announced in the future tense ("will release … before October, 22, 2026 at 21:00 GMT"), no confirmation of release; last modified 2026-10-22. Manual mitigation remains the documented option until Check Point confirms

## Update 18 – 22 Oct 2026, 20:33 UTC

Full re-check of all 93 linked sources (20:21–20:33 UTC) with an automated claim check (each row's key strings searched in the fresh source text), plus a new search for vendor statements (NCSC-NL commits since 11:00 UTC, web search, vendor support portals).

- **New vendor statements:** **HPE ClearPass affected** (HPESBNW05171; 6.14.1 / 6.11.16 only partial fix, full fix in development); **SonicWall** product notice (no PHP in SonicOS, SMA 1000, NSM, ES, CSE, UM, WNM; switches/APs under evaluation); **N-able** (Take Control, N-sight, Mail Assure, Passportal patched; rest not affected); **Zscaler** ruled out impact on production; Synology press statement (affected packages list, DSM internal PHP patch later); Laravel Cloud/Forge/Vapor, Kinsta added; FreePBX (forum only)
- **Changed:** watchTowr now reports observed in-the-wild exploitation (not only attempts); Cloudflare rules renamed ("PHP Remote Code Execution Attack" #1–#7); Google revised Cloud Armor guidance (File Upload + RFI categories, oversized-body rule); Fedora 43 fixed; Pantheon "persistent but limited probing"
- **Unchanged (verified):** Red Hat, AlmaLinux, Rocky, Oracle, SUSE, Ubuntu, Debian/ELTS, Amazon, Alpine, Remi, Plesk (upd. 17:44 UTC, same content), cPanel, DirectAdmin, CloudLinux, F5, PAN, Cisco, Fortinet, Barracuda, Sophos, Trend, WatchGuard, Netgate, OPNsense, KACE, Citrix (fix 27 Oct), QNAP, Broadcom, Progress, Akamai, Imperva, Azure, AWS, Checkmk, Zabbix, Centreon, GLPI, BSI, CERT-EU, CCCS, KEV, SSVC, NVD
- Correction: HPE moved out of "nothing found"; SonicWall's PSIRT list was the wrong place to look (statement is a support notice)

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
