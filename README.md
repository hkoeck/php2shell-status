# PHP2Shell (CVE-2026-109618 / CVE-2026-109619) – Enterprise Vendor and Distribution Status

> [!WARNING]
> **AI-generated content.** This document was researched and written by an AI assistant (Claude, Anthropic). Statements were checked against the raw text of the linked primary source (HTML/JSON/PDF, not summaries) **except where marked as not verified**; provenance is logged in [VERIFICATION.md](VERIFICATION.md). It may still contain errors and goes stale quickly. **Always verify against the vendor source before acting.** No warranty.

**Status:** 22 October 2026, 11:15 UTC (update 14). Sources re-checked 10:09–11:13 UTC on 22 Oct 2026 (rows not changed since update 12 were last read 06:13–06:32 UTC).

## Key facts

- **Fixed upstream** in PHP **8.5.12, 8.4.27, 8.3.36, 8.2.35** (21 Oct 2026, embargo lift planned for 14:00 UTC). All earlier versions are affected (sources say back to PHP 5.4). PHP 8.1 and older get no release, but the PHP security team published **minimal source backports for 7.4, 8.0 and 8.1** (CERT-EU); distributions/LTS vendors ship their own backports.
- **Severity:** CVSS v4.0 **9.2** (PHP, both CVEs) · NVD CVSS 3.1 **9.8** · Red Hat / SUSE / Amazon CVSS 3.1 **8.1 (Important)** · Ubuntu priority **Critical**.
- **Most exposed SAPI:** Apache **mod_php** (RCE validated with default limits). For 109618, FPM is "susceptible" by source analysis, but no complete FPM exploit has been demonstrated; **for 109619, session-lifecycle RCE was validated against both mod_php and FPM** (PHP GHSAs). FrankenPHP: likely susceptible; LiteSpeed LSAPI: conditional.
- **Exploitation – treat as exploited:**
  - **Amazon Threat Intelligence** (AWS Security Blog, 21 Oct): first exploitation attempt in MadPot honeypots on **17 Oct 2026**, four days before disclosure; more attempts by multiple actors on 21 Oct 02:00–08:00 UTC; *"PHP2Shell is now being broadly exploited in the wild."* Amazon recommends **investigating from 17 Oct onward**.
  - **Cloudflare** (blog, 21 Oct): "we observed attack traffic targeting our customers" while the bug was leaked; **watchTowr**: "observing active exploitation attempts of both" CVEs.
  - Official sources lag: **not in CISA KEV** (catalog 2026.10.21); CISA SSVC (21 Oct 14:34 UTC) "Exploitation: none"; BSI (21 Oct) and Canada CCCS (21 Oct): no confirmed exploitation *at that time*; Talos: none seen as of 21 Oct 14:00 UTC.
- **Mitigations are partial:** PHP names `memory_limit=-1` (109618) and `session.upload_progress.enabled=0` (one 109619 path) as incomplete config mitigations; watchTowr calls `.ini` mitigations "ineffective". Sophos additionally lists `fatal_error_backtraces=0` on PHP 8.5. **Only patching closes both bugs.** WAF rules (section 2) are defense-in-depth.
- **Look-back window:** Sophos states the PHP project received the first reports on 11 Aug 2026 and recommends reviewing exposed systems from **1 Aug 2026** (multipart POSTs to non-upload endpoints, `PHP_SESSION_UPLOAD_PROGRESS` in requests, memory-exhaustion errors and worker segfaults, admin logins).

## 1. Network and security appliances

| Vendor | Status (as published) | Exposure / action |
|---|---|---|
| **F5** | [K000163821](https://my.f5.com/manage/s/article/K000163821) (pub. 21 Oct, upd. 22 Oct; bug ID 2693429). **BIG-IP APM, SSLO** 21.1.0, 17.5.0–17.5.1, 17.1.0–17.1.3: vulnerable, component *Access profile*, High 8.1 (CVSS 3.1). APM/SSLO are additionally listed with *Configuration utility*, High 7.5 (added in the 22 Oct revision). **BIG-IP all other modules**, same versions: vulnerable, *Configuration utility*, High 7.5 — "this attack is conducted by legitimate, authenticated users". **No fixes yet.** Not vulnerable: BIG-IQ, F5 Insight, F5OS/-A/-C, all NGINX products, BIG-IP Next for Kubernetes, F5 Distributed Cloud, NGINX One Console. Still researching: BIG-IP Next CNF 1.x/2.x, F5 AI Gateway 1.x | Mitigation: `/etc/php.ini.d/K000163821.ini` (`memory_limit = -1`, `post_max_size = 8M`, `upload_max_filesize = 7M`, `session.upload_progress.enabled = 0`), `bigstart restart httpd` (+ `httpd_sam` on APM/SSLO), per blade, not upgrade-persistent. Restrict Configuration utility (port lockdown, K13309) |
| **Palo Alto Networks** | [CVE-2026-109618 advisory](https://security.paloaltonetworks.com/CVE-2026-109618) (21 Oct). **PAN-OS 10.2, 11.1, 11.2, 12.1, 12.2 and Panorama: all versions affected, fix ETA TBD.** PAN rates it **CVSS-B 8.7 High, availability impact only** (VC:N/VI:N/VA:H) in its products. Affects only the management web UI and XML API; dataplane interfaces only with a management profile. GlobalProtect portal/gateway not impacted. Not affected: Bridgecrew, Cloud NGFW, Cortex XDR Agent, XSIAM, XSOAR, Xpanse, GlobalProtect App, Idira, Prisma Cloud, Prisma Access, Prisma Access Agent. "Not aware of any malicious exploitation … against our products" | Restrict management UI to trusted IPs/jump host; enable Threat IDs (section 2) on traffic to management services |
| **Cisco** | [cisco-sa-php-october26-Jj384Daq](https://sec.cloudapps.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-php-october26-Jj384Daq) v1.1 *Interim* (first 21 Oct 19:12 GMT, upd. 22 Oct 01:24 GMT): **no product known to be affected yet.** Under investigation incl. ISE, Hypershield, Catalyst Center, Catalyst SD-WAN Manager, Nexus Dashboard Insights, BPA, WAE, StarOS, CPS, Ultra Cloud Core, Expressway, URWB, Unified Industrial Wireless, AppDynamics (on-prem Secure Application, PHP Agent, SaaS), CX Cloud, Defense Orchestrator, IoT Control Center, Multicloud Defense, Panoptica, Secure Access, Secure Email Threat Defense, Vulnerability Management, Secure Connect, Slido, Webex. Not vulnerable: AI Defense (hybrid on-prem); Umbrella is listed both under investigation and not vulnerable | Monitor advisory; restrict mgmt UIs of listed products |
| **Citrix (NetScaler)** | No bulletin yet. Support-portal notice (seen 22 Oct 06:21 UTC): *"Citrix is working to update PHP used by NetScaler management interfaces to address CVE-2026-109618 and CVE-2026-109619."* | Per Citrix: restrict NSIP GUI, management-enabled SNIP GUI and Cluster IP GUI to trusted networks |
| **Fortinet** | [FG-IR-26-186](https://fortiguard.fortinet.com/psirt/FG-IR-26-186) (21 Oct). Under investigation: FortiADC, FortiADC Manager, FortiDDoS, FortiDDoS-F, FortiSIEM, FortiMonitor, FortiClient Cloud, FortiSOAR, FortiSOAR PaaS, FortiGuard, FortiEndpoint. Not impacted (as of 10:10 UTC; **FortiClient EMS moved here**): FortiOS, FortiClient EMS, FortiPAM, FortiProxy, FortiDeceptor, FortiSandbox (+ Cloud), FortiMail (+ Cloud), FortiNAC, FortiNAC-F, FortiAP, FortiGate Cloud, FortiManager, FortiAnalyzer, FortiWeb, FortiClient (Linux/Windows/macOS/iOS/Android), FortiSASE, FortiAuthenticator, FortiSwitch | Restrict mgmt of products under investigation |
| **Check Point** | No product statement. IPS protection [CPAI-2026-15172](https://advisories.checkpoint.com/defense/advisories/public/2026/cpai-2026-15172.html) "PHP Remote Code Execution" (Critical; Security Gateway R75–R82) | Update IPS, set Prevent |
| **Trend Micro** | [KA-0024789](https://success.trendmicro.com/en-US/solution/KA-0024789) (upd. 22 Oct): "urgent assessment of existing TrendAI products and services"; no product confirmed affected or unaffected yet | Monitor |
| **Ivanti** | No public advisory found. A login-gated KB article ("Assessment-and-…", 22 Oct) is referenced on the Ivanti community hub; content not verifiable. Customers are asking about CSA 5.0.7, Connect Secure, EPMM/Sentry | Check KB with support login; isolate internet-facing CSA |
| **Juniper** | No security bulletin found (support-portal search, 22 Oct 06:22 UTC). J-Web (EX/SRX) runs PHP (Juniper bulletin 2024-10) | Restrict or disable J-Web |
| **Sophos** | [sophos-sa-20261021-php2shell](https://www.sophos.com/en-us/security-advisories/sophos-sa-20261021-php2shell) (version 3, upd. 22 Oct): "No Sophos products are affected". The hosted MyUTM licensing portal (legacy SG UTM) ran an affected PHP version and was taken offline on 21 Oct; no evidence of exploitation found so far | – |
| **Barracuda** | [Advisory](https://trust.barracuda.com/security/php-vulnerabilities): **not affected**: Email Security Gateway, Cloud-to-Cloud Backup, Cloud Archiving Service, Web Security Gateway / Agent, Advanced Threat Protection, Data Inspector, Incident Response & Impersonation Protection, RMM, BarracudaONE. **Under investigation**: CloudGen Firewall, CloudGen WAN, SecureEdge, Cloud Control, Email Gateway Defense, WAF / Load Balancer ADC / WAF Control Center, WAF-as-a-Service / Active DDoS Protection, Vulnerability Manager, XDR, Security Awareness Training, MSP / Maestro, Backup Service | Restrict mgmt of products under investigation |
| **Progress** | KB articles (community.progress.com): "LoadMaster is not affected"; MOVEit Transfer / Automation and Automate MFT: "No action or remediation is required"; WS_FTP Server / Professional: supported versions not affected ("previous supported versions were exposed") | Update unsupported WS_FTP versions |
| **WatchGuard** | [WGSA-2026-0032](https://psirt.watchguard.com/WGSA-2026-0032/) (21 Oct): "initial assessment is that none of our products are affected" | – |
| **Netgate pfSense** | [Blog](https://www.netgate.com/blog/critical-php-security-update) (21 Oct): **fixed** — Plus 26.07 / 26.03.1 and CE 2.9.0 → PHP 8.5.12; CE 2.8.1 → PHP 8.3.36; update via CLI only. Concern only if GUI or Captive Portal is reachable by attackers | Update now if Captive Portal is used |
| **OPNsense** | [Announcement](https://forum.opnsense.org/index.php?topic=53191.0) (21 Oct): **fixed** in Business Edition 26.4.2p3 (PHP 8.3.36) and Community 26.7.7 (PHP 8.5.12); restart Captive Portal afterwards | Update |
| **Zscaler** | [ThreatLabz blog](https://www.zscaler.com/blogs/security-research/cve-2026-109618-and-cve-2026-109619-php-vulnerable-unauthenticated-rce): "Zscaler is assessing the potential impact on its products in the Trust post" | Monitor trust.zscaler.com |
| **Siemens (OT)** | No ProductCERT advisory yet (CSAF feed last updated 19 Oct). Note: RUGGEDCOM APE1808 runs PAN-OS (see Siemens SSA-104023), so follow the Palo Alto status | Monitor ProductCERT |
| **Checked, nothing found** | Broadcom/VMware (VMSA list, 11:10 UTC; latest VMSA-2026-0007 of 3 Sep), A10 (advisory list, 11:11 UTC; latest entry Mar 2025), SonicWall PSIRT list (06:31 UTC; latest entry 14 Oct), HPE (only an unrelated advance notice HPESBNW05159, AOS-8/10, released 15 Oct). Absence of a statement does not mean not affected | Ask vendor |

## 2. WAF, IPS and detection content

| Vendor | Content | Notes |
|---|---|---|
| Cloudflare | Cloudflare Managed Ruleset + Free Managed Ruleset ("Generic Rules – Anomalous Execution 1–7"), [blog](https://blog.cloudflare.com/php-vulnerabilities-waf-protection/) | Deployed from 21 Oct 03:02 UTC, all plans incl. Free; uses request + response signals |
| Microsoft Azure WAF | Custom rules (Front Door, App Gateway, App Gateway for Containers); Front Door managed rule **99006001** (group MS-ThreatIntel-Response-CVEs, DRS 2.0–2.2, *disabled by default*, rollout until 28 Oct), [blog](https://techcommunity.microsoft.com/blog/azurenetworksecurityblog/addressing-php2shell-cve-2026-109618-and-cve-2026-109619-upgrade-guidance-and-az/4566623) | Rule must be enabled manually |
| AWS WAF | CRS `SizeRestrictions_BODY` (109618, >8 KB bodies) + custom rule (109619), [bulletin 2026-143](https://aws.amazon.com/security/security-bulletins/2026-143-aws/) | Compensating control |
| Google Cloud Armor | Automatically updated threat-intelligence managed rules (canary/stable); active managed rules protect without action, [blog](https://cloud.google.com/blog/products/identity-security/responding-to-core-php-vulnerabilities-cve-2026-109618-cve-2026-109619) | – |
| Imperva | [Blog](https://www.imperva.com/blog/php2shell-vulnerability-updates/): Cloud WAF protected out of the box; Elastic WAF after software update; WAF Gateway after software + ADC content update | No matching traffic seen during pre-disclosure monitoring |
| F5 (ASM / Adv. WAF / NGINX App Protect / F5 WAF for XC) | Signatures **200103697, 200204115** (109618), **200204113** (109619) in ASM-AttackSignatures_20261021_191526 or later | Blocking mode |
| Palo Alto | Threat IDs **543004, 97622, 97623, 97624, 97625** (content 9162+); 543004 via Frontier Virtual Patching since 20 Oct 22:21 PT | – |
| Cisco / Snort | SIDs **67359, 67360** (+ **67375** for subscribers per Talos) | Also in Community Ruleset |
| Fortinet | IPS virtual patch package **37.316** ([Threat Signal 6551](https://fortiguard.fortinet.com/threat-signal-report/6551)); note the PSIRT page itself says "Virtual Patch: No" | – |
| Check Point | **CPAI-2026-15172**; keep **CPAI-2021-0286** (webshell upload) in Prevent | – |
| Trend Micro | IPS rule **1012749**, TippingPoint filter **48514**, network detection rule **6021** | – |
| Akamai App & API Protector | Adaptive Security Engine rule **3000991 v1** "PHP Remote Code Execution Attack Detected" ([blog](https://www.akamai.com/blog/security-research/critical-remote-code-execution-vulnerabilities-php-core), 21 Oct) | Also existing command-injection rules |
| CloudLinux Imunify360 | WAF rulesets **8.83–8.85** (21 Oct) | ModSecurity/Coraza/LiteSpeed |
| **Scanners** | Tenable Nessus **369483** + distro local checks; Tenable WAS **115719–115722**. Qualys QIDs **389102**, **39033** (unauth.), **5019895/5019896**, distro QIDs (e.g. 6056502 for RHSA-2026:87080). Rapid7: remote unauthenticated checks (21 Oct); Velociraptor artifact `Generic.Applications.PHPInventory` | For inventory and patch verification |

## 3. Linux distributions and repositories

Fix type: *new upstream* = rebased to 8.2.35 / 8.3.36 / 8.4.27 / 8.5.12; *backport* = old version number, fix patched in (check the changelog, not `php -v`).

| Distribution / repo | PHP | Status (fixed package, advisory) | Fix type |
|---|---|---|---|
| **RHEL 10** | 8.3, 8.4 | **Fixed**: php `8.3.36-1.el10_2` ([RHSA-2026:87070](https://access.redhat.com/errata/RHSA-2026:87070)), php8.4 `8.4.27-1.el10_2` ([RHSA-2026:87071](https://access.redhat.com/errata/RHSA-2026:87071)) | New upstream |
| **RHEL 9** | 8.0 (default), 8.1–8.4 (modules) | **Fixed**: default php `8.0.30-8.el9_8.1` ([RHSA-2026:87151](https://access.redhat.com/errata/RHSA-2026:87151)), php:8.2 `8.2.35-1` ([RHSA-2026:87072](https://access.redhat.com/errata/RHSA-2026:87072)), php:8.3 `8.3.36-1` ([RHSA-2026:87079](https://access.redhat.com/errata/RHSA-2026:87079)). **php:8.4: affected, no fix yet.** php:8.1: not listed | Backport / new upstream |
| **RHEL 8** | 7.2–8.2 (modules) | **Fixed**: php:7.4 `7.4.33-8` ([RHSA-2026:87080](https://access.redhat.com/errata/RHSA-2026:87080)), php:8.2 `8.2.35-1` ([RHSA-2026:87073](https://access.redhat.com/errata/RHSA-2026:87073)). php:8.0: not listed | Backport / new upstream |
| RHEL 6 / 7 (ELS) | 5.x | Under investigation | – |
| Red Hat other | – | Hardened Images php `8.5.12` ([RHSA-2026:87414](https://access.redhat.com/errata/RHSA-2026:87414)); OpenShift Dev Spaces `udi-rhel9`: affected, no fix. Rating Important / 8.1; standard RHEL uses PHP-FPM (lower risk than mod_php). [RHSB-2026-013](https://access.redhat.com/security/vulnerabilities/RHSB-2026-013), [CSAF VEX](https://security.access.redhat.com/data/csaf/v2/vex/2026/cve-2026-109618.json) | – |
| **Rocky Linux 8 / 9 / 10** (community) | as RHEL | **Fixed** (published 22 Oct, approx. 00:05 UTC): RL10 RLSA-2026:87070, :87071; RL9 RLSA-2026:87151, :87072, :87079; RL8 RLSA-2026:87080 (php:7.4). RL8 php:8.2 not yet | as RHEL |
| Rocky / CIQ RLC Pro | as RHEL | [CIQ KB](https://kb.ciq.com/article/security-advisories/cve-php2shell-mitigation): LTS 9.6 `php-8.0.30-3.4.el9_6_ciq` and LTS 9.2 `php-8.0.30-1.2.el9_2_ciq` available; RLC Pro 8 / 9 / 10, LTS 8.6, CIQ Bridge **pending** | Backport |
| **AlmaLinux 8** | 7.2–8.2 (modules) | **Fixed** (production 21 Oct 21:15 UTC, incl. retired streams): php:7.2 `7.2.24-1…alma.1`, php:7.3 `7.3.20-1…alma.1`, php:7.4 `7.4.33-8`, php:8.0 `8.0.30-1…alma.1`, php:8.2 `8.2.33-1…alma.1` ([blog](https://almalinux.org/blog/2026-10-21-php2shell-cve-2026-109618-cve-2026-109619/)) | Backport |
| **AlmaLinux 9** | 8.0–8.3 | **Fixed**: default `8.0.30-8.el9_8.alma.1`, php:8.1 `8.1.32-1…alma.1`, php:8.2 `8.2.33-1…alma.1`, php:8.3 `8.3.33-1…alma.1` | Backport |
| **AlmaLinux 10** | 8.3, 8.4 | **Fixed**: php `8.3.33-1.el10_2.alma.1`, php8.4 `8.4.24-1.el10_2.alma.1` | Backport |
| **Oracle Linux 10** | 8.3, 8.4 | **Fixed**: php ELSA-2026-87070, php8.4 ELSA-2026-87071 ([CVE page](https://linux.oracle.com/cve/CVE-2026-109618.html)) | as RHEL |
| **Oracle Linux 9** | 8.0 | **Fixed**: php ELSA-2026-87151; module streams not listed yet | as RHEL |
| **Oracle Linux 8** | 7.4 | **Fixed**: php ELSA-2026-87080 (number mirrors RHSA-2026:87080 = php:7.4); php:8.2 not listed yet | as RHEL |
| **SLES / SLES for SAP 15 SP7** | 8.3 (php8), 7.4 (php7) | **Fixed** php8 `8.3.36-150700.3.24.1`, patch `SUSE-SLE-Module-Web-Scripting-15-SP7-2026-4844`. **php7 (Legacy module, Package Hub): affected, no fix** ([CVE page](https://www.suse.com/security/cve/CVE-2026-109618.html)) | New upstream |
| **SLES / SAP 16.0, 16.1** | 8.4 | **In progress** (16.0: `8.4.27-160000.1.1` in QA) | New upstream |
| SUSE other | 7.x / 8.x | **Affected, no fix**: 15 SP4–SP6 incl. LTSS, 16.2, Leap 16.0 / 16.1, many EOL products | – |
| **Ubuntu 26.10 / 26.04 LTS** | 8.5 | **Fixed**: `8.5.9-0ubuntu2.1` / `8.5.4-0ubuntu1.5` ([USN-8948-1](https://ubuntu.com/security/notices/USN-8948-1)) | Backport |
| **Ubuntu 24.04 LTS** | 8.3 | **Fixed**: `8.3.6-0ubuntu0.24.04.13` (USN-8948-1) | Backport |
| **Ubuntu 22.04 LTS** | 8.1 | **Fixed**: `8.1.2-1ubuntu2.28` (USN-8948-1) | Backport |
| Ubuntu 20.04 / 18.04 (Pro) | 7.4 / 7.2 | **Fixed via Ubuntu Pro**: `7.4.3-4ubuntu2.29+esm5` / `7.2.24-0ubuntu0.18.04.17+esm14` ([USN-8948-2](https://ubuntu.com/security/notices/USN-8948-2)) | Backport |
| Ubuntu 16.04 / 14.04 (Pro + Legacy) | 7.0 / 5.5 | **Fixed via Ubuntu Pro Legacy**: `7.0.33-0ubuntu0.16.04.16+esm22` / `5.5.9+dfsg-1ubuntu4.29+esm18` | Backport |
| **Debian 13 trixie** | 8.4 | **Fixed**: `8.4.27-1~deb13u1` (DSA-6574-1) ([tracker](https://security-tracker.debian.org/tracker/CVE-2026-109618)) | New upstream |
| **Debian 12 bookworm** | 8.2 | **Fixed**: `8.2.35-1~deb12u1` (DLA-4848-1) | New upstream |
| Debian 11 bullseye (Freexian ELTS, paid) | 7.4 | **Fixed**: `7.4.33-1+deb11u14` (ELA-1853-1) ([tracker](https://deb.freexian.com/extended-lts/tracker/CVE-2026-109618)) | Backport |
| Debian 10 buster / 9 stretch (ELTS) | 7.3 / 7.0 | **Fixed**: `7.3.31-1~deb10u16` (ELA-1854-1) / `7.0.33-0+deb9u26` (ELA-1855-1) | Backport |
| Debian forky (testing) / sid | 8.4 | forky `8.4.26-1` **vulnerable**; sid **fixed** `8.4.27-1` | New upstream |
| **Amazon Linux 2023** | 8.1–8.5 | **Fixed** (22 Oct): php8.2/8.3/8.4/8.5 ALAS2023-2026-3301 … -3304. **php8.1: no fix planned** ([ALAS](https://explore.alas.aws.amazon.com/CVE-2026-109618.html)) | New upstream |
| Amazon Linux 2 | core, 8.x extras | **Fixed**: PHP 8.2 extra ALAS2PHP8.2-2026-015. **Core php: no fix planned**. AL2027 preview php8.5 fixed | New upstream |
| Fedora 44 | 8.5 | **Fixed**: `php-8.5.12-1.fc44` ([FEDORA-2026-a9eba4bbc3](https://bodhi.fedoraproject.org/updates/FEDORA-2026-a9eba4bbc3), stable 21 Oct 16:43 UTC) | New upstream |
| **Remi repository** (EL8 / 9 / 10) | 7.4–8.5 | **Fixed** (repoview): `8.5.12-1`, `8.4.27-1`, `8.3.36-1`, `8.2.35-1`; backports `8.1.34-6`, `8.0.30-21`, `7.4.33-31`. No EL7 builds ([issue #351](https://github.com/remicollet/remirepo/issues/351)) | New upstream + backports |
| **packages.sury.org / ondrej PPA** (Debian 12/13, Ubuntu 24.04) | 7.4–8.5 | **Fixed** (builds of 21 Oct): `8.5.12`, `8.4.27`, `8.3.36`, `8.2.35`, plus `8.1.34-9`, `8.0.30-25`, `7.4.33-31`. Changelogs of 7.4 and 8.1 say "Backported from 8.2.35 – CVE-2026-109618, CVE-2026-109619" (8.0 not checked) | New upstream + backports |
| CloudLinux / TuxCare | 5.2–8.5 | **Fixed** ([CloudLinux KB](https://cloudlinux.zendesk.com/hc/en-us/articles/31194180517916-PHP-CVE-2026-109618-CVE-2026-109619-PHP2Shell-fixed-alt-php-and-ea-php-packages-and-how-to-verify), upd. 22 Oct): all fixed alt-php and ea-php builds are in the regular stable repos (alt-php reached the CloudLinux repos approx. 01:00 UTC on 22 Oct). CL 7/8/9 e.g. alt-php74 `7.4.33-81`, alt-php82 `8.2.34-7`, alt-php83 `8.3.35-6`, alt-php84 `8.4.26-5`, alt-php85 `8.5.11-5`; ea-php e.g. `ea-php82-php-cli-8.2.34-2.el8.cloudlinux.1`. alt-php44/51: no fix. The CloudLinux *blog* post lags behind the KB | Backport |
| EPEL | – | Not applicable (EPEL ships no PHP) | – |

## 4. Cloud platforms and container images

| Platform | Status |
|---|---|
| **AWS** ([bulletin 2026-143](https://aws.amazon.com/security/security-bulletins/2026-143-aws/), upd. 21 Oct 20:30 PDT) | Elastic Beanstalk PHP platform v4.13.12 (21 Oct); follow-on with upstream fix targeted 22 Oct (auto with Managed Platform Updates). Lightsail: new blueprints, running instances can't be updated in place → new instances. WorkMail: config controls, PHP 8.3.36 on 22 Oct, no action. Amazon Linux: see section 3 |
| **Google Cloud** ([blog](https://cloud.google.com/blog/products/identity-security/responding-to-core-php-vulnerabilities-cve-2026-109618-cve-2026-109619), upd. 21 Oct 16:25 PDT) | App Engine Standard (PHP 8.2+): updated automatically. App Engine Flexible: redeploy. Cloud Run: rebuild/redeploy unless automatic base-image updates are on. GKE: rebuild images, redeploy pods |
| **Microsoft Azure** | Azure WAF guidance (section 2). **No Microsoft statement found on App Service PHP runtime patching**; customers are asking on Microsoft Q&A |
| **Docker Official Image `php`** | Rebuilt 21 Oct (Docker Hub, 18:58–22:07 UTC) with 8.5.12 / 8.4.27 / 8.3.36 / 8.2.35. Derived images (WordPress, Nextcloud, own images) must be rebuilt |
| Red Hat images | Hardened Images fixed (RHSA-2026:87414); OpenShift Dev Spaces `udi-rhel9` affected |

## 5. Monitoring and IT automation

These tools run on PHP but do not fix PHP themselves (exceptions are images and appliances they ship). Patch the PHP that serves them, then restart PHP-FPM / Apache. Their web UIs are typically reachable by many internal users and often hold credentials for the whole estate, so restrict access until patched.

| Product | PHP role (evidence) | Vendor statement / status | Action |
|---|---|---|---|
| **Checkmk** | PHP only for NagVis; packages use the distribution's PHP | [Werk #19262](https://checkmk.com/werk/19262) (21 Oct): affected versions 2.5.0, 2.4.0, 2.3.0, **Docker image only**; rebuilt with patched Ubuntu PHP in **2.5.0p17** and **2.4.0p38**. "For all other installations, Checkmk uses the PHP packages of your Linux distribution." **Checkmk Appliance firmware 1.7.25** (21 Oct) contains the fixes. No 2.3.0 release with the fix found | Update OS PHP; Docker: new image and recreate container; appliance: firmware 1.7.25 |
| **Zabbix** | Web frontend is PHP (14 % of the repo); official Docker images bundle PHP | No advisory found ([security advisories](https://www.zabbix.com/security_advisories)); the [forum thread](https://www.zabbix.com/forum/zabbix-help/517840-critical-php-cve-released-and-patched-today-when-will-zabbix-docker-catch-up) contains only community posts. Docker: maintainer in [zabbix-docker #1982](https://github.com/zabbix/zabbix-docker/issues/1982) (22 Oct 00:47 UTC): "all latest images will be rebuilt today"; the `*-latest` tags of `zabbix/zabbix-web-nginx-pgsql` were updated on Docker Hub on 22 Oct 07:14–07:38 UTC. Users report that version-pinned tags (e.g. `alpine-7.0.32`) still contain PHP 8.5.11 | Update OS PHP; Docker: pull `*-latest` and verify `php -v` in the container, pinned tags may be unpatched |
| **Centreon** | Web UI is PHP (72 %) | [Security notice](https://thewatch.centreon.com/latest-security-bulletins-64/security-notice-centreon-assessment-of-critical-php-vulnerabilities-6007) (21 Oct, before the release): assessment in progress. "Centreon does not provide or maintain the PHP packages installed on user platforms", so take PHP updates from the OS or community repo | Update OS/Remi/sury PHP; restrict web UI |
| **GLPI** (ITSM) | PHP (84 %) | [GLPI blog](https://www.glpi-project.org/en/%F0%9F%9A%A8-critical-php2shell-php-vulnerabilities-cve-2026-109618-cve-2026-109619-what-you-need-to-know-for-your-glpi-server/): GLPI code is not the problem, but "any web server hosting a GLPI instance remains vulnerable until the server's underlying PHP engine is patched". GLPI Network Cloud patched as of 21 Oct 14:00 UTC | Update host/container PHP |
| **Nagios XI / Nagios Core** | XI: PHP web UI; Core: CGIs in C plus PHP frame pages (`index.php`, `main.php`, `side.php`) | No statement found ([security disclosures](https://www.nagios.com/security-disclosures/), [XI changelog](https://www.nagios.com/changelog/nagios-xi/), 10:13 UTC) | Update OS PHP |
| **Icinga Web 2** | PHP (84 %) | No statement found ([Icinga blog](https://icinga.com/blog/), community forum, 10:13 UTC) | Update OS PHP |
| **Cacti, LibreNMS** | PHP (62 % / 88 %) | No statement found (GitHub security advisories / releases, LibreNMS forum, 10:13 UTC) | Update OS PHP |
| **Ansible, AWX, Ansible Automation Platform** | **No PHP** (ansible/ansible: Python 86 %, AWX: Python 98 %) | Not affected by design; not listed in Red Hat's CSAF VEX for these CVEs. Relevant only if Ansible *manages* PHP hosts: use it to roll out the PHP updates | Patch PHP fleet-wide (e.g. `ansible.builtin.dnf`/`apt` with `state: latest` for `php*` and a PHP-FPM restart) |
| Rundeck, Semaphore | No PHP (Groovy/Java, Go) | Not affected by design | – |

NCSC-NL also lists Nagios Fusion, Centreon and Zabbix as "vulnerable when deployed on an affected PHP runtime" ([software list](https://github.com/NCSC-NL/php2shell)).

## 6. Other (hosting panels, SMB, non-enterprise distros)

| Product | Status |
|---|---|
| Plesk | [KB](https://support.plesk.com/hc/en-us/articles/44397729587351-Vulnerability-CVE-2026-109618-and-CVE-2026-109619-Remote-code-execution-in-PHP-shipped-with-Plesk) (upd. 22 Oct 05:29 UTC): Linux + Windows 8.2–8.5 fixed; Linux 7.4/8.0/8.1 builds of 21 Oct fixed (same version number); sw-engine fixed in Obsidian 18.0.80 U11 / 18.0.81 U4; 5.6/7.2/7.3 → TuxCare ELS |
| cPanel | EasyApache 4 [25.91](https://docs.cpanel.net/changelogs/easyapache-4-change-log-25/): ea-php82/83/84/85 → 8.2.35/8.3.36/8.4.27/8.5.12; fix backported to ea-php74/80/81 (EA-13611…13613) |
| DirectAdmin | [Forum](https://forum.directadmin.com/threads/critical-php-updates.82726/page-3): new DA build on current/stable bumps 8.2–8.5 and patches 8.1, 8.0, 7.4 (`da build php`) |
| HestiaCP | [Issue #5817](https://github.com/hestiacp/hestiacp/issues/5817): hosted-site PHP comes from sury.org (fixed); "An update for Hestia-php and hestia-nginx has been released for Ubuntu Jammy (22.04) and up, Debian Bookworm (12) and up" (22 Oct) |
| QNAP, Synology | No vendor advisory found; NCSC-NL lists both as under investigation |
| Alpine | [pkgs.alpinelinux.org](https://pkgs.alpinelinux.org/packages?name=php8*-fpm): **3.24** php83 `8.3.36-r0`, php84 `8.4.27-r0`, php85 `8.5.12-r0` (21 Oct); **3.23** php83 `8.3.36-r0` and php85 `8.5.12-r0` (22 Oct), but php84 still `8.4.21-r0`; **3.22** no fixed build (php82 `8.2.33`, php83 `8.3.29`, php84 `8.4.16`) |
| Arch | php `8.5.12-1` (21 Oct) |

## 7. Government / CERT advisories

- **CISA:** not in KEV (catalog 2026.10.21); SSVC (CISA-ADP, 21 Oct 14:34 UTC): Exploitation *none*, Automatable *no*, Technical Impact *total*
- **BSI (DE):** BSI-IT-Sicherheitshinweis BITS-H 2026-297981-1132, v1.1, 21 Oct 2026 (TLP:CLEAR, [PDF](https://www.bsi.bund.de/SharedDocs/Cybersicherheitswarnungen/DE/2026/2026-297981-1032.pdf?__blob=publicationFile&v=3)) — expects broad exploitation within hours of the patches
- **NCSC-UK:** [Critical security issue affecting PHP](https://www.ncsc.gov.uk/news/critical-security-issue-affecting-php) (21 Oct)
- **NCSC-NL:** [php2shell software list](https://github.com/NCSC-NL/php2shell) (last commit 21 Oct 21:40 UTC)
- **CERT-EU:** [Security Advisory 2026-018](https://cert.europa.eu/publications/security-advisories/2026-018/)
- **Canada CCCS:** [AL26-026](https://www.cyber.gc.ca/en/alerts-advisories/al26-026-critical-vulnerabilities-impacting-php-cve-2026-109618-cve-2026-109619) (21 Oct)

## Known gaps (not verified)

Could not be read from the primary source: Ivanti KB (login required), Azure App Service runtime patching (no Microsoft statement found), QNAP/Synology (NCSC-NL only), TuxCare ELS details beyond CloudLinux (NCSC-NL only). Absence of a vendor statement does not mean a product is not affected.

## Checking whether you are patched

With backports, `php -v` keeps showing the old version. Check package versions or changelogs:

```sh
# Debian / Ubuntu (adjust php8.x)
zgrep CVE-2026-109618 /usr/share/doc/php8.4-fpm/changelog.Debian.gz
# RHEL / Alma / Rocky / Oracle / Fedora / SUSE / Amazon Linux
rpm -q --changelog php-fpm | grep CVE-2026-109618
# Remi
dnf list --updates --refresh --repo remi-modular
```

Restart PHP-FPM after updating; for mod_php do a full Apache restart. Rebuild container images; updating the host does not update PHP inside an image.

## Fork it and keep it current with an AI

1. Fork: click **Fork** on GitHub, or `gh repo fork hkoeck/php2shell-status --clone`.
2. Open the fork in an AI coding assistant with shell and web access (e.g. Claude Code) and give it the prompt from [UPDATE_PROMPT.md](UPDATE_PROMPT.md). Fill in the placeholders: the products to add, or "update everything".
3. Review the diff. Every changed claim needs a matching row in [VERIFICATION.md](VERIFICATION.md) with source, UTC time and a verbatim quote. Spot-check a few against the vendor pages yourself.
4. Commit, push, optionally open a pull request back here.

## Sources

PHP: [GHSA-w8hw-w9fx-j79w](https://github.com/php/php-src/security/advisories/GHSA-w8hw-w9fx-j79w) (109618), [GHSA-6wmf-4rv5-p3rp](https://github.com/php/php-src/security/advisories/GHSA-6wmf-4rv5-p3rp) (109619) ·
Exploitation: [Amazon Threat Intelligence](https://aws.amazon.com/blogs/security/amazon-threat-intelligence-identifies-php2shell-exploitation-prior-to-public-disclosure-in-madpot/), [Cloudflare](https://blog.cloudflare.com/php-vulnerabilities-waf-protection/), [watchTowr](https://watchtowr.com/intelligence/php-remote-code-execution-php2shell/), [Talos](https://blog.talosintelligence.com/two-critical-rces-in-php-core/), [Unit 42](https://unit42.paloaltonetworks.com/cve-2026-109618-cve-2026-109619/) (PoC seen; no ITW claim) ·
Scanners: [Tenable](https://www.tenable.com/blog/php2shell-cve-2026-109618-cve-2026-109619-frequently-asked-questions-about-critical-php-remote), [Qualys](https://blog.qualys.com/vulnerabilities-threat-research/2026/10/20/php-announces-critical-security-release-for-two-vulnerabilities), [Rapid7](https://www.rapid7.com/blog/post/etr-cve-2026-109618-and-cve-2026-109619-critical-unauthenticated-remote-code-execution-in-php/) ·
Distros: [Debian](https://security-tracker.debian.org/tracker/CVE-2026-109618), [Freexian ELTS](https://deb.freexian.com/extended-lts/tracker/CVE-2026-109618), [Ubuntu](https://ubuntu.com/security/CVE-2026-109618), [Red Hat CVE](https://access.redhat.com/security/cve/cve-2026-109618) / [CSAF VEX](https://security.access.redhat.com/data/csaf/v2/vex/2026/cve-2026-109618.json), [Rocky errata](https://errata.rockylinux.org/), [Amazon ALAS](https://explore.alas.aws.amazon.com/CVE-2026-109618.html), [Fedora Bodhi](https://bodhi.fedoraproject.org/updates/FEDORA-2026-a9eba4bbc3), [Remi EL9 repoview](https://rpms.remirepo.net/enterprise/9/modular/x86_64/repoview/php-fpm.html) ·
Vendor and platform links are in the tables above.

---

History of changes: [CHANGELOG.md](CHANGELOG.md)
