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

## Update 16 checks (22 Oct 2026)

| Claim | Source | Checked (UTC) | Method | Evidence (verbatim / exact) |
|---|---|---|---|---|
| Check Point / SUSE / CloudLinux | see update 15 | 15:10–15:16 | – | – |
| QNAP affected | qnap.com/en/security-advisory/qsa-26-18 | 15:17 | browser (headless; curl returns 202 empty) | "Release date : October 22, 2026"; "Status Fixing"; per-product "Fixing / To be announced"; "QNAP has not received reports of exploitation targeting QNAP products." |
| Synology resolved | synology.com Synology_SA_26_14 | 15:17 | browser (headless) | "Publish Time: 2026-10-22 19:45:00 UTC+8"; "PHP 7.3 Critical No fix will be provided as this version has reached end of life."; "PHP 8.4 Critical Upgrade to 8.4.27-0051 or above." |
| Citrix NetScaler affected | community.citrix.com techzone r1640 | 15:23 | browser (headed; headless and curl get Cloudflare 403) | "NetScaler is impacted by two PHP memory safety vulnerabilities … because the NetScaler Management Portal uses PHP"; "All supported NetScaler software versions are impacted. NetScaler Console (Service and on premises) and NetScaler SVM are not impacted"; "Last updated on: October 21, 2026 (Pacific Daylight Time)" |
| Quest KACE affected | support.quest.com KB 4385046 (lead: KACE RSS item 21 Oct 09:58 GMT) | 15:23 | browser (headed; headless 403) | "The KACE Systems Management Appliance (SMA) and KACE Systems Deployment Appliance (SDA) products have been confirmed to be affected"; "Recently released KACE SMA cumulative updates (15.0 Patch 4 and 15.1 Patch 1) do not contain fixes"; R&D IDs 776199, 776200 |
| Ivanti ISM not impacted | hub.ivanti.com article 000109782 | 15:24 | browser (headed) | "Ivanti Service Manager products do not use or have PHP repos loaded on them and therefore are NOT impacted"; created 22 Oct 2026 14:23:12 |
| Ivanti ICS/IPS/vADC/ZTA KB exists, gated | hub.ivanti.com feed 0D5UL00001lXXfz0AG | 15:25 | browser (headed) | Ivanti Employee: "A KB article addressing the new PHP CVE’s … has been published"; article URL redirects to login |
| Ivanti 'Assessment' article = Tomcat | hub.ivanti.com feed 0D5UL00001lEjgK0AS | 15:24 | browser (headed) | "Article Link: https://forums.ivanti.com/s/article/Assessment-and-Impact-of-Multiple-Apache-Tomcat-Vulnerabilities" |
| Broadcom VCF not affected | knowledge.broadcom.com/external/article/459989 | 15:21 | browser (headless) | "Updated On: 10-21-2026"; "VMware Cloud Foundation components do not use PHP and are not affected by the two PHP vulnerabilities." |
| HPE community reply | community.networking.hpe.com thread | 15:21 | browser (headless) | HPE employee: "The product teams across HPE are aware of these vulnerabilities and currently evaluating"; signature: "Any opinions expressed here are solely my own" |
| Juniper: nothing | supportportal.juniper.net global search CVE-2026-109618 | 15:25 | browser (headed) | 5 results, all unrelated JSAs (JSA110075, JSA110076, JSA110091, JSA112187, JSA110078) |
| SonicWall: nothing | psirt.global.sonicwall.com/vuln-list | 15:26 | browser (headed) | top entry "SNWLID-2026-0017 … 2026-10-06"; no PHP entry |
| Barracuda unchanged | trust.barracuda.com/security/php-vulnerabilities | 15:26 | browser (headed) | same product table as update 14 |
| Sophos v4 + IPS | sophos.com advisory | 15:26 | browser (headed) | "ARTICLE VERSION 4"; "Sophos Firewall and Sophos Endpoint customers can use IPS signatures released on October 22, 2026"; "Sophos Firewall Web Application Firewall (WAF) does not currently include protection specific to these vulnerabilities." |
| Cisco v1.2 | sec.cloudapps.cisco.com advisory | 15:28 | browser (headed) | "Last Updated: 2026 October 22 14:13 GMT Version 1.2: Interim"; "Currently, no products are known to be affected."; Meraki, Splunk under investigation; "not aware of any malicious use" |
| F5 unchanged | my.f5.com K000163821 | 15:28 | browser (headed) | "Updated Date: Oct 22, 2026"; BIG-IP fixes "None" |
| PAN unchanged | security.paloaltonetworks.com/json/CVE-2026-109618 | 15:17 | JSON | last timeline entry "2026-10-21T23:33:00.000Z Threat ID released"; PAN-OS "All affected" |
| Fortinet updated | fortiguard.fortinet.com FG-IR-26-186 | 15:17 | raw | "2026-10-22: Products under investigation list updated and OT IPS references added"; FortiPortal in not-impacted list |
| Trend tool | success.trendmicro.com KA-0024789 | 15:17 | raw | "UPDATE (Oct. 22): TrendAI has released an online tool"; still "urgent assessment" |
| WatchGuard / Netgate / OPNsense / Zscaler / Siemens unchanged | respective pages / CSAF feed | 15:17–15:18 | raw / JSON | WGSA updated 2026-10-21; Zscaler "is assessing"; Siemens feed updated 2026-10-19 |
| Zabbix statement | zabbix.com/pr/pr912 | 15:19 | raw | "October 22, 2026 … PHP is used by the Zabbix frontend but is a separate software dependency and is not included in Zabbix packages." |
| Checkmk 2.3.0p51 | checkmk.com/werk/19262 | 15:18 | raw | versions "2.5.0p17 / 2.4.0p38 / 2.3.0p51" |
| Icinga NCSC link unrelated | icinga.com/blog/icinga-web-2-14-security-releases-and-module-updates | 15:11 | raw | no match for 109618/php2shell; post covers "a low-risk open redirect vulnerability" |
| Azure App Service patched | azure.github.io/AppService/2026/10/21/php-critical-security-release-app-service-linux.html | 15:21 | raw | "We have completed the rollout of the updated built-in PHP images with the security fixes to both the" [Standard and Latest] "Platform Release Channels"; table PHP 8.2 8.2.35 / 8.3 8.3.36 / 8.4 8.4.27 |
| Pantheon | status.pantheon.io/api/v2/incidents/x7h8z1yhgvml.json | 15:11 | JSON | 2026-10-21T19:08 PDT: "all pre-production customer environments are patched. Free/sandbox environments will be updated over the next 24-48 hours." |
| Upsun | status.upsun.com RSS | 15:11 | raw RSS | "Thu, 22 Oct 2026 04:12:36 GMT: We’ve finished deploying the PHP security patch to all Dedicated clusters" |
| Acquia | status.acquia.com/api/v2/incidents.json | 15:20 | JSON | 2026-10-22T07:48:29Z: "All Acquia customer applications have been patched and remain online." |
| Scalingo | doc.scalingo.com SSB-2026-005 | 15:11 | raw | "It later blocked multipart HTTP requests at the router for all PHP applications."; "Existing applications … must be rebuilt and redeployed" |
| Nextcloud | github.com/nextcloud/server/issues/65754, all-in-one #8876 | 15:22 | GitHub API | "Please upgrade to AIO v14.4.1 as soon as possible as it ships the updated php dependencies" |
| ISPConfig / aaPanel / Gentoo | respective pages | 15:11 | raw | "This is not an ISPConfig vulnerability."; GLSA "Release date October 21, 2026" |
| Rocky RL8 php:8.2 | apollo.build.resf.org API | 15:27 | JSON | "2026-10-22T12:01:35Z RLSA-2026:87073 Important: php:8.2 security update" |
| Oracle module streams | linux.oracle.com/cve/CVE-2026-109618.html | 15:27 | raw | ELSA-2026-87072, -87079 "Oracle Linux version 9 (php)"; ELSA-2026-87073 "Oracle Linux version 8 (php)" |
| Red Hat VEX unchanged | CSAF VEX | 15:27 | JSON | current_release_date 2026-10-22T05:04:37Z; RHEL 9 php:8.4 still known_affected |
| Alpine all fixed | pkgs.alpinelinux.org | 15:27 | raw | v3.22 php82 8.2.35-r0 (2026-10-22 13:35:10), php84 8.4.27-r0 (12:27:15); v3.23 php84 8.4.27-r0 (09:46:26) |
| Debian / Amazon unchanged | security-tracker.debian.org, explore.alas.aws.amazon.com | 15:27 | raw | forky 8.4.26-1 vulnerable; AL2 php "No Fix Planned" |
| Heroku runtimes | devcenter.heroku.com/changelog-items/3845 | 15:32 | raw | "PHP updates - October 2026 (CVE-2026-109618 and CVE-2026-109619)"; "Change effective on 21 October 2026"; "PHP 8.1.34 on the Heroku-22 stack has been rebuilt with the PHP project’s backported fix" |
| WP Engine: could not check | wpenginestatus.com | 15:32 | raw | "doesn't work properly without JavaScript enabled" |
| AlmaLinux, CIQ, CERT-EU, CCCS, NCSC-UK, Freexian ELTS unchanged | respective pages | 15:32–15:33 | raw | Alma "2026-10-21 21:15 UTC: … now in production"; CIQ "RLC Pro 9, Pro 10, Pro 8, LTS 8.6, and CIQ Bridge are pending"; CERT-EU "21/10/2026 --- v1.1"; CCCS "a Proof of Concept (PoC) is available, with no active exploitation being identified at this time" |
| KEV / SSVC unchanged | CISA KEV JSON, cveawg.mitre.org | 15:27 | JSON | catalogVersion 2026.10.21, 0 matches; SSVC Exploitation=none (21 Oct 14:34Z) |

## Update 17 checks (22 Oct 2026)

| Claim | Source | Checked (UTC) | Method | Evidence (verbatim / exact) |
|---|---|---|---|---|
| Section 2 re-read | Cloudflare blog, Azure WAF blog, Google blog, Imperva, Unit 42, Talos, Fortinet TS 6551, CPAI-2026-15172, Trend KA, AWS bulletin | 15:51–15:56 | raw | Cloudflare "Starting on October 21 3:02 am UTC"; Azure "99006001 … disabled. Customers need to enable the rule", "expected to complete by 28 October 2026"; Fortinet TS "virtual patches … released in version 37.316"; CPAI "Protection Provided by: Security Gateway R82, R81, R80, R77, R75"; Talos "signatures 67359, 67360, and 67375. These rules are also available in the Community Ruleset"; Trend 1012749/48514/6021 present; AWS SizeRestrictions_BODY present |
| Rapid7 PoCs | rapid7.com ETR blog (last updated Oct 22) | 15:51 | raw | "Multiple public proof-of-concept (PoC) exploits … are now available"; "none appears to be broadly reliable" |
| Qualys QIDs | blog.qualys.com (last updated October 22) | 20:13 | raw | QIDs 389102, 39033, 5019896, 6056502 …; 5019895 absent |
| Imunify360 | blog.imunify360.com/php-cve-2026-109618-cve-2026-109619/ | 20:13 | raw | "last updated 22 October 2026, 14:31 UTC"; "No rule blocks the out-of-memory path of CVE-2026-109618 yet"; "its requests had reached more than 3,600 servers" |
| BSI v1.2 | BSI PDF | 15:52 | pdftotext | "BITS-H Nr. 2026-297981-1232, Version 1.2, 22.10.2026"; "Kritikalität*: 3 / Orange"; "Proof-of-Concept öffentlich"; "noch keine bestätigten Ausnutzungen" |
| Ubuntu, Plesk, cPanel, DirectAdmin, Fedora, Docker, Remi, sury | USN-8948-1/-2, Ubuntu CVE page, Plesk Zendesk API, cPanel EA4 changelog, DA forum, Bodhi JSON, Docker Hub API, Remi repoview, sury Packages + changelog | 15:51–15:53 | raw / JSON | Ubuntu CVE page all "Fixed"; Plesk updated_at 2026-10-22T13:41:25Z; cPanel 25.92 = ea-nodejs only; DA staff "PHP 8.1 does not build cleanly on some systems"; Bodhi FEDORA-2026-d5f8446449 php-8.4.27-2.fc43 testing, FEDORA-2026-a9354b8a1e php-8.5.12-1.fc45 testing; sury php8.0 changelog "Backported from 8.2.35 + [CVE-2026-109618, CVE-2026-109619]" |
| A10 | support.a10networks.com/support/security-advisories | 15:54 | browser (headless) | top entry "TACACS+ LOGIN VULNERABILITY– A10-2025-0034 September 30, 2025" |
| Progress | community.progress.com KB 000307376, 000307378 | 15:55 | browser (headless) | WS_FTP: "not affected … as neither uses PHP" (Last Modified 10/22/2026 11:52 AM); LoadMaster etc.: "do not use PHP in any of their respective product components" |
| Feeds re-check | RH VEX, SUSE, PAN JSON, Rocky API, Oracle, ALAS, KEV, SSVC, Debian, NCSC-NL | 20:14 | JSON / raw | unchanged; RH VEX current_release_date 2026-10-22T05:04:37Z; KEV 2026.10.21 |
| CloudLinux native fixed | cloudlinux.statuspage.io API | 20:14 | JSON | 2026-10-22T19:50:16Z: "Fixed native PHP packages … are now in the stable channel for every affected version" |
| Fortinet moved products | FG-IR-26-186 | 20:14 | raw | Under investigation: "FortiDDoS FortiDDoS-F FortiClient Cloud Services FortiSOAR FortiSOAR PaaS"; NOT Impacted includes FortiADC, FortiADC Manager, FortiEndpoint, FortiSIEM, FortiMonitor, FortiDLP |
| Pantheon / Acquia | status APIs | 20:14 | JSON | Pantheon status resolved 2026-10-22T09:36:36-07:00; Acquia 18:29Z "restored all services" |
| Headless re-check | Check Point sk1000302, QNAP, Synology, Cisco, F5, Broadcom | 20:16 | browser (headless) | unchanged (CP Last Modified 2026-10-22; QNAP "V1.0 (October 22, 2026) - Published", all Fixing; Cisco v1.2 14:13 GMT) |
| Citrix fix date | Citrix Tech Zone r1640 | 20:17 | browser (headed) | "Citrix plans to release fixes … for all supported NetScaler software versions on October 27, 2026."; "Last updated on: October 22, 2026" |
| Barracuda changes, KACE, Sophos, SonicWall | respective pages | 20:17–20:18 | browser (headed) | Barracuda WAF/ADC, WaaS, Vulnerability Manager "Not affected"; Firewall Insights, Message Archiver "Under investigation"; KACE "Letzte Aktualisierung am: 10/22/2026", no patch; Sophos v4; SonicWall SNWLID-2026-0018 (NSM, 14 Oct) unrelated |
| Ivanti, Juniper | hub.ivanti.com search, supportportal.juniper.net search "CVE-2026-109618" | 20:18 | browser (headed) | Ivanti: only ISM KB public; Juniper: no results |

## Update 18 checks (22 Oct 2026)

| Claim | Source | Checked (UTC) | Method | Evidence (verbatim / exact) |
|---|---|---|---|---|
| All 93 README sources | see /tmp index (curl + browser) | 20:21–20:33 | raw / JSON / browser | automated check: all claimed key strings present except the changes listed below; Nagios/Icinga still no CVE mention |
| HPE ClearPass affected | support.hpe.com hpesbnw05171en_us (lead: HPE community post 22 Oct) | 20:31 | browser (headed) | "CPPM 6.14.0 and below / CPPM 6.11.15 and below"; "partially mitigates the vulnerabilities in question by moving them from an unauthenticated vulnerability to an authenticated vulnerability requiring cluster-admin privileges"; "HPE Mist Networking products are not impacted"; "Version:1 (rev.1) - 22 October 2026" |
| SonicWall notice | sonicwall.com/support/notices/…kA1VN000002YKw10AG | 20:31 | browser (headed) | "found no use of PHP in the following products"; "2026-10-22 8:17 AM PDT: … SonicWall PSIRT is currently evaluating Switches and Access Points (SonicWave)" |
| N-able | n-able.com blog (Cloudflare challenge; headed) | 20:29 | browser (headed) | "Update October 22, 2026 11 AM EDT We have completed patching for the following products"; "All other products are not affected." |
| Zscaler | zscaler.com ThreatLabz blog | 20:31 | browser (headed) | "has ruled out any impact to the production environment" |
| Synology statement | synology.com press release | 20:32 | raw | "limited to systems running certain PHP-dependent packages"; "scheduled a patch for a subsequent DSM release" |
| Laravel / Kinsta | laravel.com/blog/php-critical-vulnerability-response-updates; status.kinsta.com API | 20:27 | raw / JSON | Laravel "Updated 10/22 - 13:25 UTC"; Kinsta resolved 2026-10-22T08:26:44Z "All sites are protected" |
| FreePBX | community.freepbx.org topic 110401 (.json) | 20:32 | JSON | no Sangoma advisory; staff (penguinpbx) posts only |
| watchTowr exploitation | watchtowr.com FAQ | 20:23 | raw | "watchTowr has observed exploitation of both CVE-2026-109618 and CVE-2026-109619 in the wild." |
| Cloudflare rule names | blog.cloudflare.com | 20:23 | raw | "PHP Remote Code Execution Attack (CVE-2026-109618, CVE-2026-109619) #7 07f0b6ddaabf40b1b2042dade8d613fa"; "Anomalous Execution" no longer present |
| Google Cloud Armor | cloud.google.com blog | 20:23 | raw | "updated on Oct. 22, 2026 at 9:25 a.m. PDT, with revised guidance on Cloud Armor"; "enable the File Upload and RFI categories" |
| Fedora 43 | bodhi API | 20:26 | JSON | FEDORA-2026-d5f8446449 stable 2026-10-22 16:40:54 php-8.4.27-2.fc43 |
| Plesk | Zendesk API article 44397729587351 | 20:26 | JSON | updated_at 2026-10-22T17:44:23Z; fix table unchanged |
| A10, Siemens | A10 advisory list; Siemens CSAF feed | 20:33 | browser / JSON | A10 top A10-2025-0034; Siemens feed updated 2026-10-19 |

## Update 19 checks (22 Oct 2026)

| Claim | Source | Checked (UTC) | Method | Evidence (verbatim / exact) |
|---|---|---|---|---|
| Check Point auto-mitigation not confirmed | support.checkpoint.com/results/sk/sk1000302 | 21:02 | browser (headless), page `textContent` incl. embedded JSON | "Check Point will release an automatic mitigation through the Automatic Updates mechanism before October, 22, 2026 at 21:00 GMT."; `"lastModified":"2026-10-22"` |

## Update 20 checks (23 Oct 2026)

*Update 21:* check times in this section corrected to the ranges between recorded `date -u` calls (03:45, 03:47, 03:51, 03:57/03:58 page clock, 03:59, 04:05, 04:12); the single minutes first written for browser-batch rows were reconstructed, not recorded, and partly out of order.

Method: all 100 URLs of the previous sweep plus README links re-downloaded with curl 03:45–03:47 UTC into a fresh directory, converted to text and diffed line-by-line against the 22 Oct 20:21 UTC copies; automated claim check re-run. Sources that need JavaScript or block curl were read in headless (F5, HPE, QNAP) or headed Chrome on the kodi seat (Citrix, Quest, Sophos, Akamai, CloudLinux KB, Ivanti hub/forums, Juniper portal, Qualys, Upsun, SonicWall PSIRT, Progress, Broadcom, Fastly, SecurityWeek lead). Feeds: CSAF VEX (both CVEs), SUSE CVE page table, PAN JSON, Rocky apollo, Bodhi, KEV, CVE record (SSVC), NVD, Plesk Zendesk API, statuspage.io APIs, Docker Hub, GitHub API.

| Claim | Source | Checked (UTC) | Method | Evidence (verbatim / exact) |
|---|---|---|---|---|
| Cisco v1.4: Expressway and URWB vulnerable | sec.cloudapps.cisco.com cisco-sa-php-october26-Jj384Daq | 03:45–03:47 | raw | "2026 October 22 23:00 GMT"; "Version 1.4"; "Ultra-Reliable Wireless Backhaul (URWB) … CSCwx37073 … 27.1.1 (Feb 2027)"; "Expressway Series CSCwx37062 15.5.21 (TBD)"; "the attacker must be authenticated as an administrator … reducing the CVSS score to 6.6"; under investigation list and not-vulnerable list as in README |
| Splunk: no product known affected | advisory.splunk.com (SVD-2026-1013) | 03:47–03:51 | raw | "SVD-2026-1013 2026-10-22 … Currently, no Splunk products are known to be affected." |
| PAN WildFire WF-500 affected, WildFire Cloud remediated | security.paloaltonetworks.com/json/CVE-2026-109618 + HTML | 03:47–03:51 | JSON + raw | WF-500 version entry `status: affected`; HTML "WildFire Appliance WF-500 and WF-500-B All None (ETA: TBD)"; "Although WildFire Cloud was previously impacted, a remediation patch was deployed on October 22, 2026."; timeline "2026-10-23T00:25:00.000Z Updated the status of Cortex XDR Broker VM, Cortex XCORE (SaaS), Strata Cloud Manager, WildFire Appliance WF-500 and WF-500-B and WildFire Cloud" |
| Check Point: permanent fix by 23 Oct 17:00 GMT; auto-mitigation sentence removed | support.checkpoint.com/results/sk/sk1000302 | 03:45–03:47 | raw (embedded JSON, unicode-unescaped) | "October, 22, 2026 at 21:50 GMT update: Check Point is expecting to deliver a permanent fix based on the latest PHP code by October 23, 17:00 GMT."; "solution":" The fix is planned for the release on November 11, 2026 , as part of the Jumbo Hotfix Accumulators."; `"lastModified":"2026-10-23"`; no occurrence of "automatic" in the article body |
| F5 updated 23 Oct; CNF not vulnerable | my.f5.com K000163821 | 03:51–03:57 | browser (headless) innerText | "Published Date: Oct 21, 2026Updated Date: Oct 23, 2026"; "BIG-IP Next CNF All None Not applicable Not vulnerable"; "BIG-IP eBPF Observability (EOB) All None … Not vulnerable"; "F5 API Security Local Edition All None … Not vulnerable"; "F5 AI Gateway 1.x ** ** ** **"; signatures 200103697, 200204115 unchanged |
| RHEL 7 / RHEL 6 status | security.access.redhat.com CSAF VEX cve-2026-109618.json, cve-2026-109619.json | 03:45–03:51 | JSON | 109618 `current_release_date` 2026-10-22T23:03:02: RHEL 7 in `known_not_affected`, flag `vulnerable_code_not_present`; RHEL 6 `known_affected`, remediation `no_fix_planned` "Out of support scope". 109619 (23:03:18): RHEL 6 and 7 `known_affected`; RHEL 7 remediation `none_available` "Affected"; RHEL 9 php:8.4 still `known_affected` |
| SUSE 16.0 released, 16.1 affected, SLE 12 php74 released | suse.com/security/cve/CVE-2026-109618.html | 03:45–03:47 | raw (status table diff) | "SUSE Linux Enterprise Server 16.0 php8 In progress -> Released"; "16.1 php8 In progress -> Affected"; "php8 >= 8.4.27-160000.1.1", "SUSE-SLES-16.0-1955"; "php74 >= 7.4.33-1.74.1", "SUSE-SLE-Module-Web-Scripting-12-2026-4870"; "Overall state of this security issue: Pending" |
| Amazon TI wording change | aws.amazon.com/blogs/security/amazon-threat-intelligence-identifies-php2shell-… | 03:45–03:47 | raw diff | old: "PHP2Shell is now being broadly exploited in the wild." new: "PHP2Shell is now seeing broad exploitation attempts in the wild." |
| AWS bulletin 22 Oct 14:00 PDT | aws.amazon.com/security/security-bulletins/2026-143-aws/ | 03:45–03:47 | raw | "Last Updated Date: 10/22/2026 14:00 PM PDT"; WorkMail "has completed the upgrade to PHP 8.3.36. No customer action is required."; Beanstalk "updated PHP platform versions for all supported PHP versions (8.2 through 8.5) containing the upstream PHP fix"; "We are continuously updating the AWS WAF PHP Managed Rule Group" |
| Google Cloud SCC update | cloud.google.com/blog/… | 03:45–03:47 | raw | "Oct. 22, 2026 at 4:07 p.m. PDT with revised guidance for Security Command Center" |
| Barracuda: Message Archiver not affected | trust.barracuda.com/security/php-vulnerabilities | 03:45–03:47 | raw | "Message Archiver | Not affected"; "Firewall Insights | Under investigation" |
| Trend Micro filter 48534 | success.trendmicro.com KA-0024789 | 03:45–03:47 | raw | "Filter 48514 (Security Policy) – Sec Optimized enabled"; "Filter 48534 - HTTP: PHP Core Upload Progress Use-After-Free Vulnerability" (previously "Filter 48531 - …"); "Last updated: 2026/10/22" |
| Talos: Splunk ESCU | blog.talosintelligence.com/two-critical-rces-in-php-core/ | 03:45–03:47 | raw | "Splunk has released an Enterprise Security Content Update (ESCU) related to the ongoing PHP2Shell activity with additional detections." |
| CloudLinux PHP.net-numbered alt-php | cloudlinux.statuspage.io /api/v2/incidents.json | 03:47–03:51 | JSON | 2026-10-23T00:08:34Z "alt-php builds with the PHP.net version numbers are now in the stable repositories for CloudLinux OS 8 and 9: alt-php82: 8.2.35-1 … alt-php85: 8.5.12-1" |
| Citrix WAF signature v186; fix date unchanged | community.citrix.com Tech Zone r1640 | 03:51–03:57 | browser (headed) | "Yes, WAF signature (v186) has been released."; "Citrix plans to release fixes … on October 27, 2026."; "Last updated on: October 22, 2026 (Pacific Daylight Time)" |
| Quest CU5/CU2 in QA | support.quest.com KB 4385046 | 03:51–03:57 | browser (headed) | "15.0 CU5 and 15.1 CU2 are now under QA Validation."; "Last Update on: 10/22/2026" |
| Sophos unchanged (v4) | sophos.com sophos-sa-20261021-php2shell | 03:51–03:57 | browser (headed) | "UPDATED 2026 Oct 22 ARTICLE VERSION 4" |
| Akamai unchanged | akamai.com blog | 03:51–03:57 | browser (headed) | "Adaptive Security Engine: 3000991 v1 — PHP Remote Code Execution Attack Detected" |
| HPE ClearPass unchanged | support.hpe.com hpesbnw05171en_us | 03:51–03:57 | browser (headless) | "Last Updated: 2026-10-22 … Document Version: 1"; "partially fixed … CPPM 6.14.1 CPPM 6.11.16"; "fully mitigate … currently in development" |
| QNAP unchanged | qnap.com QSA-26-18 | 03:51–03:57 | browser (headless) | "Status Fixing"; every row "Fixing To be announced" |
| Ivanti forum answers by Ivanti employees | forums.ivanti.com feeds 0D5UL00001lVKex0AG, 0D5UL00001lO6O80AK, 0D5UL00001lOAjK0AW | 03:57–03:58 | browser (headed) | "G.Kumar (Ivanti Employee) … confirmed that Ivanti vTM and Services Director are not affected, as PHP is not installed or used by these products"; "AOD WAF signature updates relies on PHP-based systems … customers may observe interruptions"; "Larry_G (Ivanti Employee) … No impact. An article was just published about this: Impact of CVE-2026-109618 on EPMM/Sentry/Connector products"; "Casity.chris (Ivanti Employee) … A security update is required for the PHP components used by Ivanti Cloud Services Application (CSA)". KB links redirect to login |
| Juniper: nothing | supportportal.juniper.net global search "CVE-2026-109618" | 03:59–04:05 | browser (headed) | "Results 1-5 of 5" — JSA110075, JSA110076, JSA110091, JSA112187 (unrelated Junos bulletins) |
| Broadcom ESG advisory 39404 | support.broadcom.com …/SecurityAdvisories/0/39404 | 04:05–04:12 | browser (headed) | "Last Updated 22 October 2026 Initial Publication Date 21 October 2026 Status OPEN"; "Affected Product(s) Carbon Black App Control Server - …/39411 Symantec Endpoint Protection Manager (SEPM) - …/39421"; "under investigation: CloudSOC Cloud Access Security Broker (CASB) Content Analysis"; revisions "2026-10-22 08:00 PT - Carbon Black App Control moved to Affected", "2026-10-22 04:00 PT - Symantec Endpoint Protection Manager moved to Affected". 39411/39421 redirect to login |
| Broadcom protection bulletin | broadcom.com/support/security-center/protection-bulletin | 04:05–04:12 | browser (headed) | "October 21, 2026 PHP2Shell Vulnerabilities Allow Remote Code Execution in PHP Runtimes"; "File-Based Antivirus Protection … Hacktool.Php2shell" |
| Fastly virtual patch | quic.fastly.com …/added-virtual-patch-for-CVE-2026-109618-and-CVE-2026-109619/ | 04:05–04:12 | browser (headed) | "October 21, 2026 … Fastly has combined both CVE-2026-109618 and CVE-2026-109619 into one virtual patch. To activate it …" |
| Siemens evaluating | productcert.siemens.com/news/2026/10/22/php2shell---… | 03:59–04:05 | raw | "October 22, 2026 … We are evaluating the impact to Siemens products. For Siemens products that are affected … security advisories (SSA) will be published"; CSAF feed `updated` 2026-10-19T00:00:00Z |
| SolarWinds Pingdom | solarwinds.com/trust-center/security-advisories/cve-2026-109618-and-cve-2026-109619 | 03:59–04:05 | raw | "Pingdom uses PHP, but we have implemented compensating controls to protect the product."; "There is no action needed from customers on this issue." |
| Kaseya | status.kaseya.com /api/v2/incidents.json | 03:59–04:05 | JSON | "PHP vulnerabilities (CVE-2026-109618 and CVE-2026-109619): Kaseya status - Investigation and Remediation" status `investigating`; "Kaseya security teams are assessing all Kaseya systems and products and applying fixes as they become available."; "All products: Customer action: none" |
| TuxCare ELS | tuxcare.com/els-php2shell-patches-faq/, tuxcare.com/blog/php2shell-cve/ | 03:59–04:05 | raw | "Engineering backported the fixes to every alt-php branch: 5.2–5.6, 7.0–7.4 and 8.0–8.5."; "alt-php74 stays at 7.4.33 and changes from release -79 to -81 on EL7"; "On ELS for OS platforms, the native OS PHP packages also got the fix."; blog: "rolling out across the end-of-life PHP versions … with timing and coverage varying by branch and platform" |
| LibreNMS Docker | api.github.com/repos/librenms/docker/releases | 03:59–04:05 | JSON | "26.10.2-r1 2026-10-21T20:12:09Z … This release rebuilds the Alpine image with PHP 8.4.27." |
| Vercel | vercel.com/kb/bulletin/php2shell-security-bulletin | 03:59–04:05 | raw | "Vercel WAF blocks known php2shell exploit patterns, but does not replace patching." (21 Oct 2026) |
| Corelight | api.github.com search corelight/php2shell-detect | 03:59–04:05 | JSON | "Zeek and Suricata Detections for \"php2shell\" CVE-2026-109618 and CVE-2026-109619", pushed 2026-10-21T14:35:20Z |
| Sansec 22 Oct update | sansec.io/research/php2shell | 03:59–04:05 | raw | "Update October 22: Mass exploitation of PHP2Shell is less likely than we expected on release day. … The public exploits do not work against a default PHP installation." |
| Rapid7 exploitation wording | rapid7.com ETR blog | 03:45–03:47 | raw | "Rapid7 has not observed exploitation in the wild, though there are multiple reports of exploitation attempts" |
| CISA alert | cisa.gov/news-events/alerts/2026/10/21/critical-vulnerabilities-php-require-immediate-patching | 03:59–04:05 | raw | "While CISA has not observed exploitation of these vulnerabilities as of the time of publication"; "should take PHP-based systems offline until they can be patched or updated" |
| KEV / SSVC / NVD unchanged | KEV JSON, cveawg.mitre.org, NVD API | 03:51–03:57 | JSON | KEV `catalogVersion` 2026.10.21, no 10961x entry; SSVC Exploitation none / Automatable no / Technical Impact total; NVD 9.8, `lastModified` 2026-10-22T23:18:22 |
| Qualys QIDs | blog.qualys.com (last updated October 22) | 04:05–04:12 | browser (headed) | table incl. "520310 PHP Remote Code Execution (RCE) Vulnerabilities (PHP2Shell)", "389120 F5 BIG-IP … (K000163821)", "6056527 Red Hat Security Advisory for CVE-2026-109618 (Unfixed Vulnerability)", "5019896", "389102", "39033" |
| Upsun incident permalink | status.upsun.com/incidents/2cdvc2ctv5jwb | 04:05–04:12 | browser (headed) | "Monitoring … Last Updated: October 22, 2026 at 04:12 UTC"; "We’ve finished deploying the PHP security patch to all Dedicated clusters." |
| Acquia resolved | status.acquia.com /api/v2/incidents.json | 03:51–03:57 | JSON | 2026-10-22T20:30:43Z "All Acquia services have been restored and are fully operational. All customer applications and Acquia platform services are patched" |
| Progress unchanged | community.progress.com global search "CVE-2026-109618" | 04:05–04:12 | browser (headed) | 9 results; the 3 PHP2Shell KBs (LoadMaster, WS_FTP "No action or remediation is required", MOVEit/Automate MFT); the other 6 are unrelated older CVEs |
| A10 nothing | support.a10networks.com/support/security-advisories | 04:05–04:12 | raw | no "A10-2026-" ID and no "PHP" in page text; latest A10-2025-0034 |
| WP Engine / Adobe nothing | wpenginestatus.com, wpengine.com/?s=php2shell, status.adobe.com, helpx.adobe.com/security/security-bulletin.html | 04:05–04:12 | browser (headed) | no PHP item; Adobe bulletin index newest Commerce entry APSB26-153 (10/13/2026) |
| Tenable Security Center / Enclave Security patch | tenable.com/security/tns-2026-28, tns-2026-29; Tenable FAQ blog | 04:15 | raw | "Security Center Patch SC-202610.1 updates the following components: php to version 8.2.35"; "Tenable Enclave Security Patch SC-202610.1 updates the following components: php to version 8.2.35"; FAQ: "Tenable Security Center and Tenable Enclave Security include PHP. Out of caution, Tenable released stand-alone security patch SC-202610.1 for both products on October 22." |
| Unchanged since update 18 (text diff empty or only counters) | Debian tracker, Freexian, Ubuntu CVE/USNs, ALAS, Oracle, Alpine, Remi, Gentoo, AlmaLinux, CIQ, Heroku, Scalingo, Azure, Cloudflare, Imperva, Imunify360, Fortinet PSIRT, WatchGuard, Netgate, OPNsense, Checkmk, Zabbix, Centreon, GLPI, NCSC-UK, CERT-EU, CCCS, BSI (PDF v1.2), watchTowr, Synology, Nextcloud, HestiaCP, DirectAdmin, ISPConfig, aaPanel, cPanel, Zscaler, SonicWall notice, N-able, Laravel, Kinsta, Pantheon, FreePBX forum | 03:45–03:57 | raw diff | Rocky apollo: same 7 RLSAs; Bodhi: F43 stable, F45 testing; Plesk article `edited_at` 2026-10-22T15:58:14Z, same content; Docker Hub newest php tags 22 Oct 15:58 UTC; Arch php 8.5.12-1 |

## Update 22 checks (23 Oct 2026)

Method: the 110 URLs of the update-20/21 sweep re-downloaded with curl 11:09–11:11 UTC into a fresh directory and diffed line-by-line against the 03:45 UTC copies; pages that block curl or need JavaScript re-read in headed Chrome (kodi desktop session) 11:13–11:19 UTC; NCSC-NL commits since 22 Oct 22:50 UTC used as leads only, every adopted claim re-read at the vendor's page. Times are ranges between recorded `date -u` calls.

| Claim | Source | UTC (23 Oct) | Method | Evidence |
|---|---|---|---|---|
| PAN-OS hotfix ETAs | security.paloaltonetworks.com/CVE-2026-109618 | 11:09–11:11 | raw diff | Timeline "2026-10-23 Added estimated availability dates (ETAs) for hotfix releases across supported PAN-OS versions."; e.g. "PAN-OS 11.2.0 … < 11.2.10-h16 … >= 11.2.10-h16 (ETA: 10/26)"; "Panorama All None (ETA: TBD)" |
| Fortinet not-impacted additions, new signatures | fortiguard.fortinet.com/psirt/FG-IR-26-186 | 11:09–11:11 | raw diff | "2026-10-23: Products under investigation list updated and references added"; added "FortiAppSec Cloud", "FortiNDR", "FortiExtender", "FortiTester"; "IPS Signatures: …/ips/62657 …/ips/62658 Released in version 0.00438"; "OT IPS Signatures: …/otips/10009977 …/otips/10009978 Released in version 37.316"; endpoint-vuln 106519/106520; fwb 1090502648 |
| Red Hat EUS/AUS/TUS + 10.0 E2S errata | CSAF VEX cve-2026-109618.json, cve-2026-109619.json | 11:09–11:12 | JSON | `current_release_date` 2026-10-23T10:01:02; new vendor_fix RHSA-2026:88532 (AppStream-8.8.0.Z.E4S/TUS, php-0:7.4.33-1.module+el8.8.0+25148+55cf9df9.2), :88533 (8.6.0 AUS/EUS-ext, 7.4.19-4…el8.6.0+25157…3), :88565 (8.4.0 AUS/EUS-ext, 7.4.6-5…el8.4.0+25156…3), :88561 (AppStream-10.0.Z.E2S, php-0:8.3.19-1.el10_0.2); known_affected still RHEL 6, 9 (php:8.4), Dev Spaces; 109619 also RHEL 7 |
| Trend Micro products impacted | success.trendmicro.com KA-0024802 | 11:12–11:13 | raw | "Current Status as of Oct. 23"; "Apex Central Impacted - Mitigation currently in development"; "Apex One (On-premise server) Impacted - …"; "Trend Micro Web Security (TMWS) Impacted - …"; "Deep Discovery Inspector (DDI) Deep Discovery Analzyer (DDAN) Deep Discovery Email Inspector (DDEI) Impacted - …"; "Apex One as a Service Addressing via emergency maintenance (10/23)"; "has not seen any active instances or scenarios of successful exploitation" |
| Delta Controls SecB0015 | deltacontrols.com/wp-content/uploads/SecB0015_Security_Bulletin.pdf | 11:12–11:13 | raw (pdftotext; some glyphs garbled, only cleanly extracted lines quoted) | "enteliWEB: Security patch available now for 4.29 and newer. Apply immediately; upgrade 4.28 and older to 4.29 or newer first."; "enteliCLOUD: All instances and the enteliCLOUD Portal have been patched."; "All V4 controller firmware: Security patches in development for 4.18LTS, 4.21, and 4.19 (O3 only)."; "Disable the embedded HTTPS web server by disabling the HTTPS port using network port object NP20001"; PDF CreationDate Thu Oct 22 21:52:38 2026 CEST |
| WP Engine patched | wpengine.com/blog/php-vulnerability-update/ | 11:12–11:13 | raw | "Oct 22, 2026"; "All customer sites are running fully patched versions of PHP."; "by 3:00 AM US Central Time on October 21, we deployed the recommended mitigations"; "we have seen no successful exploit attempts" |
| N-able unchanged in README scope | n-able.com blog | 11:12–11:13 | raw | "Update: October 22, 2026, 18:30 PM EDT … all of our relevant products have been secured against these vulnerabilities and their root causes" (README row updated with this time) |
| Elastic Beanstalk 4.13.13 | docs.aws.amazon.com …/release-2026-10-22-al2023-php82-php83.html | 11:19 (curl at 11:19:25) | raw | "PHP 8.3 AL2023 version 4.13.13"; "PHP 8.3.36 and PHP 8.2.35 address CVE-2026-109618 and CVE-2026-109619" |
| Imunify360 ruleset 8.88 | blog.imunify360.com | 11:09–11:11 | raw diff | "last updated 23 October 2026, 08:40 UTC"; "Ruleset 8.88 is on stable. It includes a new blocking rule, 77049357" |
| TuxCare "Available Now" | tuxcare.com/blog/php2shell-cve/ | 11:09–11:11 | raw diff | "ELS Patches for php2shell Are Available Now" (was "… Are Rolling Out") |
| Laravel Forge all versions | laravel.com/blog/php-critical-vulnerability-response-updates | 11:09–11:11 | raw diff | "Updated 10/23 - 08:31 UTC"; "Patched versions are now available for every PHP version on Forge, from PHP 5.6 to 8.5." (removed: "If you're running PHP 8.0, or 8.1 no patch is available.") |
| Zabbix Docker closed | github.com/zabbix/zabbix-docker/issues/1982 | 11:09–11:11 | raw diff | dotneft (Collaborator), Oct 23: "All latest tags are updated + updated published a few days ago 6.0.49, 7.0.32 and 7.4.16 versions."; "closed this … completed" |
| NCSC-UK wording | ncsc.gov.uk/news/critical-security-issue-affecting-php | 11:09–11:11 | raw diff | added "Prioritise internet-facing systems first and then internal systems." |
| Qualys QID list | blog.qualys.com | 11:13–11:19 | browser (headed) | "Last updated on: October 23, 2026"; "QID 45110 – PHP Server Detected … does not confirm vulnerability"; table incl. 964549 RLSA-2026:87071, 364187 ALAS2023-2026-3304, 765979 SUSE-SU-2026:4844-1, 711202 GLSA 202610-02, 290606 FEDORA-2026-a9eba4bbc3 |
| CloudLinux KB alt-php-internal | cloudlinux.zendesk.com KB 31194180517916 | 11:13–11:19 | browser (headed) | "alt-php-internal … has no rebuilt package yet … not exposed to web requests, so the developers consider it not affected in practice" |
| Render: Docker-only, customer rebuild | render.com/docs/advisory-php2shell | 11:12–11:13 | raw | "All PHP services on Render use Docker, which means you update the PHP installation in your Docker image to patch these vulnerabilities." |
| Unchanged | F5 K000163821 (Updated Oct 23, same table), Check Point sk1000302 (`__NEXT_DATA__` decoded, no diff: "by October 23, 17:00 GMT" / "November 11, 2026"), Citrix r1640 ("Last updated on: October 22"), Quest KB 4385046 ("15.0 CU5 and 15.1 CU2 are now under QA Validation."), Sophos (version 4, 2026 Oct 22), Akamai, QNAP ("Fixing"), Upsun (Monitoring, last 22 Oct 04:12 UTC), Broadcom 39404 (Last Updated 22 October 2026), Plesk API (`edited_at` 2026-10-22T15:58:14Z), Kaseya (statuspage `investigating`, last update 22 Oct 09:29 EDT), Siemens CSAF feed (updated 2026-10-19) | 11:09–11:19 | raw / browser / JSON | as quoted |
| KEV / SSVC / NVD unchanged | KEV JSON, cveawg, NVD API | 11:13 | JSON | KEV catalogVersion 2026.10.21, no entry; SSVC Exploitation none; NVD lastModified 2026-10-22T23:18 |
| Nothing found | Juniper portal search "CVE-2026-109618" ("Results 1-5 of 5", unrelated JSAs); A10 advisories (newest A10-2025-0034, no "PHP"); Adobe bulletins (newest APSB26-170 Substance 3D Stager, -171 Dimension, -172 FrameMaker); Ivanti ICS/PS/vADC/ZTA KB (login page only; a community member quotes a support-ticket reply "identified no impact", not adopted) | 11:13–11:19 | browser (headed) | as quoted |

Update 23 note: the update-22 status line and changelog header said 11:25 UTC, but the last recorded time before the commit was 11:19:25 and the commit was made at 11:21:09 UTC; corrected to 11:21. The "–11:20" range endpoints were likewise unrecorded and corrected.

## Update 24 checks (23 Oct 2026)

Method: the 119 URLs of the update-22 sweep re-downloaded with curl 16:20–16:22 UTC into a fresh directory and diffed line-by-line against the 11:09 UTC copies. Pages that block curl or need JavaScript were re-read in headless Chrome (F5, QNAP, Citrix support 16:25–16:26; NetApp, HPE 16:30–16:31; Adobe, Ivanti, Juniper, Kaseya 16:34–16:35) and in headed Chrome on the kodi desktop session (Sophos, Citrix Tech Zone, Quest, Broadcom 39404, Akamai, CloudLinux KB, Qualys 16:27–16:29). NCSC-NL commits since 23 Oct 11:00 UTC were used as leads only. Times are ranges between `date -u` runs around each batch.

| Claim | Source | UTC (23 Oct) | Method | Evidence |
|---|---|---|---|---|
| CVE-2026-115560 informational advisory | php.net/archive/2026.php | 16:22 | raw | "23 Oct 2026 Informational advisory: Session upload progress … We suggest you set session.upload_progress.enabled=0 until the next regular bugfix release, to fully protect from an unlikely RCE vector." "An application must set session.serialize_handler to php_binary or php_serialize in its configuration and then switch it to php at runtime with ini_set() before calling session_start()." "will publish a full advisory for CVE-2026-115560 with the next release" |
| No records yet for CVE-2026-115560 | NVD API, cveawg.mitre.org, Red Hat VEX URL | 16:22–16:23 | JSON | NVD `totalResults: 0`; MITRE `CVE_RECORD_DNE`; `vex/2026/cve-2026-115560.json` HTTP 404; GitHub php-src advisories: newest are the two 21 Oct GHSAs |
| 8.5.12 does not fix it; WAF rule #6 | blog.cloudflare.com/php-vulnerabilities-waf-protection | 16:20–16:22 | raw diff | "It affects fully patched PHP releases, including 8.5.12, and will be fixed in PHP's next regular release." "Customers who have changed session.upload_progress.name are not covered by the WAF rule." "… #6" protects against this vulnerability |
| CERT-EU v1.2 / CCCS Update 1 | cert.europa.eu 2026-018; cyber.gc.ca AL26-026 | 16:20–16:22 | raw diff | CERT-EU "23/10/2026 --- v1.2 -- Updates with information about a third vulnerability" (its reference [8] is a news site; not used as source). CCCS "Update 1 … The vulnerability is not addressed by the security updates released on October 21, 2026." |
| KEV / SSVC / NVD unchanged | CISA KEV feed, cveawg, NVD | 16:22–16:25 | JSON | KEV catalogVersion 2026.10.21, neither CVE listed; SSVC still Exploitation none (21 Oct); NVD 109618 3.1 9.8 (nvd@nist.gov, Undergoing Analysis); **NVD 109619 3.1 8.1** `CVSS:3.1/AV:N/AC:H/PR:N/UI:N/S:U/C:H/I:H/A:H` (nvd@nist.gov, Analyzed, lastModified 2026-10-23T16:06:48) |
| Cisco v1.5 | sec.cloudapps.cisco.com cisco-sa-php-october26-Jj384Daq | 16:20–16:22 | raw diff | "2026 October 23 16:16 GMT Version 1.5"; "Duo Access Gateway 3.2.0 Duo Access Gateway - Release Notes"; Expressway rows footnote "2. There is a workaround for this product"; "If a product is not listed within this advisory, Cisco's review indicates that the product is not affected by this vulnerability."; CX Cloud, IoT Control Center, Meraki Dashboard, Slido now under "Products Confirmed Not Vulnerable" |
| PAN: Panorama merged into PAN-OS rows | security.paloaltonetworks.com/CVE-2026-109618 | 16:20–16:22 | raw diff | "-Panorama -All -None (ETA: TBD)" removed; rows now "PAN-OS / Panorama 11.2.0 … >= 11.2.10-h16 (ETA: 10/26)"; newest timeline entry still "2026-10-23 Added estimated availability dates (ETAs)…" (no entry for the Panorama change) |
| Fortinet lists | fortiguard.fortinet.com/psirt/FG-IR-26-186 | 16:20–16:22 | raw | "Products Under Investigation: FortiDDoS FortiClient Cloud Services FortiSOAR FortiSOAR PaaS"; "Products confirmed NOT Impacted: … FortiNDR Cloud … FortiMail Workspace Security FortiEDR FortiDDoS-F" |
| Trend Micro interim steps | success.trendmicro.com KA-0024815 | 16:24 | raw | "Make sure the Apex Central is using Build 7328 or later"; "Make sure the Apex One server is at Build 18012 or later"; "These steps are a temporary mitigation. A permanent patch is currently in preparation"; linked from KA-0024802 ("Mitigation Steps (Interim)") |
| Quest KACE port 52230 reversal | support.quest.com KB 4385046 | 16:29 | headed browser | "Note:It has been determined that while port 52230 provides an enhanced level of security for agent communications, a potentially exploitable communication path remains available after the agent tunnel is established. As a precautionary measure, customers are strongly advised to block all inbound web traffic, including ports 80, 443, and 52230"; "KACE SDA 9.3. hotfix queued for QA verification @ 20:02 UTC"; "October 23rd, 2026 Pending update"; "Letzte Aktualisierung am: 10/23/2026" |
| NetApp ONTAP 9 | security.netapp.com/advisory/NTAP-20261021-0021 | 16:30–16:31 | headless browser (tabs clicked) | "Version: 3.0 Last updated: 10/22/2026 Status: Interim"; "ONTAP 9: Affected only by CVE-2026-109618 … restricted to the PHP jail"; Remediation: "None."; three workarounds; revision "2.0 20261021 ONTAP 9 moved to Affected Products" |
| HPE ClearPass unchanged | support.hpe.com HPESBNW05171 | 16:30–16:31 | headless browser | "rev.1 … Last Updated: 2026-10-22"; "patches to fully mitigate … are currently in development" |
| Siemens SSAs | cert-portal.siemens.com/productcert/csaf/ssa-566512.json, ssa-566435.json | 16:24 | CSAF JSON | SSA-566512 known_affected "RUGGEDCOM APE1808 with Palo Alto Networks PAN-OS (10.2 All, 11.1 All, 11.2 All, 12.1 All, 12.2 All)", vendor_fix "Contact customer support to receive patch and update information"; SSA-566435 known_not_affected list (CADRA … Xpedition Layout Browser) |
| Nagios statement | nagios.com/security-disclosures | 16:20–16:22 | raw diff | "NOTICE (Oct. 22, 2026): PHP2Shell Vulnerability (CVE-2026-109618 & CVE-2026-109619) Nagios solutions run on PHP. Customers should immediately apply the PHP security updates provided by their Linux distribution vendor." Not present in the 11:09 UTC copy |
| OPNsense p3 → p4 | forum.opnsense.org topic 53191 | 16:20–16:22 | raw diff | Title now "fix for 26.4.2p4, 26.1.11, 26.7.7"; "Business Edition 26.4.2p4: PHP 8.3.36 / Community Edition 26.1.11: PHP 8.3.36"; post edited "at 01:24:54 PM by franco" |
| RHEL 9.6 EUS / 9.4 E4S | Red Hat CSAF VEX, both CVEs | 16:20–16:23 | JSON | `current_release_date` 2026-10-23T15:24:13; RHSA-2026:88720 → AppStream-9.6.0.Z.EUS `php-0:8.0.30-3.el9_6.2`; RHSA-2026:88725 → AppStream-9.4.0.Z.E4S `php-0:8.0.30-1.el9_4.2`; RHEL 9 known_affected only `…::php:8.4`; RHEL 7 still known_affected for 109619 |
| SUSE Leap 16.0 contradiction, BCI | suse.com/security/cve/CVE-2026-109618.html | 16:20–16:22 | raw diff | "openSUSE Leap 16.0 apache2-mod_php8 >= 8.4.27-160000.1.1 … Patchnames: openSUSE-Leap-16.0-1955"; status table "openSUSE Leap 16.0 php8 Affected"; "Container bci/php:latest php8 >= 8.3.36-150700.3.24.1"; "CVE page last modified: Fri Oct 23 12:55:24 2026" |
| Debian forky still vulnerable | security-tracker.debian.org | 16:31 | raw | "forky 8.4.26-1 vulnerable sid 8.4.27-1 fixed" (Freexian tracker now merges "sid, forky" in one row; Debian tracker used) |
| CloudLinux ea-php PHP.net builds | cloudlinux.statuspage.io incident zl0vt1yq3dj5; blog.cloudlinux.com | 16:20–16:22 | raw diff | "ea-php builds with the PHP.net version numbers are released … ea-php84: 8.4.27-1, for CloudLinux OS 8, 9, 10 and CloudLinux OS for Ubuntu 22.04"; "Posted Oct 23, 2026 - 13:10 UTC" |
| VMware unaffected list | knowledge.broadcom.com/external/article/459989 | 16:20–16:22 | raw diff | "A further list of known unaffected products follows: VMware Cloud Foundation (VCF) and VMware vSphere Foundation (VVF) components and add-ons, versions 5.2.4 and 9.1.1. … VMware Cloud Director VMware Remote Console HCX PowerCLI VMware Telco Cloud Platform VMware Workstation VMware Fusion" |
| Azure Stack Hub | azure.github.io AppService blog | 16:20–16:22 | raw diff | "The above guidance re PHP on App Service Windows also applies for App Service on Azure Stack Hub" |
| Check Point not yet delivered | support.checkpoint.com sk1000302 | 16:37 | raw (`__NEXT_DATA__`) | Unchanged vs 11:09 copy: "by October 23, 17:00 GMT" (deadline not yet reached at check time) |
| Unchanged (browser) | F5 K000163821, QNAP QSA-26-18, Sophos v4, Citrix Tech Zone + support banner, Broadcom 39404, Akamai, Plesk API | 16:25–16:29 | browser / JSON | F5 BIG-IP rows "None" fixes, AI Gateway "**"; QNAP "V1.0 (October 22, 2026)"; Sophos "UPDATED 2026 Oct 22"; Citrix "fixes … on October 27, 2026", "Last updated on: October 22, 2026"; Broadcom revisions end "2026-10-22 04:00 PT"; Plesk `updated_at` 2026-10-23T06:05:47Z, content unchanged |
| Ivanti hub search | hub.ivanti.com/s/searchallcontent#q=CVE-2026-109618 | 16:34–16:35 | headless browser | New result title "Impact of CVE-2026-109618/19 on Incapptic" (snippet "Ivanti Incapptic Connect does not use or contain any PHP code and is therefore NOT …"); article itself not opened; not adopted |
| Not usable this pass | helpx.adobe.com/security.html; kaseya.com/trust-center (redirect to trust.kaseya.com) | 16:34–16:35 | headless browser | no matching text extracted; README keeps the 11:13–11:19 Adobe result |
| Kaseya unchanged | status.kaseya.com/api/v2/incidents.json | 16:41 | JSON | incident tkp9hhttm8xh status "investigating", updated_at 2026-10-22T09:29:32-04:00 |
| Update-24 corrections | own records | 16:41–16:44 | – | browser batch ranges narrowed to recorded `date -u` anchors (16:25:39–16:26:55, 16:27:10–16:29:19, Quest by 16:29:58, 16:30:22–16:31:35); Cisco "also new" list reduced to entries with `+` lines in the 11:09→16:20 diff |

## Update 25 check (23 Oct 2026)

| Claim | Source | UTC (23 Oct) | Method | Evidence |
|---|---|---|---|---|
| Check Point deadline passed, SK unchanged | support.checkpoint.com/results/sk/sk1000302 | 18:24 | raw (`__NEXT_DATA__`) | extracted text identical to the 16:37 copy (empty diff, same 38141 bytes); still "Check Point is expecting to deliver a permanent fix based on the latest PHP code by October 23, 17:00 GMT."; `"lastModified":"2026-10-23"` |
| CPAI-2026-15172 unchanged | advisories.checkpoint.com | 18:24 | raw diff | empty diff against the 16:20 copy |

## Update 26 checks (24 Oct 2026)

Method: the 125 URLs of the update-24 sweep (`urls4`, `urls_new`, `urls5l`) re-downloaded with curl 06:16:15–06:18:08 UTC into fresh directories and diffed line-by-line against the 23 Oct 16:20–16:22 UTC copies. Pages that block curl or need JavaScript were re-read in headless Chrome (F5 06:16–06:18 and 06:32–06:33; QNAP, NetApp, HPE 06:23–06:24; Juniper 06:24; Citrix support, Ivanti, Adobe 06:24–06:27) and in headed Chrome on the kodi desktop session (Sophos, Quest 06:27–06:28; Citrix Tech Zone, Broadcom 39404, Akamai, CloudLinux KB, Qualys 06:28–06:29). Times are ranges between printed `date -u` runs around each batch. NCSC-NL: no commit since 23 Oct 12:50 UTC.

| Claim | Source | UTC (24 Oct) | Method | Evidence |
|---|---|---|---|---|
| F5 fixes, article Final | my.f5.com K000163821 | 06:16–06:17 | headless browser | "Published Date: Oct 21, 2026Updated Date: Oct 24, 2026"; "Final- This article is marked as 'Final' …"; "BIG-IP APM 21.x 21.1.0 21.1.0.4 High/8.1 … 17.5.0 - 17.5.1 17.1.0 - 17.1.3 17.5.1.11 17.1.3.7"; "BIG-IP (all modules) … High/7.5 … Control plane: The Configuration utility"; "F5 AI Gateway All None Not applicable Not vulnerable"; "ASM-AttackSignatures_20261022_154742.im or later" |
| F5 release list | my.f5.com K000163848 | 06:17–06:18 | headless browser | "BIG-IP Next for Kubernetes: 2.4.2 BIG-IP TMOS BIG-IP: 17.1.3.7 BIG-IP: 17.5.1.11 BIG-IP: 21.1.0.4" (K000163821 lists Next for Kubernetes as "Not vulnerable") |
| F5 CVE-2026-115560 | my.f5.com K000163878 | 06:17–06:18, 06:32–06:33 | headless browser | "Published Date: Oct 23, 2026Updated Date: Oct 24, 2026"; "BIG-IP (all modules) 21.x ** … 17.x ** … BIG-IQ Centralized Management 8.x **"; "/etc/php.ini.d/K000163878.ini … ; These will NOT survive an upgrade of BIG-IP TMOS. session.upload_progress.enabled = 0" |
| F5 quote removed | my.f5.com K000163821 | 06:32–06:33 | headless browser | "authenticated users" not found in the current text (no saved copy of the earlier text; README now quotes only the current text) |
| Unit 42 post-exploitation case | unit42.paloaltonetworks.com | 06:16–06:18 | raw diff | "Updated October 23, 2026, at 12:30 p.m. PT to add details on agentic AI post-exploitation activity"; "In one case, the attackers targeted a government entity in Europe and within two hours of the initial exploitation they had successfully accessed password hashes and multi-factor authentication secrets."; still "Unit 42 has seen proof of concept of these vulnerabilities"; "over 22.6 million exposed instances" |
| Zscaler telemetry, corporate env. cleared | zscaler.com ThreatLabz blog | 06:16–06:18 | raw diff | "*October 23, 2026: This advisory has been updated …"; "scanning activity and possible exploitation attempts"; "observed 1,156 exploitation attempts from 156 unique attacker IPs targeting 70 organizations"; "has ruled out any impact to Zscaler Cloud Platforms, products, distributed components, services, or our enterprise environment" |
| Google / Mandiant guidance | cloud.google.com blog | 06:16–06:18 | raw diff | "on Oct. 23, 2026 at 3:20 p.m. PDT, with additional guidance from Mandiant Consulting"; "capture worker memory before patching or rebooting"; "23 new curated detections added to the Mandiant Frontline Threats rule pack" |
| Datadog PoC analysis | securitylabs.datadoghq.com | 06:16–06:18 | raw diff | "Multiple public PoCs have demonstrated other code paths with the same flaw"; "Based on an analysis of multiple public PoCs, the majority begin with a similar multipart form upload" |
| KEV / SSVC / NVD / 115560 records | CISA KEV feed, cveawg, NVD API, Red Hat VEX URL, GitHub | 06:20 | JSON | KEV catalogVersion 2026.10.23, neither CVE listed; SSVC "Exploitation: none" (timestamp 2026-10-21); NVD 109618 `vulnStatus` "Analyzed", lastModified 2026-10-23T16:26:54; 115560: NVD `totalResults` 0, MITRE `CVE_RECORD_DNE`, VEX HTTP 404; newest php-src GHSAs still the two of 21 Oct |
| Check Point hotfix | support.checkpoint.com sk1000302 | 06:22 | raw (`__NEXT_DATA__`) | "October, 23, 2026 at 18:30 GMT update: Check Point provided a Hotfix for CVE-2026-109618 and CVE-2026-109619. See the Solution section."; "This Hotfix implements the PHP 7.4 published fix"; "R82.20 Coming soon R82.10 (TAR) R82.10 for 3900 Appliances (TAR) R82 (TAR) R81.20 (TAR)"; "The fix is also planned for the release on November 11, 2026"; `"lastModified":"2026-10-23"` |
| CPAI unchanged | advisories.checkpoint.com cpai-2026-15172 | 06:22 | raw diff | empty diff against the 23 Oct 18:24 copy (same 97243 bytes) |
| PAN WF-500, Panorama note, new not-affected | security.paloaltonetworks.com/CVE-2026-109618 | 06:16–06:18 | raw diff | "Updated 2026-10-24"; "WildFire Appliance WF-500 and WF-500-B None All"; timeline "Also made the correction to the status of WildFire Appliance WF-500 and WF-500-B impact"; "This issue is applicable to PAN-OS software on PA-Series and VM-Series firewalls and on Panorama (virtual and M-Series)"; Prisma SD-WAN ION/Controller/On-Prem Controller, Next Generation Trust Security, Trust Protection Foundation "None All"; "2026-10-24 Added updated threat signature and content version release details" |
| Cisco v1.6 | sec.cloudapps.cisco.com | 06:16–06:18 | raw diff | "2026 October 23 22:39 GMT Version 1.6"; "Updated to indicate that workarounds are available. Updated products under investigation and products confirmed not vulnerable."; Catalyst Center, WAE, AppDynamics Enterprise Console / Virtual Appliance, Nexus Dashboard now under "Products Confirmed Not Vulnerable"; 11 products under investigation |
| Juniper JSA112681 | supportportal.juniper.net | 06:24 | headless browser (link from HPE bulletin) | "Article ID JSA112681 Created 2026-10-23"; "Junos is vulnerable to CVE-2026-109618 and is being upgraded to PHP 8.5.12 to resolve this issue. For affected systems, the recommended mitigation is to disable J-Web, JSC, and fwAuth."; "SRX does not use PHP starting with 25.2R1"; "Junos OS Evolved (EVO) Not Vulnerable. Session Smart Router Not Vulnerable."; "Junos Space Not Vulnerable."; "Other products not listed above are still under investigation." |
| HPE ClearPass rev.2 | support.hpe.com HPESBNW05171 | 06:23–06:24 | headless browser | "Last Updated: 2026-10-24 … Document Version: 2"; "ClearPass 6.14.1 (released on Sep 29, 2026) and below"; "ClearPass 6.14.1 Hotfix Patch to Address PHP Vulnerabilities …"; "Final hotfixes have been released and address the issue completely."; "Version:2 (rev.2) - 23 October 2026 Revised to address Hotfix Releases and update Unaffected Products section." |
| Quest KACE SMA fixed | support.quest.com KB 4385046 | 06:27–06:28 | headed browser | "KACE SMA 15.0 CU5 (15.0.378) and 15.1 CU2 (15.1.177) addressing the PHP2Shell vulnerabilities … are now available"; "publication and immediate global advertisement @ 17:03 UTC"; "KACE SDA 9.3 hotfix ETA Tuesday October 27th"; "CVE-2026-115560 … has been confirmed to not impact the KACE SMA and SDA systems" |
| Barracuda status table | trust.barracuda.com | 06:16–06:18 | raw diff | "SecureEdge Patch released Apply the patch immediately"; "Firewall Insights Patch released"; "CloudGen Firewall Not affected"; "Email Gateway Defense Remediated"; "Cloud Control … Remediated"; "Managed XDR (MXDR) Under investigation" |
| Broadcom ESG | support.broadcom.com notification 39404 | 06:28–06:29 | headed browser | "Last Updated 23 October 2026"; "2026-10-23 11:00 PT - CloudSOC SpanVA Appliance added to Affected and Symantec Protection Engine (SPE) Console added to Not Vulnerable"; "2026-10-23 12:00 PT - CloudSOC Cloud Access Security Broker (CASB) moved to Not Vulnerable"; "under investigation: Content Analysis" |
| Trend Micro DDI/DDAN/DDEI ETAs | success.trendmicro.com KA-0024802 | 06:16–06:18 | raw diff | "Critical Patch ETAs: - DDI : 10/30 - DDAN: 10/30 - DDEI: 10/30"; "Addressed via emergency maintenance (10/23)"; "Last updated: 2026/10/24" |
| Kaseya product table | status.kaseya.com/api/v2/incidents.json | 06:22 | JSON | incident status "identified", update 2026-10-23T16:20:50-04:00: "Kaseya has completed an evaluation of its product portfolio"; "VSA 10 - Fully Patched"; "VSA 9 - Compensating Controls"; "IT Glue - Unaffected"; permalink stspg.io/3qgdm5yjrc2b |
| Ivanti Incapptic, Service Manager | hub.ivanti.com KB 000109797, 000109785 | 06:24–06:27 | headless browser | "Ivanti Incapptic Connect does not use or contain any PHP code and is therefore NOT impacted"; "Ivanti Service Manager products do not use or have PHP repos loaded on them and therefore are NOT impacted" (Article Number 000109785); Connect Secure KB: "Invalid page or you need to log in" |
| Red Hat new errata | Red Hat CSAF VEX, both CVEs | 06:16–06:18 | JSON | `current_release_date` 2026-10-24T00:27:42 / 00:28:19; RHSA-2026:88693 → 7Server-ELS `php-0:5.4.16-48.el7_9.1` (incl. x86_64), CVE-2026-109619 only; RHSA-2026:88659 → AppStream-9.2.0.Z.E4S `php-0:8.0.30-1.el9_2.2`; RHSA-2026:88834 → 9.6 EUS php:8.2 `8.2.28-1`; RHSA-2026:88835 → 9.4 E4S php:8.2 `8.2.13-1`; RHEL 9 `known_affected` still only `::php:8.4`; RHEL 7 no longer in 109619 `known_affected` |
| RHSB on RHEL 7 | access.redhat.com RHSB-2026-013 | 06:16–06:18 | raw diff | "October 23, 2026, 13:15"; "This is the single most effective change and the only one required on Red Hat Enterprise Linux 7."; "Uncommenting the shipped line leaves the feature enabled." |
| CIQ all variants patched | kb.ciq.com | 06:16–06:18 | raw diff | "Patched PHP packages are available for all supported CIQ variants as of 2026-10-23."; LTS 8.6 "php-7.4.33-8 (php:7.4), php-8.2.35 (php:8.2)"; Bridge "php-5.4.45-1.2.el7_9.ciqcbr"; "CIQ has backported the fix into the Bridge PHP package" |
| Debian forky fixed | security-tracker.debian.org | 06:16–06:18 | raw diff | "forky, sid 8.4.27-1 fixed" (was "forky 8.4.26-1 vulnerable") |
| CloudLinux php-els reversal | cloudlinux.statuspage.io, blog.cloudlinux.com, blog.imunify360.com; cloudlinux.zendesk.com KB | 06:16–06:18; KB 06:28–06:29 | raw diff; headed browser | "Correction: keep the ELS ALT PHP repository enabled … That is not correct. Please keep the repository enabled." (Posted Oct 23, 2026 - 21:36 UTC); KB ("23 hours ago Updated") still: "dnf config-manager --set-disabled php-els" |
| AWS EMR, all regions | aws.amazon.com bulletin 2026-143 | 06:16–06:18 | raw diff | "10/23/2026 13:30 PM PDT"; "Amazon EMR on EC2 clusters launched with Ganglia included in the application set are affected, specifically EMR releases 4.2.0–5.29.0 and 5.30.0–6.15.0"; "Updated PHP packages are available for all regions."; "Bref has published a security release" |
| Tenable SC-202610.2 | tenable.com TNS-2026-30, TNS-2026-31; Tenable FAQ blog | 06:33; blog 06:16–06:18 | raw | "Stand-alone Security Patch Available for Tenable Security Center Versions 6.6.0, 6.7.2, 6.8.0, 6.9.1: SC-202610.2"; "php to version 8.2.35"; Enclave Security 1.7.0, 1.8.0, 1.9.1 |
| Rapid7 / Qualys coverage | rapid7.com ETR blog; blog.qualys.com | 06:16–06:18; 06:28–06:29 | raw diff; headed browser | Rapid7: "authenticated scan checks for both the Scan Engine and the Agent"; "released coverage for CVE-2026-115560"; "scope for authenticated coverage: macOS and Linux. Windows to follow."; Qualys: "389141 … (CVE-2026-115560) To be released soon" |
| Unchanged | QNAP QSA-26-18, NetApp NTAP-20261021-0021, Sophos, Citrix support + Tech Zone, Akamai, Plesk API, Fortinet, SonicWall, A10, Icinga, Siemens CSAF | 06:16–06:29 | browser / raw diff / JSON | QNAP "V1.0 (October 22, 2026)"; NetApp "Version: 3.0 Last updated: 10/22/2026", Remediation "None."; Sophos "UPDATED 2026 Oct 22 ARTICLE VERSION 4"; Citrix "fixes … on October 27, 2026", "Last updated on: October 22, 2026"; Plesk `edited_at` 2026-10-22T15:58:14Z, body unchanged; Fortinet diff only "Linksys Products" (site navigation) |
| Juniper portal search misses JSA112681 | supportportal.juniper.net global search "CVE-2026-109618" | 06:42–06:43 | headless browser | "Results 1-5 of 5 for CVE-2026-109618": JSA110075, JSA110076, JSA110091, JSA112187, JSA110078 (all unrelated); JSA112681 not listed (anonymous session) |
| CISA alert update | cisa.gov alert 2026/10/21 | 06:42 | raw | "Update October 23, 2026"; "provide a SIGMA detection rule"; "While CISA has not observed successful exploitation of these vulnerabilities in the wild as of the time of publication" |
| F5 attacker model | my.f5.com K000163821 | 06:16–06:17 | headless browser | "APM Data Plane This vulnerability may allow a remote unauthenticated attacker to execute arbitrary system commands"; "Control Plane This vulnerability may allow a remote authenticated attacker …" |
| Sources outside the sweep | Splunk SVD-2026-1013, Siemens ProductCERT news, SolarWinds, Upsun, Fastly, Corelight, LibreNMS docker, Broadcom protection bulletin, Elastic Beanstalk notes | 06:42 | raw (no older copy) | Splunk "Last Updated: 2026-10-23", "Currently, no Splunk products are known to be affected"; Siemens "We are evaluating the impact to Siemens products"; SolarWinds "Affected Products SolarWinds Pingdom and SolarWinds External Websites"; Upsun "resolved incident" |
| Not usable this pass | helpx.adobe.com security bulletins | 06:24–06:27 | headless browser | HTTP 403 "Access Denied"; README keeps the 23 Oct 11:13–11:19 UTC result |

## Update 27 checks (24 Oct 2026)

Method: the 132 distinct URLs of the sweep (update-24 lists plus the ten sources added in update 26) re-downloaded with curl 21:53:45–21:56:08 UTC and diffed line-by-line against the 24 Oct 06:16–06:18 UTC copies (the ten update-26 sources against their 06:42 UTC copies). Earlier method lines said "125 URLs"; that counted list lines, incl. one blank line and two duplicate URLs. Browser-only pages re-read in headless Chrome (F5 21:57–21:59; QNAP, HPE, Juniper, Ubiquiti, NetApp, Citrix support, Ivanti hub search, Adobe 21:59–22:01) and headed Chrome on the kodi desktop session (Sophos, Quest, Citrix Tech Zone, Broadcom 39404, Akamai, CloudLinux KB, Qualys 22:01–22:04). Times are ranges between printed `date -u` runs. No copies of browser-only pages from update 26 exist, so those were compared against the quotes logged in update 26.

| Claim | Source | UTC (24 Oct) | Method | Evidence |
|---|---|---|---|---|
| QNAP OS fixes (V1.1) | qnap.com QSA-26-18 | 21:59–22:01 | headless browser | "V1.1 (October 24, 2026) - QTS、QuTS hero and QuTScloud Resolved Published"; "QTS 6.1.0 Resolved QTS 6.1.0.3656 build 20261023"; "QTS 5.2.11 and earlier Resolved QTS 5.2.11.3661 build 20261023"; "QuTS hero h6.0.x Resolved QuTS hero h6.0.2.3656 build 20261023"; "QuTScloud c5.2.9 and earlier Resolved c5.2.9.3661 build 20261023"; "Note Station 3 3.9.14 and earlier Fixing To be announced" (same for QNE, QVR Surveillance, TVR OS); QuMagie not in the fix table; "QNAP has not received reports of exploitation targeting QNAP products" |
| NetApp ONTAP fixes (v4.0) | security.netapp.com NTAP-20261021-0021 | 21:59–22:01 | headless browser, all tabs clicked | Remediation: "First Fixed in Release ONTAP 9" with download links `…/62286/9.16.1P16HF1` and `…/62286/9.17.1P11HF1`; Revision History: "4.0 20261024 ONTAP 9.16.1P16HF1 and 9.17.1P11HF1 added to Software Versions and Fixes" |
| Ubiquiti UISP 3.1.70 | uisp.community.ui.com release notes | 21:59–22:01 | headless browser (lead: NCSC-NL PR #44) | "This hotfix includes security updates for the PHP and Node.js runtimes used by the UISP application. It addresses CVE-2026-109618 and CVE-2026-109619 in the PHP runtime used by the UISP CRM module."; "We recommend updating promptly"; page date "Oct 23, 2026". Comments under the release are not quoted |
| GetPageSpeed EL7 builds | getpagespeed.com/php2shell | 22:04 | curl (lead: NCSC-NL PR #46) | "Updated October 24, 2026"; "GetPageSpeed rebuilt every one of them with PHP2Shell fixed. Package names stay the same, so yum upgrade replaces them in place"; table `5.6.40-44.el7` … `8.4.27-3.el7`. The page also says "Exploited in the wild"; not adopted (no primary evidence; KEV/SSVC say otherwise) |
| Rapid7 product status | docs.rapid7.com/insightvm/rapid7-status-php2shell | 21:56 | curl (new link in the Rapid7 blog) | "Last updated: October 23, 2026"; "no customer action is required on the Rapid7 modules, features, and services listed below"; eight modules "Not affected – Does not use the affected PHP components"; Command Platform, MVM/MTC "No action required – No PHP usage" |
| Qualys QIDs | blog.qualys.com | 22:01–22:04 | headed browser | "Last updated on: October 24, 2026" (no earlier copy of the page exists, so which QIDs are new on 24 Oct is unknown); table incl. "6297246 Debian Security Update for php8.2,php8.4 (CVE-2026-109618)", "6877310 / 6877311 Ubuntu … (USN-8948-1/-2)", "6567432–6567434 Alpine Linux 3.24", "6101335 / 6101336 Arch Linux", Rocky 964518/964520/964542/964543, Amazon Linux 364180–364182; CVE-2026-115560 QIDs 39036 and 389141 still "To be released soon" |
| F5 unchanged | my.f5.com K000163821, K000163878, K000163848 | 21:57–21:59 | headless browser | K000163821 "Updated Date: Oct 24, 2026", Final, same fix table; K000163878 "BIG-IP (all modules) 21.x ** … 17.x ** … BIG-IQ Centralized Management 8.x **"; K000163848 "Updated Date: Oct 23, 2026", same release list |
| Unchanged, browser | HPE HPESBNW05171 (Document Version 2), Juniper JSA112681 (last log entry "2026-10-23: Updated Mist status"), Citrix support notice and Tech Zone ("Last updated on: October 22, 2026", fixes 27 Oct), Sophos, Quest KB 4385046 (SDA ETA 27 Oct), Broadcom 39404 (last entry 2026-10-23 12:00 PT), Akamai, CloudLinux KB (still shows `--set-disabled php-els`), Ivanti hub search (no new Ivanti KB) | 21:59–22:04 | browser | — |
| Unchanged, raw diff | all other sweep URLs, incl. PAN, Cisco, Check Point SK, Trend Micro, Barracuda, Unit 42, Zscaler, Tenable, CISA alert, Splunk, Siemens news, SolarWinds | 21:53–21:56 | raw diff | Only counters, reaction lists, related-article teasers or ordering changed. Red Hat errata 87072/87079/87080/87151: product list extended or re-ordered, "Issued/Updated 2026-10-21" unchanged; VEX unchanged. aaPanel forum post: install commands and "(test first recommended)" removed, "All four versions are now updatable via the App Store" added (README row updated). RHSA 87072/87151 new lines (e.g. `php-8.2.35-1.module+el9.8.0+25111`, `php-common-8.0.30-8.el9_8.1`) are additional product listings of builds already in the errata; no line was removed |
| Feeds | CISA KEV, NVD, cveawg.mitre.org, Red Hat VEX, Kaseya statuspage API, Plesk API, NCSC-NL commits (open PRs 21:57–22:04) | 21:57 | JSON | KEV "2026.10.23" (released 2026-10-23T19:30:18Z), neither CVE listed; NVD 109618/109619 "Analyzed"; SSVC "Exploitation: none"; CVE-2026-115560: CVE record 404, NVD empty, VEX 404; Kaseya incident last update 2026-10-23T16:20:50-04:00; Plesk `updated_at` 2026-10-23T22:34:58Z unchanged; NCSC-NL newest commit 2026-10-23T12:50:49Z |
| No statement | Cacti, LibreNMS GitHub releases and security advisories | 22:04 | GitHub API | Cacti newest release 1.2.31 (June 2026), no PHP2Shell advisory; LibreNMS 26.10.2 (21 Oct), newest advisories 23 Sep |
| Not usable | helpx.adobe.com | 21:59–22:01 | headless browser | HTTP 403 "Access Denied" |

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
