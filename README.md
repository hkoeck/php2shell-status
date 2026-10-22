# PHP2Shell (CVE-2026-109618 / CVE-2026-109619) – Vendor and Linux Distribution Status

> [!WARNING]
> **AI-generated content.** This document was researched and written by an AI assistant (Claude, Anthropic) and reviewed by AI against the linked primary sources. It may contain errors or be out of date. **Always verify against the vendor sources before acting.** No warranty.

**Status snapshot:** 22 October 2026, approx. 06:30 UTC (update 11). Checked against primary sources on 22 Oct 2026 between 05:50 and 06:30 UTC — see [Verification notes](#verification-notes).

## Background

Two critical PHP core flaws (CVSS v4.0 9.2 each) allow unauthenticated remote code execution as the web worker account:

- **CVE-2026-109618** – OOM bailout (`longjmp()`) during request parsing leaves request memory in an invalid state → memory corruption / RCE ([GHSA-w8hw-w9fx-j79w](https://github.com/php/php-src/security/advisories/GHSA-w8hw-w9fx-j79w))
- **CVE-2026-109619** – fatal-error handling retains stale request state across worker reuse → use-after-free / RCE ([GHSA-6wmf-4rv5-p3rp](https://github.com/php/php-src/security/advisories/GHSA-6wmf-4rv5-p3rp))

**Fixed upstream** in PHP 8.5.12, 8.4.27, 8.3.36, 8.2.35 (21 Oct 2026). PHP 8.1 and older are EOL and get no upstream release; fixes for those exist only as distribution/third-party backports (Red Hat, AlmaLinux, Ubuntu ESM, Remi, Plesk, …).

**Affected SAPIs** (per PHP advisory): Apache mod_php (confirmed), PHP-FPM and FrankenPHP (likely), LiteSpeed LSAPI. Red Hat rates its default PHP-FPM setup as lower risk than mod_php. Red Hat/SUSE score CVSS 3.1 8.1 (Important); NVD 9.8.

**Exploitation:** watchTowr reports active exploitation attempts of both CVEs (21 Oct, 14:19 UTC). Cloudflare reportedly saw attacks from 07:43 UTC on 21 Oct, i.e. before the 14:00 UTC release (secondary source: Sansec), and Patchstack reportedly saw attempts against hosting partners (secondary sources only). Unit 42 describes the flaws as exploited in the wild. CERT-EU: PoCs are circulating. Talos had seen no in-the-wild exploitation as of 21 Oct 14:00 UTC. Cisco and Palo Alto report no known exploitation against their own products.

### Changes in update 11

- **RHEL corrected:** RHEL 10 (php 8.3, php8.4) and RHEL 9 default php 8.0 are fixed (RHSA-2026:87070, :87071, :87151). Oracle Linux 9/10 followed (ELSA)
- **Vendors added:** Netgate pfSense (fixed), OPNsense (fixed), Trend Micro (investigating; IPS/TippingPoint/DDI rules), QNAP, Synology, other firewall/NAS vendors without a statement
- **New section 2** for hosting panels, container images and cloud platforms: cPanel, DirectAdmin, HestiaCP, ISPConfig, CloudLinux/TuxCare, Docker Official Images, AWS, Google Cloud, Azure
- **Distros added:** Amazon Linux, Oracle Linux, Alpine, Arch, sury.org / ondrej PPA, Debian forky/sid
- F5 and Plesk now verified (F5 via browser, Plesk via the Zendesk API); Cisco Talos adds Snort SID 67375; the exploitation status is now backed by sources

### Changes since update 7

- New vendor advisories: Cisco (interim, products under investigation), Fortinet (FG-IR-26-186)
- Sophos v2: products not affected
- Palo Alto: per-branch table, GlobalProtect not affected
- F5 (K000163821, upd. 22 Oct): BIG-IP 17.1 / 17.5 / 21.1 vulnerable, no fixes; BIG-IQ / F5OS / NGINX not vulnerable
- Check Point: IPS protection CPAI-2026-15172
- Distros: Debian bookworm fixed (DLA-4848-1); RHEL 9 php:8.3 and RHEL 8 php:7.4 RHSAs; AlmaLinux all streams released; Ubuntu ESM fixed back to 14.04; Remi EL8/9/10 incl. 7.4–8.1 backports, no EL7; SUSE 15 SP7 fixed; Fedora 44 fixed

## 1. Security vendors – PHP usage and own-product status

| Vendor | Uses PHP? Where? (evidence) | Vendor statement / status | Risk / action |
|---|---|---|---|
| **F5** | Yes. BIG-IP ships PHP (Apache httpd for the Configuration utility, `httpd_sam` for APM/SSLO). APM webtop renderer `/var/sam/www/webtop/renderer/*.php3` | [K000163821](https://my.f5.com/manage/s/article/K000163821) (pub. 21 Oct, upd. 22 Oct; BIG-IP bug ID 2693429). **BIG-IP APM, SSLO**: 21.1.0, 17.5.0–17.5.1, 17.1.0–17.1.3 vulnerable, component "Access profile", High 8.1 (CVSS 3.1). **BIG-IP all other modules**: same versions, component Configuration utility, High 7.5 (per F5: exploitable by authenticated users). No fixes yet. **Not vulnerable**: BIG-IQ, F5 Insight, F5OS / F5OS-A / F5OS-C, all NGINX products, BIG-IP Next for Kubernetes, F5 Distributed Cloud, NGINX One Console. **Still researching**: BIG-IP Next CNF 1.x/2.x, F5 AI Gateway 1.x | **High.** Mitigation per F5: `/etc/php.ini.d/K000163821.ini` (`memory_limit=-1`, `post_max_size=8M`, `upload_max_filesize=7M`, `session.upload_progress.enabled=0`), then `bigstart restart httpd` and `httpd_sam` (APM/SSLO); per blade; not upgrade-persistent. Restrict TMUI (port lockdown, K13309). Protect backends with ASM signatures 200103697, 200204115, 200204113 (sig file 20261021_191526) |
| **Palo Alto Networks** | Yes. PAN-OS management web UI (nginx → Apache/PHP) | [Advisory](https://security.paloaltonetworks.com/CVE-2026-109618): PAN-OS 10.2, 11.1, 11.2, 12.1, 12.2 and Panorama: all versions affected, fix ETA TBD. **Not affected**: GlobalProtect App and portal/gateway, Prisma Access, Prisma Access Agent, Prisma Cloud, Cloud NGFW, Cortex XDR Agent, XSIAM, XSOAR, Xpanse, Bridgecrew, Idira. Threat IDs 543004, 97622–97625 (content 9162+). No known exploitation against PAN products | **High:** restrict mgmt UI / Panorama to trusted IPs or jump host |
| **Citrix (NetScaler)** | Yes. PHP listed in NetScaler ADC 14.1 third-party notices; admin GUI uses PHP; VPN portal PHP paths (GTIG) | No Citrix bulletin found. NCSC-NL: under investigation | **High:** Gateway is internet-facing; monitor Citrix bulletins |
| **Ivanti** | Yes. Cloud Services Appliance has a PHP front end (Horizon3, CVE-2024-8190) | No Ivanti statement found (Oct 2026 security update page does not mention PHP) | **High:** CSA is internet-facing; isolate |
| **Juniper** | Yes. Junos J-Web (EX/SRX) runs PHP; Juniper fixed PHP CVEs in J-Web (bulletin 2024-10) | No Juniper bulletin found. NCSC-NL: under investigation | **Medium:** disable or restrict J-Web |
| **Cisco** | Partly. AppDynamics PHP Agent runs in customer PHP; other products under review | [cisco-sa-php-october26-Jj384Daq](https://sec.cloudapps.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-php-october26-Jj384Daq) v1.1 interim (upd. 22 Oct 01:24 UTC): no product confirmed vulnerable. **Under investigation** incl. ISE, Catalyst Center, Catalyst SD-WAN Manager, Nexus Dashboard Insights, BPA, WAE, Expressway, StarOS, CPS, Ultra Cloud Core, URWB, Hypershield, AppDynamics, Secure Access, Webex et al. **Not vulnerable**: AI Defense (hybrid on-prem); Umbrella appears in both lists (cloud-hosted: not vulnerable). Snort SIDs 67359, 67360 (Talos also lists 67375) | Monitor; restrict mgmt UIs of listed products |
| **Fortinet** | Partly. FortiADC uses PHP-FPM (vendor CLI docs) | [FG-IR-26-186](https://fortiguard.fortinet.com/psirt/FG-IR-26-186) (21 Oct): **under investigation**: FortiADC, FortiADC Manager, FortiClient EMS, FortiDDoS, FortiDDoS-F, FortiSIEM, FortiMonitor, FortiClient Cloud, FortiSOAR, FortiSOAR PaaS, FortiGuard, FortiEndpoint. **Not impacted**: FortiOS, FortiManager, FortiAnalyzer, FortiWeb, FortiMail, FortiClient (Win/Mac/Linux), FortiSASE, FortiAuthenticator, FortiSwitch, FortiNAC. IPS virtual patch in package 37.316 (per Threat Signal 6551; the PSIRT page itself still says "Virtual Patch: No") | Monitor FG-IR-26-186; restrict FortiADC / FortiSIEM / EMS mgmt |
| **Sophos** | Products: no. Hosted MyUTM licensing portal ran affected PHP | [sophos-sa-20261021-php2shell](https://www.sophos.com/en-us/security-advisories/sophos-sa-20261021-php2shell) v2: "No Sophos products are affected." MyUTM portal (legacy SG UTM licensing) taken offline 21 Oct for update; no evidence of exploitation | No action for products |
| **Check Point** | Not evidenced | No sk / product statement. IPS protection [CPAI-2026-15172](https://advisories.checkpoint.com/defense/advisories/public/2026/cpai-2026-15172.html) "PHP Remote Code Execution" (Critical, R75–R82 gateways); keep CPAI-2021-0286 in Prevent | Update IPS, set protection to Prevent |
| **Trend Micro** | Yes (per NCSC-NL: Apex One, Apex Central have a PHP component) | [KA-0024789](https://success.trendmicro.com/en-US/solution/KA-0024789) (upd. 22 Oct): own products under urgent assessment, none confirmed affected or unaffected yet. Protections: IPS rule 1012749, TippingPoint filter 48514, network detection rule 6021 | Monitor KA-0024789; restrict Apex One / Apex Central consoles |
| **Netgate pfSense** | Yes. webConfigurator GUI and Captive Portal are PHP | [Blog](https://www.netgate.com/blog/critical-php-security-update) (21 Oct): **fixed** PHP 8.5.12 for pfSense Plus 26.07 / 26.03.1 and CE 2.9.0; PHP 8.3.36 for CE 2.8.1. Update via CLI only (not via the GUI). Risk only if the GUI or Captive Portal is reachable by attackers; GUI is LAN-only by default | **High for Captive Portal users** — update now; keep GUI off WAN |
| **OPNsense** | Yes. WebGUI/API are PHP | [Forum announcement](https://forum.opnsense.org/index.php?topic=53191.0) (21 Oct): **fixed** in Community 26.7.7 (PHP 8.5.12) and Business 26.4.2p3 (PHP 8.3.36). Restart Captive Portal after the update | Update now |
| **QNAP** | Yes. QTS / QuTS hero ship a built-in PHP runtime | No QNAP advisory found. NCSC-NL: under investigation | Medium: keep the NAS UI off the internet; watch QNAP advisories |
| **Synology** | Yes. Web Station PHP packages (5.6–8.4) | No Synology advisory found. NCSC-NL: all PHP packages under investigation | Medium: Web Station sites are exposed; workaround `session.upload_progress.enabled=0` (community advice) |
| **SonicWall** | Unlikely (SMA100 UI uses CGI binaries) | No advisory | Low |
| **Zyxel, WatchGuard, DrayTek, Ubiquiti, Barracuda** | Unclear | No statement found; not on the NCSC-NL list (as of 22 Oct) | Monitor |

Whether an embedded PHP build is actually exploitable can only be confirmed by the vendor.

## 2. Hosting panels, container images and cloud platforms

| Product | Status | Action |
|---|---|---|
| **Plesk** | [KB 44397729587351](https://support.plesk.com/hc/en-us/articles/44397729587351-Vulnerability-CVE-2026-109618-and-CVE-2026-109619-Remote-code-execution-in-PHP-shipped-with-Plesk) (upd. 22 Oct 05:29 UTC): **fixed** Linux and Windows 8.2–8.5; Linux 7.4/8.0/8.1 builds of 21 Oct include fixes; Windows 7.4–8.1: no fix listed; sw-engine (Plesk UI) fixed in Obsidian 18.0.80 U11 / 18.0.81 U4 | Patch now |
| **cPanel** | [EasyApache 4 25.91](https://docs.cpanel.net/changelogs/easyapache-4-change-log-25/) (21 Oct): **fixed** ea-php82/83/84 updated to 8.2.35 / 8.3.36 / 8.4.27, fix backported to ea-php74/80/81. Internal cpanel-php84 → 8.4.27 in cPanel & WHM 136.0.50 (per NCSC-NL) | Update EA4 and cPanel |
| **DirectAdmin** | [Forum](https://forum.directadmin.com/threads/critical-php-updates.82726/page-3): CustomBuild **fixed** 8.2–8.5 (new versions) and 7.4/8.0/8.1 (patched builds); 7.3 and older **not yet patched** | `da update && da build php` |
| **HestiaCP** | Hosted-site PHP packages **fixed**; the panel's own `hestia-php` was **still vulnerable** when checked, fix in preparation (per NCSC-NL, [issue #5817](https://github.com/hestiacp/hestiacp/issues/5817)) | Update; restrict panel access |
| **ISPConfig** | Control panel affected via unpatched PHP (per NCSC-NL) | Update OS PHP |
| **CloudLinux / TuxCare** | [CloudLinux blog](https://blog.cloudlinux.com/php-cve-2026-109618-and-cve-2026-109619): **fixed** ea-php52–85 (CloudLinux builds), alt-php in stable for CL 7/8/9/10 and Ubuntu 22.04, native PHP 8.2/8.3 (CL 9) and 8.2 (CL 8); other native PHP rolling out. TuxCare ELS: partly fixed (e.g. CentOS 8.4/8.5, Ubuntu 16.04/18.04 per NCSC-NL). Imunify360 WAF rulesets 8.83–8.85 block known exploit requests (not a fix) | Update; check ruleset ≥ 8.85 |
| **Docker Official Image `php`** | **Fixed**: tags 8.5 / 8.4 / 8.3 / 8.2 rebuilt on 21 Oct with 8.5.12 / 8.4.27 / 8.3.36 / 8.2.35 (Docker Hub). Images based on it (WordPress, Nextcloud, …) must be rebuilt/pulled again | Pull and rebuild; restart containers |
| **AWS** | [Bulletin 2026-143](https://aws.amazon.com/security/security-bulletins/2026-143-aws/): Amazon Linux fixed (see section 3); Elastic Beanstalk platform 4.13.12 (21 Oct), upstream PHP fix targeted for 22 Oct; Lightsail: new blueprints, needs new instances; WorkMail: mitigated, upgrade on 22 Oct | Follow the bulletin |
| **Google Cloud** | [Blog](https://cloud.google.com/blog/products/identity-security/responding-to-core-php-vulnerabilities-cve-2026-109618-cve-2026-109619): App Engine Standard (PHP 8.2+) and Cloud Run with automatic base-image updates are **auto-patched**; App Engine Flexible, Cloud Run custom images and GKE require a rebuild/redeploy. Cloud Armor rules available | Rebuild and redeploy |
| **Azure App Service (PHP on Linux)** | No Microsoft statement found; NCSC-NL: under investigation | Monitor |

## 3. Linux distributions and repositories (.deb / .rpm / .apk)

| Distribution / repo | PHP | Status (fixed versions, advisory) | Fix type |
|---|---|---|---|
| Debian 13 trixie | 8.4 | **Fixed**: php8.4 8.4.27-1~deb13u1 (DSA-6574-1) | New upstream |
| Debian 12 bookworm | 8.2 | **Fixed**: php8.2 8.2.35-1~deb12u1 (DLA-4848-1) | New upstream |
| Debian 11 bullseye | 7.4 | Freexian ELTS (paid) only | – |
| Debian forky (testing) / sid | 8.4 | sid **fixed** 8.4.27-1; forky still vulnerable (until migration) | New upstream |
| packages.sury.org / ondrej PPA | 7.4–8.5 | **Rebuilt 21 Oct** for Debian 12/13 and Ubuntu 24.04: 8.5.12, 8.4.27, 8.3.36, 8.2.35 plus new 8.1.34-9, 8.0.30-25, 7.4.33-31 builds (version check of the repo indexes; that the EOL builds contain the backport was not verified — check the changelog). Some PPA mirrors lag | New upstream + backports |
| Ubuntu 26.10 / 26.04 LTS | 8.5 | **Fixed**: 8.5.9-0ubuntu2.1 / 8.5.4-0ubuntu1.5 (USN-8948-1) | Backport |
| Ubuntu 24.04 / 22.04 LTS | 8.3 / 8.1 | **Fixed**: 8.3.6-0ubuntu0.24.04.13 / 8.1.2-1ubuntu2.28 (USN-8948-1) | Backport |
| Ubuntu 20.04 / 18.04 / 16.04 / 14.04 (ESM) | 7.4 / 7.2 / 7.0 / 5.5 | **Fixed via Ubuntu Pro** (USN-8948-2): 7.4.3-4ubuntu2.29+esm5, 7.2.24-0ubuntu0.18.04.17+esm14, 7.0.33-0ubuntu0.16.04.16+esm22, 5.5.9+dfsg-1ubuntu4.29+esm18 (16.04/14.04 need the Legacy add-on) | Backport |
| RHEL 8 / 9 / 10 | 7.4–8.4 | **Largely released** (all 21 Oct): RHEL 10 php → 8.3.36-1.el10_2 (RHSA-2026:87070), RHEL 10 php8.4 → 8.4.27-1.el10_2 (RHSA-2026:87071); RHEL 9 default php → 8.0.30-8.el9_8.1 (RHSA-2026:87151), php:8.2 → 8.2.35-1 (RHSA-2026:87072), php:8.3 → 8.3.36-1 (RHSA-2026:87079); RHEL 8 php:7.4 → 7.4.33-8 (RHSA-2026:87080). Not found yet: RHEL 8 php:8.0 / php:8.2, RHEL 9 php:8.1. Red Hat: Important, CVSS 3.1 8.1; bulletin [RHSB-2026-013](https://access.redhat.com/security/vulnerabilities/RHSB-2026-013) (also OpenShift Dev Spaces 3) | Rebase / backport |
| Oracle Linux 9 / 10 | as RHEL | **Fixed**: OL10 php (ELSA-2026-87070), OL10 php8.4 (ELSA-2026-87071), OL9 php (ELSA-2026-87151), all 21 Oct; OL8 / module streams not listed yet | Rebase / backport |
| AlmaLinux 8 / 9 / 10 | 7.2–8.4 | **Released** to production 21 Oct 21:15 UTC (ahead of RHEL), incl. retired streams: AL8 php:7.2, 7.3, 7.4 (7.4.33-8), 8.0, 8.2; AL9 default 8.0, php:8.1, 8.2, 8.3; AL10 8.3 and 8.4 (`.alma.1` releases, keep old upstream version numbers, e.g. 8.2.33, 8.3.33, 8.4.24). Mirrors may lag | Backport |
| Rocky Linux / CIQ | as RHEL | CIQ KB (21 Oct): RLC Pro 8/9/10 and LTS 8.6 **pending**; RLC Pro LTS 9.2 and 9.6 **available** (21 Oct). PHP 7.2/7.3 (EL8 streams): no fix branch, unmitigated | Pending |
| Remi repository | 7.4–8.5 | **Fixed** (repoview): EL8, EL9, EL10 modular 8.5.12-1, 8.4.27-1, 8.3.36-1, 8.2.35-1 and backports 8.1.34-6, 8.0.30-21, 7.4.33-31; SCL e.g. php83-php-fpm 8.3.36-1 (EL9). Remi: "Fedora 43+, RHEL 8+". EL7: no (issue #351). EL8 php 7.2/7.3 streams: no rebuild | New upstream + backports |
| Fedora | 8.4 / 8.5 | Fedora 44: **fixed** php-8.5.12-1.fc44 (FEDORA-2026-a9eba4bbc3); check Bodhi for F43/F45 | New upstream |
| Amazon Linux | 8.x | [ALAS](https://explore.alas.aws.amazon.com/CVE-2026-109618.html): **fixed** AL2023 php8.2/8.3/8.4/8.5 (ALAS2023-2026-3301 … -3304), AL2 extras php8.2 (ALAS2PHP8.2-2026-015), AL2027 preview; **no fix planned**: AL2 core php, AL2023 php8.1 | New upstream |
| Alpine Linux | 8.3–8.5 | Per secondary sources: Alpine 3.24 fixed for php83/84/85, older branches will not get a fix; tracked in [aports #18512](https://gitlab.alpinelinux.org/alpine/aports/-/work_items/18512) (not reachable for verification) | New upstream |
| Arch Linux | 8.5 | **Fixed**: php 8.5.12-1 (21 Oct) | New upstream |
| EPEL | – | Not applicable: EPEL ships no PHP interpreter; PHP comes from RHEL AppStream / Remi | – |
| SUSE SLES 15 SP7 / SAP 15 SP7 | 8.3 | **Fixed**: php8 8.3.36-150700.3.24.1 (Module for Web and Scripting 15 SP7; SUSE TID-PHP-RCE-202610) | New upstream |
| SUSE SLES 16.0 / 16.1 / SAP 16.x | 8.4 | In progress; 8.4.27-160000.1.1 in QA | New upstream |
| SUSE other (SLES 15 SP4–SP6 LTSS, 16.2, Leap 16.0/16.1, BCI php images, php7 on EOL products) | 7.x / 8.x | SUSE CVE page (21 Oct 20:57): affected, no fix yet | – |

### Checking whether you are patched

With backports, `php -v` keeps showing the old version. Check the package version / changelog instead:

```sh
# Debian / Ubuntu (adjust php8.x to your version)
zgrep CVE-2026-109618 /usr/share/doc/php8.4-fpm/changelog.Debian.gz
# RHEL / AlmaLinux / Rocky / Fedora / SUSE
rpm -q --changelog php-fpm | grep CVE-2026-109618
# Remi
dnf list --updates --refresh --repo remi-modular
```

After updating, restart PHP-FPM; for mod_php do a full Apache restart.

## 4. Links – vendor advisories and sources

### Upstream / CERTs / exploitation

- PHP [GHSA-w8hw-w9fx-j79w](https://github.com/php/php-src/security/advisories/GHSA-w8hw-w9fx-j79w) (CVE-2026-109618), [GHSA-6wmf-4rv5-p3rp](https://github.com/php/php-src/security/advisories/GHSA-6wmf-4rv5-p3rp) (CVE-2026-109619)
- [CERT-EU 2026-018](https://cert.europa.eu/publications/security-advisories/2026-018/)
- [NCSC-NL php2shell software list](https://github.com/NCSC-NL/php2shell)
- [watchTowr: exploitation observed](https://watchtowr.com/intelligence/php-remote-code-execution-php2shell/); [Sansec research (Cloudflare timeline)](https://sansec.io/research/php2shell)

### Security / network vendors

- **F5**: [K000163821](https://my.f5.com/manage/s/article/K000163821); [bug ID1270257](https://cdn.f5.com/product/bugtracker/ID1270257.html) (older PHP CVE-2023-0662 in BIG-IP TMOS – evidence that BIG-IP ships PHP)
- **Palo Alto Networks**: [CVE-2026-109618 advisory](https://security.paloaltonetworks.com/CVE-2026-109618); [Unit 42 threat brief](https://unit42.paloaltonetworks.com/cve-2026-109618-cve-2026-109619/)
- **Cisco**: [cisco-sa-php-october26-Jj384Daq](https://sec.cloudapps.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-php-october26-Jj384Daq); [Talos blog (Snort SIDs)](https://blog.talosintelligence.com/two-critical-rces-in-php-core/)
- **Fortinet**: [FG-IR-26-186](https://fortiguard.fortinet.com/psirt/FG-IR-26-186); [FortiGuard Threat Signal 6551](https://fortiguard.fortinet.com/threat-signal-report/6551)
- **Sophos**: [sophos-sa-20261021-php2shell](https://www.sophos.com/en-us/security-advisories/sophos-sa-20261021-php2shell)
- **Check Point**: [CPAI-2026-15172](https://advisories.checkpoint.com/defense/advisories/public/2026/cpai-2026-15172.html); [blog](https://blog.checkpoint.com/security/php2shell-what-we-know-about-the-leaked-critical-php-vulnerabilities-cve-2026-109618-cve-2026-109619/)
- **Trend Micro**: [KA-0024789](https://success.trendmicro.com/en-US/solution/KA-0024789)
- **Netgate pfSense**: [Critical PHP security update](https://www.netgate.com/blog/critical-php-security-update)
- **OPNsense**: [26.7.7 / 26.4.2p3 announcement](https://forum.opnsense.org/index.php?topic=53191.0)
- **Citrix (NetScaler)** – no advisory; PHP evidence: [Google GTIG NetScaler analysis](https://cloud.google.com/blog/topics/threat-intelligence/defending-against-active-exploitation-of-citrix-netscaler-adc-and-gateway-appliances)
- **Ivanti** – no advisory; PHP evidence: [Horizon3 CSA analysis](https://www.horizon3.ai/attack-research/cisa-kev-cve-2024-8190-ivanti-csa-command-injection/); [Ivanti Oct 2026 security update](https://www.ivanti.com/blog/october-2026-security-update) (no PHP mention)
- **Juniper** – no advisory; PHP evidence: [J-Web PHP bulletin 2024-10](https://supportportal.juniper.net/s/article/2024-10-Security-Bulletin-Junos-OS-J-Web-Multiple-vulnerabilities-resolved-in-PHP-software)

### Hosting panels / images / cloud

- **Plesk**: [KB 44397729587351](https://support.plesk.com/hc/en-us/articles/44397729587351-Vulnerability-CVE-2026-109618-and-CVE-2026-109619-Remote-code-execution-in-PHP-shipped-with-Plesk)
- **cPanel**: [EasyApache 4 change log](https://docs.cpanel.net/changelogs/easyapache-4-change-log-25/), [cPanel & WHM 136 change log](https://docs.cpanel.net/changelogs/136-change-log/)
- **DirectAdmin**: [forum thread "Critical PHP updates"](https://forum.directadmin.com/threads/critical-php-updates.82726/page-3)
- **HestiaCP**: [issue #5817](https://github.com/hestiacp/hestiacp/issues/5817)
- **CloudLinux / TuxCare**: [blog](https://blog.cloudlinux.com/php-cve-2026-109618-and-cve-2026-109619), [KB](https://cloudlinux.zendesk.com/hc/en-us/articles/31194180517916-PHP-CVE-2026-109618-CVE-2026-109619-reported-pre-disclosure-RCEs-updated-package-availability)
- **Docker**: [Official Image php](https://hub.docker.com/_/php)
- **AWS**: [Security bulletin 2026-143](https://aws.amazon.com/security/security-bulletins/2026-143-aws/)
- **Google Cloud**: [Responding to core PHP vulnerabilities](https://cloud.google.com/blog/products/identity-security/responding-to-core-php-vulnerabilities-cve-2026-109618-cve-2026-109619)

### Distributions / repositories

- **Debian**: [tracker CVE-2026-109618](https://security-tracker.debian.org/tracker/CVE-2026-109618), [DSA-6574-1](https://security-tracker.debian.org/tracker/DSA-6574-1), [DLA-4848-1](https://security-tracker.debian.org/tracker/DLA-4848-1)
- **Ubuntu**: [CVE page](https://ubuntu.com/security/CVE-2026-109618), [USN-8948-1](https://ubuntu.com/security/notices/USN-8948-1), [USN-8948-2 (ESM)](https://ubuntu.com/security/notices/USN-8948-2)
- **sury.org**: [packages.sury.org/php](https://packages.sury.org/php/), [ondrej/php PPA](https://launchpad.net/~ondrej/+archive/ubuntu/php)
- **Red Hat**: [CVE page](https://access.redhat.com/security/cve/cve-2026-109618), [RHSB-2026-013](https://access.redhat.com/security/vulnerabilities/RHSB-2026-013), [RHSA-2026:87070](https://access.redhat.com/errata/RHSA-2026:87070) (EL10 php), [RHSA-2026:87071](https://access.redhat.com/errata/RHSA-2026:87071) (EL10 php8.4), [RHSA-2026:87151](https://access.redhat.com/errata/RHSA-2026:87151) (EL9 php 8.0), [RHSA-2026:87072](https://access.redhat.com/errata/RHSA-2026:87072) (EL9 php:8.2), [RHSA-2026:87079](https://access.redhat.com/errata/RHSA-2026:87079) (EL9 php:8.3), [RHSA-2026:87080](https://access.redhat.com/errata/RHSA-2026:87080) (EL8 php:7.4)
- **Oracle Linux**: [CVE page](https://linux.oracle.com/cve/CVE-2026-109618.html)
- **AlmaLinux**: [blog with package list](https://almalinux.org/blog/2026-10-21-php2shell-cve-2026-109618-cve-2026-109619/)
- **Rocky / CIQ**: [CIQ KB](https://kb.ciq.com/article/security-advisories/cve-php2shell-mitigation)
- **Remi**: repoview [EL8](https://rpms.remirepo.net/enterprise/8/modular/x86_64/repoview/php-fpm.html), [EL9](https://rpms.remirepo.net/enterprise/9/modular/x86_64/repoview/php-fpm.html), [EL10](https://rpms.remirepo.net/enterprise/10/modular/x86_64/repoview/php-fpm.html); [issue #351 (EL7)](https://github.com/remicollet/remirepo/issues/351)
- **Fedora**: [FEDORA-2026-a9eba4bbc3 (F44)](https://linuxsecurity.com/advisories/fedora/fedora-44-php-2026-a9eba4bbc3), [package index](https://packages.fedoraproject.org/pkgs/php/php/)
- **Amazon Linux**: [ALAS CVE page](https://explore.alas.aws.amazon.com/CVE-2026-109618.html)
- **Alpine**: [aports #18512](https://gitlab.alpinelinux.org/alpine/aports/-/work_items/18512)
- **Arch**: [php package](https://archlinux.org/packages/extra/x86_64/php/)
- **SUSE**: [CVE page](https://www.suse.com/security/cve/CVE-2026-109618.html)

## Verification notes

Checked on 22 Oct 2026 (approx. 05:50–06:30 UTC) against the primary sources: both PHP GHSAs, Debian tracker, USN-8948-1/-2, Red Hat CVE page, RHSB-2026-013 and all six RHSAs, Oracle Linux CVE page, AlmaLinux blog, CIQ KB, Remi EL9 repoview + issue #351, Fedora advisory, SUSE CVE page, Amazon ALAS + AWS bulletin, Arch package API, sury.org/PPA package indexes, Docker Hub, F5 (browser), Plesk (Zendesk API), Palo Alto, Cisco, Talos, Fortinet (PSIRT + Threat Signal), Sophos, Check Point (advisory + blog), Trend Micro, Netgate, OPNsense, cPanel, DirectAdmin, CloudLinux blog, Google Cloud, watchTowr, CERT-EU, NCSC-NL (list as of 21 Oct 21:40 UTC).

**Corrected compared with the original PDF (update 10):**
- RHEL: RHEL 10 and the RHEL 9 default stream were listed as "not found yet", but fixes were already out (RHSA-2026:87070, :87071, :87151)
- Verification command: the CVE ID was cut off (`CVE-2026-10961`); the Debian example used `php8.3-fpm`, which Debian doesn't ship
- Background: no upstream backports for 7.4/8.0/8.1 are mentioned in the PHP advisories; these fixes come from distributions and third parties
- Rocky/CIQ: not all variants are pending (LTS 9.2/9.6 available); PHP 7.3 also has no fix, not just 7.2
- SUSE: advisory ID per the CVE page is TID-PHP-RCE-202610; the unfixed list lists Leap 16.0/16.1 (not 15.x); the claim that earlier "not affected" statuses had been revised could not be verified, so it was removed
- Cisco: Umbrella appears both under investigation and as not vulnerable (cloud-hosted); Talos lists an additional Snort SID 67375
- Fortinet: the virtual patch is only in Threat Signal 6551; the PSIRT page says "No"
- F5: "exploited by authenticated users" → "exploitable by authenticated users" (F5: "this attack is conducted by legitimate, authenticated users"; no in-the-wild claim)
- Plesk: KB has been updated since (05:29 UTC); Windows EOL versions have no fix listed
- The colour legend of the PDF was dropped (status is given in words)

**Not independently verified:** Cloudflare and Patchstack exploitation reports (secondary sources only); Alpine (aports not reachable); HestiaCP, ISPConfig and the TuxCare details (taken from NCSC-NL); whether the sury.org EOL builds contain the backport; the "no advisory" status of Citrix, Ivanti, Juniper, SonicWall, QNAP, Synology, Azure, Zyxel, WatchGuard, DrayTek, Ubiquiti and Barracuda (absence of a statement can't be proven).
