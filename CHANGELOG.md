# Changelog

> AI-generated document; see the warning in [README.md](README.md).

## Editorial – 27 Oct 2026, 16:50 UTC

README condensed from about 12,300 to about 5,900 words. **No status changes and no new checks**; the data is still that of update 29 (06:25–06:53 UTC).

- Removed from the README: change history inside rows ("moved from …", earlier wording, corrections), per-source check times (kept in VERIFICATION.md), repeated lists (PAN hotfixes now listed once), long not-affected lists (now a selection plus "full list: advisory").
- Key facts: CVE-2026-115560 vendor statements moved to their rows; exploitation block shortened to KEV, confirmed shells, attempts, PoCs and "not observed" statements.
- Known gaps rewritten as a short list by category.
- Every quote left in the README is a verbatim substring of the update 29 text; all fixed versions, advisory IDs and links to sources were kept, except history-only details.
- `UPDATE_PROMPT.md`: new rule against re-adding history and check times to the README.

## Update 29 – 27 Oct 2026, 06:53 UTC

Re-check of all 127 in-scope sweep URLs (curl diff 27 Oct 06:25–06:27 UTC against the 26 Oct 08:17–08:19 UTC copies), browser-only pages 06:33–06:39 UTC (diffed against the saved 26 Oct copies), feeds and APIs 06:28–06:47 UTC, then README quotes matched against today's texts (scope and exceptions in VERIFICATION). Details in [VERIFICATION.md](VERIFICATION.md#update-29-checks-27-oct-2026).

- **Correction (same update, follow-up commit):** the status line, this entry and VERIFICATION claimed "every" quote was matched; the per-line check skipped lines without a swept URL. Those quotes were then checked across all of today's texts; scope and exceptions are now stated. The Splunk row said the old wording held "until 23 Oct"; it was still in the 26 Oct 08:17 UTC copy. Trend Micro's Nov. 11 ETA and PAN's Cortex Cloud entry are marked as "seen 27 Oct" (no change date known); the Cacti / LibreNMS check time is a range.
- **CISA KEV: both CVEs added on 26 Oct**, due date 29 Oct (BOD 26-04), forensic triage "Yes". The CISA alert was updated and no longer says CISA has not observed exploitation. CISA SSVC in the CVE record still says "Exploitation: none". CVE-2026-115560 is not in KEV.
- **Successful exploitation on honeypots:** Adel Karimi's report (24 Oct): 35 shells started by Apache workers on three PHP 8.4.26 `mod_php` honeypots, matching the public PoCs (the report warns this is no measure of reliability elsewhere). Trail of Bits (26 Oct): demo shell on MediaWiki, Symfony, Laravel and phpBB. Zscaler and Sansec softened their wording.
- **Palo Alto: 11 of 20 PAN-OS hotfixes released** (new: `10.2.13-h27`, `10.2.16-h12`, `12.1.7-h11`, `12.2.4-h1`); 9 still due 27–30 Oct. New suggested-solution table; the separate Node.js Brotli CVE is fixed in the same hotfixes except `11.2.10-h16`. Cortex Cloud and Koi not affected.
- **Check Point: gaps closed.** R82.20 hotfix (also for 3900 appliances) and Spark R81.10.17 Build 996004992 released; hotfixes now support Standalone; new deploy steps (remove the manual mitigation first). The Spark R82.00.x package is now labelled R82.00.11 (same build 998002823).
- **NetApp v9.0:** ONTAP 9.14.1P18HF1 added (six lines fixed); workaround steps moved to a KB that needs a login; NetApp recommends upgrading instead of workarounds.
- **F5:** engineering hotfixes for BIG-IP 17.5.1.10 and 17.1.3.6 carry the PHP fix.
- **Citrix:** security bulletin CTX697263 (created 22 Oct, first listed in the KB search on 27 Oct): NetScaler ADC / Gateway impacted, 14 other Citrix products not impacted. Fix still due 27 Oct, not out at 06:39 UTC.
- **Cisco v1.7:** Expressway fix 15.5.21 no longer "TBD"; under investigation down from 11 to 4 products.
- **New Splunk row:** investigation complete, all products unaffected, Smartlook remedied.
- **Other changes:** Fortinet (FortiClient Cloud Services remediated), WatchGuard (final "none affected" plus IPS signatures, also in section 2), Barracuda (Security Awareness Training remediated), Broadcom (KB 459989 rewritten; CASMA under investigation, CAS not vulnerable), Trend Micro (Apex Central / Apex One Critical Patch ETA 11 Nov), Juniper (Apstra not vulnerable), Siemens (SSA-566435 v2, new SSA-166980), Kaseya (Autotask PSA, Datto RMM, Endpoint Backup V2 fully patched), Red Hat (RHSA-2026:89111, 9.6 EUS php:8.3), CIQ (LTS 9.2 php:8.2/8.3), SUSE Liberty 9.6 EMS, Qualys (new web-app QIDs, one intrusive), Azure WAF (request size guidance), Laravel Forge (upload progress off on new servers).
- **CloudLinux contradiction resolved:** the KB now also says to keep `php-els` enabled; `alt-php-internal` fixed in 8.2.35-1.
- **Late additions (missed since 21–22 Oct):** PHP regression php-src #24488 in 8.4.27 / 8.5.12 (SimpleXML GC double free; fix committed 22 Oct, not released). Also noted: the PHP Windows `-1` builds of 26 Oct fix a separate Brotli CVE, not PHP2Shell.
- **Corrections:** removed vendor text no longer quoted as current (CISA "not observed", Broadcom VMware list, NetApp workaround text, Laravel Forge instructions, Sansec and Zscaler wording); Citrix Tech Zone quote completed; Trend Micro ETA quote reformatted to the source; the earlier "No CTX bulletin found" removed.
- Unchanged: Unit 42, Amazon, watchTowr, Sophos, HPE, Quest (SDA hotfix due 27 Oct), Akamai, Plesk, Cacti / LibreNMS; NCSC-NL no new commit. Not re-read: Adobe (HTTP 403), login-gated Ivanti / Broadcom KBs and the NetApp KB steps, Juniper portal search, Surý, Fortinet IPS encyclopedia, Upsun incident text.

## Update 28 – 26 Oct 2026, 08:29 UTC

Re-check of all 132 sweep URLs (curl diff 26 Oct 08:17–08:19 UTC against the 25 Oct 15:00 UTC copies of an unpublished intermediate pass), browser-only pages 08:21–08:26 UTC (now diffed against saved full-text copies), feeds and APIs 08:20 UTC. Details in [VERIFICATION.md](VERIFICATION.md#update-28-checks-2526-oct-2026).

- **Scope: non-enterprise rows removed.** aaPanel, HestiaCP, ISPConfig, DirectAdmin, QNAP, Synology, Ubiquiti UISP, FreePBX/Sangoma, GetPageSpeed, Fedora, Debian forky/sid, Arch and Gentoo are no longer tracked (also removed: their scanner QIDs, the Fedora source link, the QNAP entries in key facts and known gaps). Section 6 now holds hosting control panels (Plesk, cPanel), collaboration servers, Alpine and other software. `UPDATE_PROMPT.md` lists the excluded categories.
- **Unit 42 retracted its exploitation case.** On 25 Oct it withdrew the 23 Oct report of an attack on a European government entity: "We are unable to confirm that initial access is associated with the specific PHP2Shell CVEs." The key-facts bullet now says so. The other exploitation reports (Amazon, watchTowr, Cloudflare, Zscaler) are unchanged.
- **Palo Alto: 7 of 20 PAN-OS hotfixes released** (`10.2.18-h13`, `11.1.4-h38`, `11.1.6-h40`, `11.1.10-h36`, `11.1.13-h16`, `11.1.16-h4`, `11.2.10-h16`). The rest are due 27–30 Oct. PAN says CVE-2026-115560 does not affect PAN-OS.
- **NetApp v7.0:** fixes for ONTAP 9.15.1, 9.16.1, 9.17.1, 9.18.1 and 9.19.1 (`…HF1` builds). The advisory status is still *Interim*.
- **Check Point:** hotfix for Spark Firewalls (R82.00.10 Build 998002823). R82.20 is still "Coming soon"; there is no package for Spark R81.10.x.
- **Broadcom:** Carbon Black App Control Server is fixed in 8.12.2 and 8.13.2 (public KB 459982).
- **Ivanti Endpoint Security added:** affected; end of life 31 Dec 2026, Ivanti recommends migration; the mitigation article needs a login.
- **Trend Micro:** Vision One Container Security and Deep Discovery Director listed as not impacted.
- **SUSE:** BCI PHP container images now have fixed version tags (`8.3.36-28.14` / `-28.15`).
- **ownCloud and Cleo Streem added:** fixed ownCloud 10/11 Docker images (22 Oct); Cleo Streem patch available through Cleo support (21 Oct).
- **LibreNMS Docker 26.10.2-r2** disables `session.upload_progress` against CVE-2026-115560.
- **Late addition:** Surý (sury.org, ondrej PPA) also backported the fix to PHP 5.6, 7.0, 7.1, 7.2 and 7.3 on 21 Oct. It was missing from the row since then.
- **Correction (same update, follow-up commit):** the Surý row header now says 5.6–8.5 and names Debian 11 / Ubuntu 22.04; Ivanti Endpoint Security is listed as "affected, no fix announced" (it was under "fix in development"); the status line no longer lists OVHcloud (out of scope) as a new source.
- **Corrections:** update 27 dropped the NetApp "*Interim*" status (restored). Qualys QID 39036 (CVE-2026-115560, unauthenticated) was missing from the scanner row. The Cacti/LibreNMS row still showed the 23 Oct check time.
- Unchanged: F5, HPE, Juniper, Citrix (fix due 27 Oct), Quest (SDA hotfix due 27 Oct), Sophos, Akamai, CloudLinux, Kaseya, CISA KEV / SSVC ("Exploitation: none"), Red Hat VEX, NVD; CVE-2026-115560 still has no CVE record. Adobe again HTTP 403.

## Update 27 – 24 Oct 2026, 22:06 UTC

Re-check of all 132 sweep URLs (curl diff 21:53–21:56 UTC against the 24 Oct 06:16 UTC copies; the ten update-26 sources against their 06:42 UTC copies), browser-only pages 21:57–22:04 UTC, feeds 21:57 UTC.

- **QNAP V1.1:** QTS, QuTS hero and QuTScloud fixed (builds of 20261023). Note Station 3, QNE (ADRA), QVR Surveillance and TVR OS are still "To be announced". QuMagie is in the affected list but not in the fix table.
- **NetApp v4.0:** ONTAP 9.16.1P16HF1 and 9.17.1P11HF1 fix the issue. Other ONTAP 9 lines have no fix named yet.
- **Ubiquiti UISP added:** UISP Application 3.1.70 fixes both CVEs in the PHP runtime of the UISP CRM module.
- **GetPageSpeed added** (Linux repositories): fixed EL7 rebuilds of Remi's PHP 5.6–8.4 packages for CentOS 7.
- **Rapid7:** product status page; none of its products are affected.
- **Qualys:** blog header now "Last updated on: October 24". The README now also lists Qualys distro QIDs for Debian, Ubuntu, Alpine and Arch, and more Rocky and Amazon Linux QIDs (no earlier copy of the page, so which of them are new is unknown). CVE-2026-115560 QIDs are still "To be released soon".
- **aaPanel:** older 7.x builds now via the App Store; install script commands removed from the post.
- **Known gaps:** QNAP and NetApp moved from "fix announced" / "workarounds only" to the remaining products only.
- **Correction (same update, follow-up commit):** aaPanel row updated (had been wrongly logged as "no row"); diff baseline of the ten update-26 sources (06:42 UTC) and the NCSC-NL PR check time (21:57–22:04 UTC) stated correctly; Qualys QIDs no longer called new.
- **Counting fix:** earlier status lines said "125 URLs"; that counted list lines incl. one blank line and two duplicates. The sweep now covers 132 distinct URLs, incl. the ten added in update 26, which are now diffed.
- **Unchanged:**
  - F5 (K000163821 Final, CVE-2026-115560 still researched), PAN (no hotfix yet, ETAs 26–30 Oct), Cisco v1.6, Check Point, Juniper, HPE, Quest, Citrix (fixes 27 Oct), Sophos, Broadcom, Kaseya, Trend Micro, Barracuda, CloudLinux contradiction.
  - KEV catalog 2026.10.23 lists neither CVE; SSVC "Exploitation: none"; Red Hat VEX unchanged.
  - CVE-2026-115560 still has no CVE record, NVD entry or Red Hat VEX. NCSC-NL: no new commit since 23 Oct 12:50 UTC.
- **Not verified / not re-read:** Adobe (HTTP 403 again), login-gated Ivanti and Broadcom detail KBs, Juniper portal search (last run 06:42 UTC).

## Update 26 – 24 Oct 2026, 06:36 UTC

Re-check of all 125 sweep sources (curl diff 06:16–06:18 UTC against the 23 Oct 16:20 UTC copies, browser-only pages 06:16–06:33 UTC, feeds). F5 was checked first on request.

- **F5: fixes released.** BIG-IP 21.1.0.4, 17.5.1.11 and 17.1.3.7 (Critical Release of 23 Oct, K000163848). K000163821 is now marked "Final"; F5 AI Gateway moved to not vulnerable. New K000163878 for CVE-2026-115560: BIG-IP and BIG-IQ are still being researched. F5's `.ini` mitigation files do not survive a TMOS upgrade, so check `session.upload_progress.enabled` again after upgrading. The README no longer quotes "legitimate, authenticated users", which is not in the current text. Inconsistency flagged: K000163848 lists BIG-IP Next for Kubernetes 2.4.2, a product K000163821 calls not vulnerable.
- **Exploitation (Key facts):**
  - Unit 42 (upd. 23 Oct) describes a post-exploitation case at a European government entity: password hashes and MFA secrets taken within two hours of initial exploitation. The paragraph does not name the initial access vector.
  - Zscaler decoys: 1,156 exploitation attempts from 156 IPs against 70 organisations in the first 48 hours.
  - Google/Mandiant forensics guidance; Datadog analysis of multiple public PoCs.
  - KEV catalog 2026.10.23 still lists neither CVE; CISA SSVC still "Exploitation: none".
- **Check Point: hotfix released.** "October, 23, 2026 at 18:30 GMT update", for R82.10 (incl. 3900), R82 and R81.20. R82.20: "Coming soon". No Spark versions in the table. The check in update 25 (18:24 UTC) came just before this note.
- **Juniper added** (JSA112681, 23 Oct, found via a link in the HPE bulletin): Junos OS vulnerable to CVE-2026-109618, will move to PHP 8.5.12, disable J-Web/JSC/fwAuth. SRX without PHP from 25.2R1. EVO, Session Smart Router, Junos Space and Mist not vulnerable. Removed from "no vendor statement".
- **HPE ClearPass rev.2:** hotfix patches for 6.14.1 and 6.11.16 ("Final hotfixes … address the issue completely"); 6.14.1 and 6.11.16 without the hotfix are now listed as affected.
- **Quest KACE:** SMA 15.0 CU5 (15.0.378) and 15.1 CU2 (15.1.177) released (23 Oct 17:03 UTC). SDA 9.3 hotfix ETA 27 Oct. Not affected by CVE-2026-115560.
- **Palo Alto:** WildFire WF-500/WF-500-B corrected to not affected. Panorama is now covered by a note under the PAN-OS rows. Five more products (Prisma SD-WAN etc.) are not affected. The Threat ID list was extended (content 9162–9164). ETAs unchanged; no hotfix released yet.
- **Cisco v1.6:** workarounds flag set. Catalyst Center, WAE and AppDynamics Enterprise Console / Virtual Appliance are not vulnerable. 11 products remain under investigation.
- **Barracuda:** patches for SecureEdge and Firewall Insights. CloudGen Firewall not affected. Several cloud services remediated. Only MXDR is still under investigation.
- **Broadcom ESG:** CloudSOC SpanVA Appliance affected (39429). CASB moved to not vulnerable.
- **Kaseya:** product table published. VSA 10, BMS and vPenTest fully patched; 17 products, incl. VSA 9, under "Compensating Controls".
- **Trend Micro:** Critical Patch ETA 30 Oct for DDI, DDAN and DDEI. Apex One SaaS "Addressed".
- **Zscaler:** enterprise environment ruled out; removed from "under investigation".
- **Red Hat:**
  - RHEL 7 ELS fixed for CVE-2026-109619 (RHSA-2026:88693).
  - RHEL 9.2 E4S (88659), 9.6 EUS php:8.2 (88834) and 9.4 E4S php:8.2 (88835).
  - RHSB now has mitigation steps (on RHEL 7, disabling upload progress is "the only one required") and covers CVE-2026-115560.
  - RHEL 9 php:8.4 still unfixed.
- **Distributions and other platforms:**
  - **CIQ:** all variants patched, incl. LTS 8.6 and CIQ Bridge (PHP 5.4 backport).
  - **Debian forky:** fixed.
  - **CloudLinux:** reversed its advice, now "keep the ELS ALT PHP repository enabled". The KB still shows the disable command; flagged as a contradiction.
  - **AWS:** EMR on EC2 with Ganglia affected (EMR 4.2.0–6.15.0); Amazon Linux packages in all regions; Bref layers for Lambda.
  - **Tenable:** SC-202610.2 (TNS-2026-30/31) replaces SC-202610.1.
- **Smaller updates:**
  - NVD 109618 is now "Analyzed".
  - Ivanti Incapptic not impacted (KB 000109797, now read in full).
  - Rapid7 and Qualys coverage for CVE-2026-115560.
  - F5 WAF signature file now named `ASM-AttackSignatures_20261022_154742`.
- **Unchanged:**
  - QNAP (V1.0), NetApp (v3.0, no patch), Sophos (v4), Citrix (fixes 27 Oct), Akamai, Plesk.
  - Fortinet, SonicWall, A10, Icinga, Siemens CSAF.
  - CVE-2026-115560 still has no CVE record, NVD entry or Red Hat VEX.
  - NCSC-NL: no new commits since 23 Oct 12:50 UTC.
- **Correction (same update, follow-up commit):**
  - Kaseya was listed both under "under investigation" and "affected"; it is now only under "affected, fix in development".
  - Juniper Junos OS moved from "fixes announced" to "fix in development (no date)".
  - "Missed by CVE-ID searches" replaced with the recorded fact: the anonymous portal search still does not return JSA112681 (06:42–06:43 UTC).
  - RHEL 9 php:8.2 versions written out in full.
  - F5 row states the attacker model again (APM data plane unauthenticated, Configuration utility authenticated).
  - CISA alert update of 23 Oct (SIGMA rule; "has not observed successful exploitation") added.
  - Ten sources outside the sweep fetched at 06:42 UTC and named in the status line.
- **Not verified / not re-read:**
  - Adobe returned HTTP 403.
  - The Ivanti Connect Secure and EPMM KBs and the Broadcom detail advisories (39411, 39421, 39429) need a login.
  - Cacti and LibreNMS are outside the sweep and keep their 23 Oct check times.

## Update 25 – 23 Oct 2026, 18:24 UTC

Only Check Point re-checked (on request); no other source was re-read.

- **Check Point:** the promised permanent fix "by October 23, 17:00 GMT" is not announced in sk1000302 as of 18:24 UTC. The SK text is unchanged since 11:09 UTC, and the solution field still says 11 Nov (Jumbo Hotfix). The CPAI-2026-15172 IPS advisory is unchanged.

## Update 24 – 23 Oct 2026, 16:38 UTC

Re-check of all 119 sources (curl diff 16:20–16:22 UTC against the 11:09 copies, browser-only pages 16:25–16:35 UTC, feeds), plus new leads from NCSC-NL commits since 11:00 UTC, verified at the vendor page.

- **Correction (16:42 UTC, same day):** the browser time ranges in the first commit of this update (16:25–16:27, 16:27–16:30, 16:30–16:33) were narrowed to the recorded `date -u` anchors. The Cisco "also new" list included products already in v1.4. Siemens was restored to "under investigation" for its other products. CVE-2026-109619 NVD score corrected to 8.1. Quoted SUSE timestamp: the page gives no time zone.
- **New related CVE-2026-115560** (PHP informational advisory, 23 Oct): session upload progress plus a runtime switch of `session.serialize_handler`. It is not fixed by the 21 Oct releases, and the fix comes with the next regular release. Keep `session.upload_progress.enabled=0` even after patching. No CVE record or NVD entry yet. Added to Key facts, CERT-EU (v1.2), CCCS (Update 1) and Cloudflare (rule #6).
- **Correction, Quest KACE (mitigation):** Quest withdrew the port 52230 advice. It now says to "block all inbound web traffic, including ports 80, 443, and 52230". The old README text ("use port 52230 and keep 443 closed") was replaced, and the timeline was updated (SDA 9.3 hotfix queued for QA, 23 Oct "Pending update").
- **Correction, Palo Alto:** Panorama is now in the PAN-OS rows ("PAN-OS / Panorama") with the same hotfix ETAs of 26–30 Oct. The earlier "Panorama: all versions, ETA TBD" was removed. PAN made this change without a revision-history entry.
- **Cisco v1.5** (23 Oct 16:16 GMT):
  - New vulnerable product: Duo Access Gateway, fixed in 3.2.0.
  - Expressway and URWB: workarounds are in the bugs.
  - CX Cloud, IoT Control Center, Meraki Dashboard and Slido moved to not vulnerable.
  - Eight product scopes are newly under investigation (SD-WAN Analytics/Portal/Validator, SD-AVC, SD-AVC Cloud Connector, Catalyst 1300, SD-WAN Cloud OnRamp, SSM On-Prem).
  - New scope sentence: "not listed within this advisory … not affected".
- **NetApp ONTAP 9 added** (NTAP-20261021-0021 v3.0, published 21–22 Oct and missed until now): affected by CVE-2026-109618 only, no patch, three workarounds.
- **Siemens:**
  - SSA-566512: RUGGEDCOM APE1808 with PAN-OS is affected; customers should contact Siemens support.
  - SSA-566435: a list of software products that are not affected.
- **Nagios** now has a statement ("apply the PHP security updates provided by their Linux distribution vendor") and was removed from "no vendor statement".
- **Trend Micro:** interim steps for Apex Central and Apex One on-prem (KA-0024815).
- **Fortinet:** FortiDDoS-F moved to not impacted; FortiNDR Cloud, FortiMail Workspace Security and FortiEDR added as not impacted.
- **OPNsense:** Business Edition is 26.4.2p4 (the post said p3 before); Community 26.1.11 was added.
- **Red Hat:** RHEL 9.6 EUS (RHSA-2026:88720) and 9.4 E4S (RHSA-2026:88725). RHEL 9 php:8.4 and RHEL 7 (CVE-2026-109619) still have no fix.
- **SUSE:** the openSUSE Leap 16.0 page lists both a fixed package and the status "Affected"; flagged as a contradiction. BCI PHP containers now ship php8 8.3.36.
- **Smaller updates:**
  - CloudLinux: ea-php builds with PHP.net version numbers.
  - VMware KB: list of unaffected products.
  - Azure App Service on Azure Stack Hub.
- **Check Point:** no permanent fix at 16:37 UTC. The SK still says "by October 23, 17:00 GMT", so the deadline had not yet passed.
- **Unchanged:** F5, QNAP, Sophos, Citrix (27 Oct), Broadcom 39404, HPE ClearPass, Akamai, Plesk, Kaseya, KEV/SSVC. **NVD:** CVE-2026-109619 now "Analyzed" with NVD CVSS 3.1 **8.1** (`AC:H`), not 9.8; Key facts corrected.
- **NCSC-NL leads:**
  - Adopted: NetApp.
  - Already covered: HPE ClearPass, CloudLinux, TuxCare, Plesk, RHEL 9, HestiaCP, Nextcloud AIO.
  - Cisco rows are based on v1.4 and are superseded by v1.5.
  - **Not adopted:** SEPM fixed builds `14.3.27716.10000` / `14.4.494.0000`. They come from a GitHub issue, NCSC-NL says they were "not independently verified", and the Broadcom advisory requires a login. Named in Known gaps.
  - **Not adopted (single apps and Docker images, outside enterprise scope, not verified):** FileCloud, FileRun, FrankenPHP static builds, GLPI images, Grav, grommunio, Part-DB, phpLDAPadmin, Roundcube image, Shaarli, Shlink.
- **Not verified / not re-read:**
  - The Adobe page gave no usable text this pass; the earlier result is kept. Kaseya was checked via the status-page API (still "investigating").
  - Ivanti and Broadcom detail KBs require a login.
  - The Ivanti Incapptic KB was seen only as a search snippet.

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
