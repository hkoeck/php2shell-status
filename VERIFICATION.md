# Verification log

> AI-generated. Each row: the claim used in README.md, its source, when it was checked (UTC, 22 Oct 2026), how (raw = curl + HTML-to-text, browser = Playwright innerText, JSON = machine-readable feed), and the exact evidence. Rows marked **not verified** could not be read from the primary source.

## Claims

| Claim | Source | Checked (UTC) | Method | Evidence (verbatim / exact) |
|---|---|---|---|---|
| Fixed 8.2.35/8.3.36/8.4.27/8.5.12; affected < these | GHSA-w8hw-w9fx-j79w, GHSA-6wmf-4rv5-p3rp | 2026-10-22 06:13 | raw HTML | "Affected versions < 8.2.35 < 8.3.36 < 8.4.27 < 8.5.12" |
| CVSS v4 9.2, vector | GHSA / NVD API | 06:13 | raw / JSON | `CVSS:4.0/AV:N/AC:H/AT:P/PR:N/UI:N/VC:H/VI:H/VA:H/SC:N/SI:N/SA:N`, 9.2 |
| NVD CVSS 3.1 9.8 (both CVEs) | NVD API 2.0 | 06:14 | JSON | `nvd@nist.gov Primary 3.1 9.8` |
| Not in CISA KEV | CISA KEV JSON (catalog 2026.10.21, released 2026-10-21T14:04Z) | 06:14 | JSON | no entry for CVE-2026-109618/109619 |
| CISA SSVC Exploitation: none | CVE record, CISA-ADP | 06:14 | JSON | `{"Exploitation":"none"},{"Automatable":"no"},{"Technical Impact":"total"}` @ 2026-10-21T14:34Z |
| mod_php confirmed; FPM exits child on startup failure; FrankenPHP likely; LSAPI app-specific | GHSA-w8hw | 06:13 | raw | "Complete remote code execution was validated over HTTP against mod_php…" |
| 109619 session lifecycle RCE validated on mod_php and FPM | GHSA-6wmf | 06:13 | raw | "Session lifecycle RCE was validated against mod_php and FPM." |
| Minimal source backports for 7.4/8.0/8.1 from PHP team | CERT-EU 2026-018; CIQ KB | 06:13 | raw | "the PHP security team has also published minimal source backports for PHP 7.4, 8.0 and 8.1" |
| Unit 42: PoC seen, not ITW | Unit 42 brief | 06:13 | raw | "Unit 42 has seen proof of concept of these vulnerabilities. At least one European government has taken its website offline as a precaution." |
| Talos: no ITW as of 21 Oct 14:00 UTC; SIDs 67359, 67360 (+67375 subscribers) | Talos blog | 06:13 | raw | "has not seen them being exploited in the wild yet (as of October 21, 2026 14:00 UTC…)"; "SNORT® SIDs … 67359, 67360, 67375" |
| watchTowr: active exploitation attempts | watchTowr | 06:13 | raw | see grep |
| Check Point: none ITW at publication, not in KEV; CPAI-2026-15172; CPAI-2021-0286 | CP blog / advisory | 06:13 | raw | "Exploitation: None reported in the wild so far, and the flaws are not listed in CISA's Known Exploited Vulnerabilities catalog." |
| Cisco v1.1 interim, first 21 Oct 19:12 GMT, upd 22 Oct 01:24 GMT; no product vulnerable; Umbrella in both lists | Cisco advisory | 06:13 | raw | lists verbatim |
| Fortinet PSIRT "Virtual Patch: No"; TS 6551 "virtual patches … version 37.316" | FG-IR-26-186, TS 6551 | 06:13 | raw | verbatim |
| SUSE patchname SUSE-SLE-Module-Web-Scripting-15-SP7-2026-4844; php8 8.3.36-150700.3.24.1; 16.0 8.4.27-160000.1.1 in QA; php7 on 15 SP7 Affected; page modified 21 Oct 20:57 | SUSE CVE page | 06:13 | raw | verbatim |
| Red Hat per-stream status | Red Hat CSAF VEX rev 3 (2026-10-22T05:04Z) | 06:14 | JSON | RHSA-2026:87070/87071/87072/87073/87079/87080/87151/87414; RHEL 9 php:8.4 "Affected / none_available"; RHEL 6/7 under_investigation |
| Rocky community RLSAs | apollo.build.resf.org API | 06:20 | JSON | RLSA-2026:87070/87071 (RL10), 87072/87079/87151 (RL9), 87080 (RL8), published 2026-10-22 00:01–00:08Z |
| CIQ RLC Pro: LTS 9.2/9.6 available, rest pending | CIQ KB | 06:13 | raw | table verbatim |
| Debian | security-tracker | 06:13 | raw | bookworm (security) 8.2.35-1\~deb12u1 fixed DLA-4848-1; trixie (security) 8.4.27-1\~deb13u1 DSA-6574-1; forky 8.4.26-1 vulnerable; sid 8.4.27-1 fixed |
| Ubuntu | USN-8948-1/-2, CVE page | 06:13 | raw | versions verbatim; priority "Critical" |
| Oracle Linux | linux.oracle.com CVE page | 06:13 | raw | ELSA-2026-87070 (OL10 php), -87071 (OL10 php8.4), -87151 (OL9 php), 2026-10-21 |
| Amazon Linux | ALAS explore | 06:13 | raw | ALAS2PHP8.2-2026-015; ALAS2023-2026-3301..3304; ALAS2027-2026-243; "No Fix Planned" ×2 |
| AlmaLinux | blog | 06:13 | raw | versions verbatim; production 2026-10-21 21:15 UTC |
| Amazon: first attempt 17 Oct; broad exploitation | AWS Security Blog (CJ Moses, 21 OCT 2026) | 06:16 | raw | "PHP2Shell exploitation attempt dating to Oct. 17, 2026, in MadPot telemetry"; "PHP2Shell is now being broadly exploited in the wild."; "investigate from at least starting on October 17th" |
| Cloudflare: attack traffic observed; rules from 21 Oct 03:02 UTC; all plans | Cloudflare blog | 06:18 | raw | "we observed attack traffic targeting our customers"; "available and deployed automatically on all plans with WAF deployed, including Free users" |
| Imperva: Cloud WAF protected OOTB; no matching traffic pre-disclosure | Imperva blog | 06:19 | raw | "Cloud WAF customers are protected against this vulnerability out of the box." |
| Azure WAF rule 99006001, disabled by default, rollout until 28 Oct | Microsoft Tech Community (21 Oct, v11.0) | 06:15 | raw | "Rule ID: 99006001"; "Default state: disabled"; "expected to complete by 28 October 2026" |
| Azure App Service: no MS statement | Microsoft Q&A question 6045369 | 06:15 | raw | customer question, no Microsoft answer in page |
| AWS services | AWS bulletin 2026-143 (last upd. 10/21/2026 20:30 PDT) | 06:13 | raw | Beanstalk v4.13.12; Lightsail; WorkMail; WAF SizeRestrictions_BODY |
| Google Cloud | GCP blog (upd. 21 Oct 16:25 PDT) | 06:13 | raw | App Engine Standard auto; Flexible/Cloud Run/GKE redeploy; Cloud Armor managed rules |
| PAN CVSS-B 8.7 availability-only; mgmt UI + XML API only | PAN advisory | 06:13 | raw | "CVSS-B: 8.7 (CVSS:4.0/AV:N/AC:L/AT:N/PR:N/UI:N/VC:N/VI:N/VA:H/…)"; "strictly affects the management web interface, which includes the HTTPS web UI and XML API service" |
| F5 K000163821 | my.f5.com (Playwright innerText) | 06:24 | browser | "Published Date: Oct 21, 2026Updated Date: Oct 22, 2026"; tables verbatim; sigs 200103697/200204115/200204113 |
| Citrix notice | support.citrix.com (Playwright) | 06:21 | browser | "Citrix is working to update PHP used by NetScaler management interfaces to address CVE-2026-109618 and CVE-2026-109619." |
| Ivanti | hub.ivanti.com search (Playwright) | 06:22 | browser | KB "Assessment-and-…" referenced, login-gated; forum questions on CSA 5.0.7 / Connect Secure / EPMM |
| Juniper | supportportal search (Playwright) | 06:22 | browser | no JSA matching CVE-2026-109618 |
| Broadcom/VMware | support.broadcom.com | 06:22 | browser | blocked by bot check (403) — not verifiable |
| Akamai blog | akamai.com | 06:23 | curl + browser | 403 Access Denied — not verifiable |
| Sophos advisory | sophos.com | 06:13–06:25 | curl + browser | unreachable (timeout / HTTP2 error); content only from an earlier summary |
| WatchGuard WGSA-2026-0032 | psirt.watchguard.com | 06:19 | raw | "WatchGuard's initial assessment is that none of our products are affected by this vulnerability." |
| Zscaler | ThreatLabz blog | 06:24 | raw | "Zscaler is assessing the potential impact on its products in the Trust post." |
| Siemens | ProductCERT CSAF feed | 06:20 | JSON | feed updated 2026-10-19, no PHP entry; SSA-104023 title "Multiple Vulnerabilities in Palo Alto Networks PAN-OS on RUGGEDCOM APE1808 Devices" |
| Trend Micro KA-0024789 | Trend success portal | 06:13 | raw | rules 1012749 / filter 48514 / rule 6021; "urgent assessment"; "Last updated: 2026/10/22" |
| Netgate | blog | 06:13 | raw | versions verbatim; "cannot be performed using the pfSense software PHP GUI or the Nexus GUI" |
| OPNsense | forum | 06:13 | raw | "Community Edition 26.7.7: PHP 8.5.12"; "Business Edition 26.4.2p3: PHP 8.3.36" |
| Plesk KB | Zendesk API JSON | 06:17 | JSON | updated_at 2026-10-22T05:29:18Z; tables verbatim |
| cPanel EA4 25.91 | docs.cpanel.net changelog | 06:13 | raw | EA-13607…13613 entries verbatim |
| DirectAdmin | forum thread p.3 | 06:25 | raw | "bump PHP 8.5, 8.4, 8.3, 8.2 to latest version, and adds patches for PHP 8.1, PHP 8.0 and PHP 7.4" |
| HestiaCP | GitHub issue #5817 | 06:25 | raw | "HestiCP control panel bundled php (hestia-php) is still vulnerable." |
| CloudLinux | blog (TL;DR 22 Oct 06:00 UTC) | 06:13 | raw | ea-php52–85 fixed; rulesets 8.83 (09:08 UTC) / 8.84 (13:07) / 8.85 (17:17) |
| Remi EL8/9/10 | repoview | 06:24 | raw | 8.5.12-1 … 7.4.33-31 per EL |
| Freexian ELTS | deb.freexian.com tracker | 06:24 | raw | ELA-1853-1/1854-1/1855-1; bullseye 7.4.33-1+deb11u14 fixed |
| Docker Official php | Docker Hub API + docker-library versions.json | 06:30 | JSON | 8.5-fpm 2026-10-21T18:58Z … 8.4-fpm 22:07Z; versions 8.2.35/8.3.36/8.4.27/8.5.12 |
| Arch | Arch JSON API | 06:30 | JSON | php 8.5.12-1, last_update 2026-10-21T13:50Z |
| sury.org | trixie Packages index + .deb changelogs (php7.4-common, php8.1-common) | 06:30–06:31 | raw | "Backported from 8.2.35 + [CVE-2026-109618, CVE-2026-109619]: Avoid state corruption via bailout." |
| Tenable | blog | 06:15 | raw | plugin 369483; WAS 115719–115722 |
| Qualys | blog | 06:15 | raw | QIDs 5019895, 5019896, 389102, 39033, 6056502, … |
| Rapid7 | blog | 06:15 | raw | "remote unauthenticated vulnerability checks now available in a dedicated release" |
| BSI | BITS-H 2026-297981-1132 v1.1 (PDF) | 06:23 | pdftotext | "Zum aktuellen Zeitpunkt sind noch keine bestätigten Ausnutzungen der Schwachstellen bekannt" |
| CCCS AL26-026 | cyber.gc.ca | 06:15 | raw | "no active exploitation being identified at this time" |
| NCSC-UK | ncsc.gov.uk news | 06:15 | raw | "Published 21 October 2026" |
| NCSC-NL list | GitHub | 06:19 | git API | last commit 2026-10-21T21:40:13Z |
| Fedora | Bodhi JSON | 06:30 | JSON | FEDORA-2026-a9eba4bbc3 stable 2026-10-21 16:43:43, php-8.5.12-1.fc44, security/high |
| HPE | HPESBNW05159 (Playwright) | 06:31 | browser | "Release Date: 2026-10-15"; AOS-8/AOS-10 advance notice, unrelated to PHP |
| SonicWall | PSIRT vuln-list (Playwright) | 06:31 | browser | no PHP entry; latest SNWLID-2026-0018 (2026-10-14) |
| A10 / Barracuda / Progress | vendor pages | 06:19–06:31 | raw | lists not rendered / no PHP hit — **not verified** |


## Update 13 checks (22 Oct 2026)

| Claim | Source | Checked (UTC) | Method | Evidence (verbatim / exact) |
|---|---|---|---|---|
| KEV still not listed; SSVC unchanged; VEX rev 3 | CISA KEV JSON (catalog 2026.10.21), CVE record ADP, Red Hat VEX | 10:10 | JSON | no KEV entry; `Exploitation: none` @ 2026-10-21T14:34Z; VEX `current_release_date 2026-10-22T05:04:37Z` |
| Fortinet: FortiClient EMS now not impacted | FG-IR-26-186 | 10:09 | raw | "Products confirmed NOT Impacted: FortiOS FortiClient EMS FortiPAM FortiProxy FortiDeceptor FortiSandbox FortiMail Cloud FortiNAC-F FortiAP …" |
| Oracle Linux 8 fixed | linux.oracle.com CVE page | 10:09 | raw | "Oracle Linux version 8 (php) \| ELSA-2026-87080 \| 2026-10-21" |
| F5: APM/SSLO also Configuration utility 7.5; no fixes | K000163821 (Playwright) | 10:11 | browser | "BIG-IP (APM, SSLO) 21.x 21.1.0 None High/7.5 (CVSS v3.1) The Configuration utility" |
| Citrix unchanged | support.citrix.com (Playwright) | 10:11 | browser | notice text unchanged, no bulletin listed |
| HestiaCP hestia-php released | GitHub issue #5817 | 10:09 | raw | "An update for Hestia-php and hestia-nginx has been released for Ubuntu Jammy (22.04) and up Debian Bookworm (12) and up" |
| CloudLinux post changed back | blog.cloudlinux.com (3 uncached requests, cf-cache-status MISS) | 10:10 | raw | now "Last updated 21 October 2026, 23:00 UTC"; "on CloudLinux 7, 8 and 9, fixed packages are not in the CloudLinux repositories yet" (at 06:13 UTC the page said "last updated 22 October 2026, 06:00 UTC") |
| Alpine package versions | pkgs.alpinelinux.org package pages | 10:13 | raw | v3.24 php85-fpm 8.5.12-r0 (2026-10-21 16:29), php84-fpm 8.4.27-r0, php83-fpm 8.3.36-r0; v3.23 php85-fpm 8.5.12-r0 (2026-10-22 08:39), php83-fpm 8.3.36-r0, php84-fpm 8.4.21-r0; v3.22 php84 8.4.16-r0, php83 8.3.29-r0, php82 8.2.33-r0 |
| Checkmk Werk #19262 | checkmk.com/werk/19262 | 10:14 | raw | "Only users running Checkmk as a Docker container are affected. For all other installations, Checkmk uses the PHP packages of your Linux distribution"; "Affected Checkmk Versions 2.5.0 2.4.0 2.3.0" |
| Checkmk releases / appliance | forum.checkmk.com JSON (posts by Checkmk-Announcement, staff=true) | 10:14 | JSON | 2.4.0p38 and 2.5.0p17 list "19262 SEC: Docker image: Rebuild with patched PHP (PHP2Shell)"; firmware 1.7.25 "contains fixes for the PHP vulnerabilities CVE-2026-109618 & CVE-2026-109619" |
| Zabbix Docker | GitHub zabbix/zabbix-docker #1982 + Docker Hub API | 10:13 | API | dotneft (COLLABORATOR) 2026-10-22T00:47Z: "all latest images will be rebuilt today"; user report: "alpine-7.0.32 … php 8.5.11", "alpine-7.0-latest … php 8.5.12"; zabbix-web-nginx-pgsql `*-latest` last_updated 2026-10-22T07:14–07:38Z |
| Zabbix advisory | zabbix.com/security_advisories | 10:13 | raw | no PHP2Shell entry; forum thread blocked (bot check) — **not verified** |
| Centreon notice | thewatch.centreon.com | 10:13 | raw | "Centreon does not provide or maintain the PHP packages installed on user platforms." (dated October 21, 2026) |
| GLPI | glpi-project.org blog | 10:13 | raw | "any web server hosting a GLPI instance remains vulnerable until the server's underlying PHP engine is patched"; "every GLPI Cloud server is running a patched, secure PHP version" |
| Nagios | nagios.com security disclosures + XI changelog | 10:13 | raw | no PHP2Shell / CVE match |
| Icinga, Cacti, LibreNMS | icinga.com/blog, community.icinga.com search, Cacti GitHub advisories, LibreNMS releases + forum search | 10:13 | raw / JSON | no PHP2Shell / CVE match |
| Implementation languages | GitHub languages API | 10:14 | API | ansible/ansible Python 86 %; ansible/awx Python 98 %; zabbix/zabbix PHP 14 %; icingaweb2 PHP 84 %; cacti PHP 62 %; librenms PHP 88 %; glpi PHP 84 %; centreon PHP 72 %; nagioscore C 75 % + `html/index.php.in, main.php, side.php`; rundeck Groovy/Java; semaphore Go |
| Ansible not in Red Hat VEX | VEX product tree | 10:14 | JSON | products: RHEL, OpenShift AI, OpenShift Dev Spaces, Hardened Images — no Ansible product |


## Update 14 checks (22 Oct 2026, headed Chrome)

| Claim | Source | Checked (UTC) | Method | Evidence (verbatim / exact) |
|---|---|---|---|---|
| Zabbix forum: no vendor statement | zabbix.com forum thread 517840 | 11:09 | browser (headed) | community posts only, e.g. "There will probably be an implicit unintended patch when the image for the next zabbix patch version 7.0.33(?) is released" |
| Sophos advisory | sophos.com | 11:09 | browser (headed) | "UPDATED 2026 Oct 22 \| ARTICLE VERSION 3 \| FIRST PUBLISHED 2026 Oct 21"; "No Sophos products are affected by these vulnerabilities."; "The PHP Project received the first reports of these issues on August 11, 2026"; "reviewing activity on exposed systems from August 1, 2026 onwards"; "on PHP 8.5, fatal_error_backtraces=0" |
| Broadcom/VMware: no advisory | support.broadcom.com security advisories | 11:10 | browser (headed) | latest entry "VMSA-2026-0007 … 03 September 2026"; no PHP entry |
| Akamai WAF rule | akamai.com blog (21 Oct) | 11:10 | browser (headed) | "Adaptive Security Engine: 3000991 v1 — PHP Remote Code Execution Attack Detected (CVE-2026-109618, CVE-2026-109619)" |
| CloudLinux KB | cloudlinux.zendesk.com article 31194180517916 | 11:10 | browser (headed) | "All fixed alt-php and ea-php builds are in the regular stable repositories"; "reached the CloudLinux repositories at about 01:00 UTC on 22 October"; build table (alt-php74 7.4.33-81 …) |
| A10: no advisory | support.a10networks.com security advisories | 11:11 | browser (headed) | latest entry "RADIUS PROTOCOL - CVE-2024-3596 March 20, 2025" |
| Barracuda advisory | trust.barracuda.com/security/php-vulnerabilities | 11:12 | browser (headed) | product table verbatim (Not affected / Under investigation) |
| Progress KB | community.progress.com search | 11:12 | browser (headed) | titles: "LoadMaster is not affected by CVE-2026-109618 and CVE-2026-109619"; MOVEit: "No action or remediation is required"; WS_FTP: "supported WS_FTP Server and Professional versions are not affected … previous supported versions were exposed" (search snippets of the KB articles) |

## Update 15 checks (22 Oct 2026)

| Claim | Source | Checked (UTC) | Method | Evidence (verbatim / exact) |
|---|---|---|---|---|
| Check Point affected, fix date, mitigation | support.checkpoint.com/results/sk/sk1000302 | 15:10 | browser (headless), `innerText` + hidden sections via `textContent` | "Affected Versions: R81.20, R82, R82.10, R82.20 / R80, R80.10, R80.20, R80.30, R80.40, R81, R81.10 (all EoS) / Spark Firewalls R81.10.x, R82.00.x / Spark Firewalls R77.20.x, R80.20.x (all EoS)"; "Check Point Portal and SaaS services are already patched"; "Check Point will release an automatic mitigation through the Automatic Updates mechanism before October, 22, 2026 at 21:00 GMT"; "The fix is planned for the release on November 11, 2026, as part of the Jumbo Hotfix Accumulators."; "Date Created 2026-10-21 Last Modified 2026-10-22" |
| SUSE LTSS / SAP fixed | suse.com/security/cve/CVE-2026-109618.html and -109619.html (identical status tables) | 15:12 / 15:15 | raw HTML | "SUSE Linux Enterprise Server 15 SP6-LTSS :: php8 >= 8.2.35-150600.3.39.1"; "SUSE Linux Enterprise Server 15 SP4-LTSS :: php8 >= 8.0.30-150400.4.80.1"; "php7 >= 7.4.33-150400.4.81.1"; patchnames `SUSE-SLE-Product-SLES-15-SP4-LTSS-2026-4852`, `…-4853`, `SUSE-SLE-Product-SLES-15-SP6-LTSS-2026-4843`, `SUSE-SLE-Module-Legacy-15-SP7-2026-4853`; 16.0/16.1 "In progress"; "Overall state of this security issue: Pending" |
| CloudLinux native php partial | cloudlinux.statuspage.io incident zl0vt1yq3dj5 (`/api/v2/incidents.json`) | 15:12 | JSON API | update 2026-10-22T09:21:46Z: "The fixed builds for the other native versions are not in stable yet. They are in the beta channel (updates-testing), and a gradual rollout has delivered them to about 0.2% of servers so far."; 05:23Z: "The native PHP 7.3 fix for CloudLinux 8 is still being prepared."; alt-php "(in stable since 21 October, 21:48 UTC)" |

## Fetch log (raw downloads)

| UTC | name | HTTP | bytes | URL |
|---|---|---|---|---|
| 2026-10-22T06:13:37Z | sophos | 000 | 0 | https://www.sophos.com/en-us/security-advisories/sophos-sa-20261021-php2shell |
| 2026-10-22T06:13:37Z | cpai | 200 | 6136 | https://advisories.checkpoint.com/defense/advisories/public/2026/cpai-2026-15172.html |
| 2026-10-22T06:13:37Z | fortipsirt | 200 | 8333 | https://fortiguard.fortinet.com/psirt/FG-IR-26-186 |
| 2026-10-22T06:13:37Z | fortits | 200 | 12604 | https://fortiguard.fortinet.com/threat-signal-report/6551 |
| 2026-10-22T06:13:37Z | pan | 200 | 6762 | https://security.paloaltonetworks.com/CVE-2026-109618 |
| 2026-10-22T06:13:37Z | ghsa2 | 200 | 22131 | https://github.com/php/php-src/security/advisories/GHSA-6wmf-4rv5-p3rp |
| 2026-10-22T06:13:37Z | ghsa1 | 200 | 15347 | https://github.com/php/php-src/security/advisories/GHSA-w8hw-w9fx-j79w |
| 2026-10-22T06:13:37Z | unit42 | 200 | 9897 | https://unit42.paloaltonetworks.com/cve-2026-109618-cve-2026-109619/ |
| 2026-10-22T06:13:37Z | netgate | 200 | 9481 | https://www.netgate.com/blog/critical-php-security-update |
| 2026-10-22T06:13:38Z | debian | 200 | 1738 | https://security-tracker.debian.org/tracker/CVE-2026-109618 |
| 2026-10-22T06:13:38Z | suse | 200 | 20311 | https://www.suse.com/security/cve/CVE-2026-109618.html |
| 2026-10-22T06:13:37Z | opnsense | 200 | 1832 | https://forum.opnsense.org/index.php?topic=53191.0 |
| 2026-10-22T06:13:38Z | usn1 | 200 | 5079 | https://ubuntu.com/security/notices/USN-8948-1 |
| 2026-10-22T06:13:37Z | trend | 200 | 10980 | https://success.trendmicro.com/en-US/solution/KA-0024789 |
| 2026-10-22T06:13:38Z | usn2 | 200 | 7006 | https://ubuntu.com/security/notices/USN-8948-2 |
| 2026-10-22T06:13:38Z | ubuntucve | 200 | 5470 | https://ubuntu.com/security/CVE-2026-109618 |
| 2026-10-22T06:13:38Z | alma | 200 | 16091 | https://almalinux.org/blog/2026-10-21-php2shell-cve-2026-109618-cve-2026-109619/ |
| 2026-10-22T06:13:38Z | awsbull | 200 | 11793 | https://aws.amazon.com/security/security-bulletins/2026-143-aws/ |
| 2026-10-22T06:13:38Z | oracle | 200 | 2146 | https://linux.oracle.com/cve/CVE-2026-109618.html |
| 2026-10-22T06:13:38Z | gcp | 200 | 12721 | https://cloud.google.com/blog/products/identity-security/responding-to-core-php-vulnerabilities-cve-2026-109618-cve-2026-109619 |
| 2026-10-22T06:13:38Z | alas | 200 | 2142 | https://explore.alas.aws.amazon.com/CVE-2026-109618.html |
| 2026-10-22T06:13:38Z | certeu | 200 | 7288 | https://cert.europa.eu/publications/security-advisories/2026-018/ |
| 2026-10-22T06:13:39Z | fedora | 200 | 4160 | https://linuxsecurity.com/advisories/fedora/fedora-44-php-2026-a9eba4bbc3 |
| 2026-10-22T06:13:39Z | watchtowr | 200 | 15011 | https://watchtowr.com/intelligence/php-remote-code-execution-php2shell/ |
| 2026-10-22T06:13:38Z | ciq | 200 | 17098 | https://kb.ciq.com/article/security-advisories/cve-php2shell-mitigation |
| 2026-10-22T06:13:39Z | cloudlinux | 200 | 20192 | https://blog.cloudlinux.com/php-cve-2026-109618-and-cve-2026-109619 |
| 2026-10-22T06:13:39Z | remi351 | 200 | 11288 | https://github.com/remicollet/remirepo/issues/351 |
| 2026-10-22T06:13:37Z | cpblog | 200 | 15217 | https://blog.checkpoint.com/security/php2shell-what-we-know-about-the-leaked-critical-php-vulnerabilities-cve-2026-109618-cve-2026-109619/ |
| 2026-10-22T06:13:37Z | talos | 200 | 8372 | https://blog.talosintelligence.com/two-critical-rces-in-php-core/ |
| 2026-10-22T06:13:37Z | cisco | 200 | 8335 | https://sec.cloudapps.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-php-october26-Jj384Daq |
| 2026-10-22T06:13:39Z | rhsb | 200 | 6320 | https://access.redhat.com/security/vulnerabilities/RHSB-2026-013 |
| 2026-10-22T06:13:39Z | cpanelea4 | 200 | 86417 | https://docs.cpanel.net/changelogs/easyapache-4-change-log-25/ |
| 2026-10-22T06:18:22Z | akamai | 403 | 289 | https://www.akamai.com/blog/security-research/critical-remote-code-execution-vulnerabilities-php-core |
| 2026-10-22T06:18:23Z | hpe05159 | 200 | 2 | https://support.hpe.com/hpesc/public/docDisplay?docId=hpesbnw05159en_us&docLocale=en_US |
| 2026-10-22T06:18:22Z | cccs | 200 | 5826 | https://www.cyber.gc.ca/en/alerts-advisories/al26-026-critical-vulnerabilities-impacting-php-cve-2026-109618-cve-2026-109619 |
| 2026-10-22T06:18:23Z | tenable | 200 | 32051 | https://www.tenable.com/blog/php2shell-cve-2026-109618-cve-2026-109619-frequently-asked-questions-about-critical-php-remote |
| 2026-10-22T06:18:24Z | tenablecve | 200 | 3353 | https://www.tenable.com/cve/CVE-2026-109618 |
| 2026-10-22T06:18:22Z | sophosblog | 000 | 0 | https://www.sophos.com/en-us/blog/proof-of-concept-exploit-released-for-php-vulnerabilities-109618-109619 |
| 2026-10-22T06:18:24Z | sophos | 000 | 0 | https://www.sophos.com/en-us/security-advisories/sophos-sa-20261021-php2shell |
| 2026-10-22T06:18:22Z | qualys | 200 | 17242 | https://blog.qualys.com/vulnerabilities-threat-research/2026/10/20/php-announces-critical-security-release-for-two-vulnerabilities |
| 2026-10-22T06:18:22Z | ncscuk | 200 | 7586 | https://www.ncsc.gov.uk/news/critical-security-issue-affecting-php |
| 2026-10-22T06:18:22Z | rapid7 | 200 | 17032 | https://www.rapid7.com/blog/post/etr-cve-2026-109618-and-cve-2026-109619-critical-unauthenticated-remote-code-execution-in-php/ |
| 2026-10-22T06:18:22Z | msqa | 200 | 3552 | https://learn.microsoft.com/en-gb/answers/questions/6045369/when-will-php-8-4-27-fix-for-cve-2026-109618-cve-2 |
| 2026-10-22T06:18:22Z | msblog | 200 | 9897 | https://techcommunity.microsoft.com/blog/azurenetworksecurityblog/addressing-php2shell-cve-2026-109618-and-cve-2026-109619-upgrade-guidance-and-az/4566623 |
| 2026-10-22T06:18:58Z | amazonti | 200 | 12175 | https://aws.amazon.com/blogs/security/amazon-threat-intelligence-identifies-php2shell-exploitation-prior-to-public-disclosure-in-madpot/ |
| 2026-10-22T06:19:25Z | junipersirt |  | 0 | https://supportportal.juniper.net/s/global-search/%40uri?language=en_US#sort=%40sfcec_community_publish_date_formula__c%20descending&f:ctype=[Security%20Advisories] |
| 2026-10-22T06:19:25Z | ivantiforum |  | 0 | https://forums.ivanti.com/s/searchallcontent?language=en_US#t=All&sort=date%20descending&f:@sfkbknowledgearticletypec=[Security%20Advisory] |
| 2026-10-22T06:19:25Z | siemens | 200 | 1241896 | https://cert-portal.siemens.com/productcert/csaf/ssa-feed-tlp-white.json |
| 2026-10-22T06:19:26Z | zabbix | 200 | 6377 | https://www.zabbix.com/security_advisories |
| 2026-10-22T06:19:25Z | watchguard | 200 | 32760 | https://www.watchguard.com/wgrd-psirt/advisories |
| 2026-10-22T06:19:25Z | ivantisa | 200 | 379 | https://www.ivanti.com/blog/topics/security-advisory |
| 2026-10-22T06:19:25Z | sonicwall | 200 | 19 | https://psirt.global.sonicwall.com/vuln-list |
| 2026-10-22T06:19:25Z | citrixsb | 404 | 767 | https://support.citrix.com/s/article/CTX000000?language=en_US |
| 2026-10-22T06:19:27Z | adobe | 403 | 225 | https://helpx.adobe.com/security.html |
| 2026-10-22T06:19:27Z | akamaiblog | 403 | 289 | https://www.akamai.com/blog/security-research/critical-remote-code-execution-vulnerabilities-php-core |
| 2026-10-22T06:19:27Z | cfblog | 200 | 8390 | https://blog.cloudflare.com/ |
| 2026-10-22T06:19:25Z | barracuda | 200 | 20094 | https://www.barracuda.com/company/legal/trust-center |
| 2026-10-22T06:19:26Z | nagios | 200 | 5775 | https://www.nagios.com/products/security/ |
| 2026-10-22T06:19:27Z | progress | 200 | 19704 | https://www.progress.com/security |
| 2026-10-22T06:19:27Z | imperva | 200 | 10862 | https://www.imperva.com/blog/ |
| 2026-10-22T06:19:27Z | zscaler | 404 | 381 | https://trust.zscaler.com/posts |
| 2026-10-22T06:19:27Z | a10 | 404 | 1386 | https://support.a10networks.com/support/security_advisories |
| 2026-10-22T06:19:48Z | wgsa | 200 | 32760 | https://www.watchguard.com/wgrd-psirt/advisory/wgsa-2026-00032 |
| 2026-10-22T06:19:49Z | impervapost | 200 | 22071 | https://www.imperva.com/blog/php2shell-vulnerability-updates/ |
| 2026-10-22T06:20:06Z | wgsa | 200 | 2290 | https://psirt.watchguard.com/WGSA-2026-0032/ |
| 2026-10-22T06:20:06Z | cfpost | 200 | 19992 | https://blog.cloudflare.com/php-vulnerabilities-waf-protection/ |
| 2026-10-22T06:23:54Z | remi8 | 200 | 7372 | https://rpms.remirepo.net/enterprise/8/modular/x86_64/repoview/php-fpm.html |
| 2026-10-22T06:23:54Z | remi10 | 200 | 6532 | https://rpms.remirepo.net/enterprise/10/modular/x86_64/repoview/php-fpm.html |
| 2026-10-22T06:23:59Z | remi9 | 200 | 6514 | https://rpms.remirepo.net/enterprise/9/modular/x86_64/repoview/php-fpm.html |
| 2026-10-22T06:24:06Z | elts | 200 | 1786 | https://deb.freexian.com/extended-lts/tracker/CVE-2026-109618 |
| 2026-10-22T06:24:06Z | zscaler | 200 | 17579 | https://www.zscaler.com/blogs/security-research/cve-2026-109618-and-cve-2026-109619-php-vulnerable-unauthenticated-rce |
| 2026-10-22T06:25:26Z | directadmin | 200 | 8560 | https://forum.directadmin.com/threads/critical-php-updates.82726/page-3 |
| 2026-10-22T06:25:26Z | hestia | 200 | 13225 | https://github.com/hestiacp/hestiacp/issues/5817 |
| 2026-10-22T10:10:01Z | debian | 200 | 1738 | https://security-tracker.debian.org/tracker/CVE-2026-109618 |
| 2026-10-22T10:10:01Z | netgate | 200 | 9481 | https://www.netgate.com/blog/critical-php-security-update |
| 2026-10-22T10:10:01Z | suse | 200 | 20311 | https://www.suse.com/security/cve/CVE-2026-109618.html |
| 2026-10-22T10:10:02Z | elts | 200 | 2238 | https://deb.freexian.com/extended-lts/tracker/CVE-2026-109618 |
| 2026-10-22T10:10:02Z | usn1 | 200 | 5079 | https://ubuntu.com/security/notices/USN-8948-1 |
| 2026-10-22T10:10:01Z | fortipsirt | 200 | 9018 | https://fortiguard.fortinet.com/psirt/FG-IR-26-186 |
| 2026-10-22T10:10:02Z | ubuntucve | 200 | 5470 | https://ubuntu.com/security/CVE-2026-109618 |
| 2026-10-22T10:10:02Z | usn2 | 200 | 7006 | https://ubuntu.com/security/notices/USN-8948-2 |
| 2026-10-22T10:10:02Z | alma | 200 | 16091 | https://almalinux.org/blog/2026-10-21-php2shell-cve-2026-109618-cve-2026-109619/ |
| 2026-10-22T10:10:01Z | wgsa | 200 | 2290 | https://psirt.watchguard.com/WGSA-2026-0032/ |
| 2026-10-22T10:10:01Z | pan | 200 | 6762 | https://security.paloaltonetworks.com/CVE-2026-109618 |
| 2026-10-22T10:10:02Z | oracle | 200 | 2635 | https://linux.oracle.com/cve/CVE-2026-109618.html |
| 2026-10-22T10:10:02Z | ciq | 200 | 17098 | https://kb.ciq.com/article/security-advisories/cve-php2shell-mitigation |
| 2026-10-22T10:10:01Z | trend | 200 | 10980 | https://success.trendmicro.com/en-US/solution/KA-0024789 |
| 2026-10-22T10:10:02Z | cloudlinux | 200 | 33800 | https://blog.cloudlinux.com/php-cve-2026-109618-and-cve-2026-109619 |
| 2026-10-22T10:10:02Z | awsbull | 200 | 11793 | https://aws.amazon.com/security/security-bulletins/2026-143-aws/ |
| 2026-10-22T10:10:02Z | gcp | 200 | 12721 | https://cloud.google.com/blog/products/identity-security/responding-to-core-php-vulnerabilities-cve-2026-109618-cve-2026-109619 |
| 2026-10-22T10:10:02Z | alas | 200 | 2142 | https://explore.alas.aws.amazon.com/CVE-2026-109618.html |
| 2026-10-22T10:10:03Z | cfpost | 200 | 19992 | https://blog.cloudflare.com/php-vulnerabilities-waf-protection/ |
| 2026-10-22T10:10:01Z | cisco | 200 | 8335 | https://sec.cloudapps.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-php-october26-Jj384Daq |
| 2026-10-22T10:10:03Z | rhsb | 200 | 6684 | https://access.redhat.com/security/vulnerabilities/RHSB-2026-013 |
| 2026-10-22T10:10:03Z | watchtowr | 200 | 15011 | https://watchtowr.com/intelligence/php-remote-code-execution-php2shell/ |
| 2026-10-22T10:10:03Z | amazonti | 200 | 12175 | https://aws.amazon.com/blogs/security/amazon-threat-intelligence-identifies-php2shell-exploitation-prior-to-public-disclosure-in-madpot/ |
| 2026-10-22T10:10:03Z | zscaler | 200 | 17587 | https://www.zscaler.com/blogs/security-research/cve-2026-109618-and-cve-2026-109619-php-vulnerable-unauthenticated-rce |
| 2026-10-22T10:10:03Z | sophos | 000 | 0 | https://www.sophos.com/en-us/security-advisories/sophos-sa-20261021-php2shell |
| 2026-10-22T10:10:02Z | cpanelea4 | 200 | 86417 | https://docs.cpanel.net/changelogs/easyapache-4-change-log-25/ |
| 2026-10-22T10:10:03Z | remi9 | 200 | 6514 | https://rpms.remirepo.net/enterprise/9/modular/x86_64/repoview/php-fpm.html |
| 2026-10-22T10:10:03Z | remi8 | 200 | 7372 | https://rpms.remirepo.net/enterprise/8/modular/x86_64/repoview/php-fpm.html |
| 2026-10-22T10:10:03Z | remi10 | 200 | 6532 | https://rpms.remirepo.net/enterprise/10/modular/x86_64/repoview/php-fpm.html |
| 2026-10-22T10:10:03Z | hestia | 200 | 14227 | https://github.com/hestiacp/hestiacp/issues/5817 |
| 2026-10-22T10:10:02Z | msblog | 200 | 9895 | https://techcommunity.microsoft.com/blog/azurenetworksecurityblog/addressing-php2shell-cve-2026-109618-and-cve-2026-109619-upgrade-guidance-and-az/4566623 |
| 2026-10-22T10:10:03Z | certeu | 200 | 7288 | https://cert.europa.eu/publications/security-advisories/2026-018/ |
| 2026-10-22T10:12:27Z | zbxforum | 403 | 18 | https://www.zabbix.com/forum/zabbix-help/517840-critical-php-cve-released-and-patched-today-when-will-zabbix-docker-catch-up |
| 2026-10-22T10:12:27Z | zbxsec | 200 | 6377 | https://www.zabbix.com/security_advisories |
| 2026-10-22T10:12:27Z | nagiossec | 200 | 5775 | https://www.nagios.com/security-disclosures/ |
| 2026-10-22T10:12:27Z | checkmkwerks | 200 | 92925 | https://checkmk.com/werks |
| 2026-10-22T10:12:27Z | nagiosxicl | 200 | 343871 | https://www.nagios.com/changelog/nagios-xi/ |
| 2026-10-22T10:12:28Z | cactisec | 200 | 4017 | https://github.com/Cacti/cacti/security/advisories |
| 2026-10-22T10:12:27Z | centreon | 200 | 7440 | https://thewatch.centreon.com/latest-security-bulletins-64/security-notice-centreon-assessment-of-critical-php-vulnerabilities-6007 |
| 2026-10-22T10:12:28Z | librenmsrel | 200 | 24792 | https://github.com/librenms/librenms/releases |
| 2026-10-22T10:12:27Z | icingablog | 200 | 131920 | https://icinga.com/blog/ |
| 2026-10-22T10:12:27Z | glpi | 200 | 17773 | https://www.glpi-project.org/en/%F0%9F%9A%A8-critical-php2shell-php-vulnerabilities-cve-2026-109618-cve-2026-109619-what-you-need-to-know-for-your-glpi-server/ |
| 2026-10-22T10:14:09Z | werk19262 | 200 | 2321 | https://checkmk.com/werk/19262 |
