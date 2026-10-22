# PHP2Shell (CVE-2026-109618 / CVE-2026-109619) – Vendor and Linux Distribution Status

> [!WARNING]
> **AI-generated content.** This document was researched and written by an AI assistant (Claude, Anthropic) and reviewed by AI against the linked primary sources. It may contain errors or be out of date. **Always verify against the vendor sources before acting.** No warranty.

**Status snapshot:** 22 October 2026, approx. 05:30 UTC (update 10). Spot-checked against primary sources on 22 Oct 2026, approx. 06:00 UTC — see [Verification notes](#verification-notes).

## Background

Two critical PHP core flaws (CVSS v4.0 9.2 each) allow unauthenticated remote code execution as the web worker account:

- **CVE-2026-109618** – OOM bailout (`longjmp()`) during request parsing leaves request memory in an invalid state → memory corruption / RCE ([GHSA-w8hw-w9fx-j79w](https://github.com/php/php-src/security/advisories/GHSA-w8hw-w9fx-j79w))
- **CVE-2026-109619** – fatal-error handling retains stale request state across worker reuse → use-after-free / RCE ([GHSA-6wmf-4rv5-p3rp](https://github.com/php/php-src/security/advisories/GHSA-6wmf-4rv5-p3rp))

**Fixed upstream** in PHP 8.5.12, 8.4.27, 8.3.36, 8.2.35 (21 Oct 2026). PHP 8.1 and older are EOL and get no upstream release; fixes for those exist only as distribution/third-party backports (Red Hat, AlmaLinux, Ubuntu ESM, Remi, Plesk, …).

**Affected SAPIs** (per PHP advisory): Apache mod_php (confirmed), PHP-FPM and FrankenPHP (likely), LiteSpeed LSAPI. Red Hat rates its default PHP-FPM setup as lower risk than mod_php. Red Hat/SUSE score CVSS 3.1 8.1 (Important); NVD 9.8.

Exploitation attempts have been reported since 21 Oct (Patchstack, Cloudflare, watchTowr — not independently verified here). Cisco and Palo Alto report no known exploitation against their own products.

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
| **Cisco** | Partly. AppDynamics PHP Agent runs in customer PHP; other products under review | [cisco-sa-php-october26-Jj384Daq](https://sec.cloudapps.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-php-october26-Jj384Daq) v1.1 interim (upd. 22 Oct 01:24 UTC): no product confirmed vulnerable. **Under investigation** incl. ISE, Catalyst Center, Catalyst SD-WAN Manager, Nexus Dashboard Insights, BPA, WAE, Expressway, StarOS, CPS, Ultra Cloud Core, URWB, Hypershield, AppDynamics, Secure Access, Webex et al. **Not vulnerable**: AI Defense (hybrid on-prem); Umbrella appears in both lists (cloud-hosted: not vulnerable). Snort SIDs 67359, 67360 | Monitor; restrict mgmt UIs of listed products |
| **Fortinet** | Partly. FortiADC uses PHP-FPM (vendor CLI docs) | [FG-IR-26-186](https://fortiguard.fortinet.com/psirt/FG-IR-26-186) (21 Oct): **under investigation**: FortiADC, FortiADC Manager, FortiClient EMS, FortiDDoS, FortiDDoS-F, FortiSIEM, FortiMonitor, FortiClient Cloud, FortiSOAR, FortiSOAR PaaS, FortiGuard, FortiEndpoint. **Not impacted**: FortiOS, FortiManager, FortiAnalyzer, FortiWeb, FortiMail, FortiClient (Win/Mac/Linux), FortiSASE, FortiAuthenticator, FortiSwitch, FortiNAC. IPS virtual patch in package 37.316 (per Threat Signal 6551; the PSIRT page itself still says "Virtual Patch: No") | Monitor FG-IR-26-186; restrict FortiADC / FortiSIEM / EMS mgmt |
| **Sophos** | Products: no. Hosted MyUTM licensing portal ran affected PHP | [sophos-sa-20261021-php2shell](https://www.sophos.com/en-us/security-advisories/sophos-sa-20261021-php2shell) v2: "No Sophos products are affected." MyUTM portal (legacy SG UTM licensing) taken offline 21 Oct for update; no evidence of exploitation | No action for products |
| **Check Point** | Not evidenced | No sk / product statement. IPS protection [CPAI-2026-15172](https://advisories.checkpoint.com/defense/advisories/public/2026/cpai-2026-15172.html) "PHP Remote Code Execution" (Critical, R75–R82 gateways); keep CPAI-2021-0286 in Prevent | Update IPS, set protection to Prevent |
| **SonicWall** | Unlikely (SMA100 UI uses CGI binaries) | No advisory | Low |
| **Plesk** (not a security vendor) | Yes. Bundled PHP | Fixed (22 Oct 02:11): Linux and Windows 8.2–8.5 patched; Linux 7.4/8.0/8.1 rebuilds of 21 Oct; Windows 7.4–8.1 no fix; sw-engine fixed in 18.0.80 U11 / 18.0.81 U4 | Patch now |

Whether an embedded PHP build is actually exploitable can only be confirmed by the vendor.

## 2. Linux distributions and repositories (.deb / .rpm)

| Distribution / repo | PHP | Status (fixed versions, advisory) | Fix type |
|---|---|---|---|
| Debian 13 trixie | 8.4 | **Fixed**: php8.4 8.4.27-1~deb13u1 (DSA-6574-1) | New upstream |
| Debian 12 bookworm | 8.2 | **Fixed**: php8.2 8.2.35-1~deb12u1 (DLA-4848-1) | New upstream |
| Debian 11 bullseye | 7.4 | Freexian ELTS (paid) only | – |
| Ubuntu 26.10 / 26.04 LTS | 8.5 | **Fixed**: 8.5.9-0ubuntu2.1 / 8.5.4-0ubuntu1.5 (USN-8948-1) | Backport |
| Ubuntu 24.04 / 22.04 LTS | 8.3 / 8.1 | **Fixed**: 8.3.6-0ubuntu0.24.04.13 / 8.1.2-1ubuntu2.28 (USN-8948-1) | Backport |
| Ubuntu 20.04 / 18.04 / 16.04 / 14.04 (ESM) | 7.4 / 7.2 / 7.0 / 5.5 | **Fixed via Ubuntu Pro** (USN-8948-2): 7.4.3-4ubuntu2.29+esm5, 7.2.24-0ubuntu0.18.04.17+esm14, 7.0.33-0ubuntu0.16.04.16+esm22, 5.5.9+dfsg-1ubuntu4.29+esm18 (16.04/14.04 need the Legacy add-on) | Backport |
| RHEL 8 / 9 / 10 | 7.4–8.4 | **Partly released**: RHEL 9 php:8.2 → php-8.2.35-1 (RHSA-2026:87072); RHEL 9 php:8.3 → php-8.3.36-1 (RHSA-2026:87079); RHEL 8 php:7.4 → php-7.4.33-8 (RHSA-2026:87080). Not found yet: RHEL 8 php:8.2, RHEL 9 default 8.0, RHEL 10. Red Hat: Important, CVSS 3.1 8.1 | Rebase / backport |
| AlmaLinux 8 / 9 / 10 | 7.2–8.4 | **Released** to production 21 Oct 21:15 UTC (ahead of RHEL), incl. retired streams: AL8 php:7.2, 7.3, 7.4 (7.4.33-8), 8.0, 8.2; AL9 default 8.0, php:8.1, 8.2, 8.3; AL10 8.3 and 8.4 (`.alma.1` releases, keep old upstream version numbers, e.g. 8.2.33, 8.3.33, 8.4.24). Mirrors may lag | Backport |
| Rocky Linux / CIQ | as RHEL | CIQ KB (21 Oct): RLC Pro 8/9/10 and LTS 8.6 **pending**; RLC Pro LTS 9.2 and 9.6 **available** (21 Oct). PHP 7.2/7.3 (EL8 streams): no fix branch, unmitigated | Pending |
| Remi repository | 7.4–8.5 | **Fixed** (repoview): EL8, EL9, EL10 modular 8.5.12-1, 8.4.27-1, 8.3.36-1, 8.2.35-1 and backports 8.1.34-6, 8.0.30-21, 7.4.33-31; SCL e.g. php83-php-fpm 8.3.36-1 (EL9). Remi: "Fedora 43+, RHEL 8+". EL7: no (issue #351). EL8 php 7.2/7.3 streams: no rebuild | New upstream + backports |
| Fedora | 8.4 / 8.5 | Fedora 44: **fixed** php-8.5.12-1.fc44 (FEDORA-2026-a9eba4bbc3); check Bodhi for F43/F45 | New upstream |
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

## 3. Links – vendor advisories and sources

### Upstream / CERTs

- PHP [GHSA-w8hw-w9fx-j79w](https://github.com/php/php-src/security/advisories/GHSA-w8hw-w9fx-j79w) (CVE-2026-109618), [GHSA-6wmf-4rv5-p3rp](https://github.com/php/php-src/security/advisories/GHSA-6wmf-4rv5-p3rp) (CVE-2026-109619)
- [CERT-EU 2026-018](https://cert.europa.eu/publications/security-advisories/2026-018/)
- [NCSC-NL php2shell software list](https://github.com/NCSC-NL/php2shell)

### Vendors

- **F5**: [K000163821](https://my.f5.com/manage/s/article/K000163821); [bug ID1270257](https://cdn.f5.com/product/bugtracker/ID1270257.html) (older PHP CVE-2023-0662 in BIG-IP TMOS – evidence that BIG-IP ships PHP)
- **Palo Alto Networks**: [CVE-2026-109618 advisory](https://security.paloaltonetworks.com/CVE-2026-109618); [Unit 42 threat brief](https://unit42.paloaltonetworks.com/cve-2026-109618-cve-2026-109619/)
- **Cisco**: [cisco-sa-php-october26-Jj384Daq](https://sec.cloudapps.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-php-october26-Jj384Daq); [Talos blog (Snort SIDs)](https://blog.talosintelligence.com/two-critical-rces-in-php-core/)
- **Fortinet**: [FG-IR-26-186](https://fortiguard.fortinet.com/psirt/FG-IR-26-186); [FortiGuard Threat Signal 6551](https://fortiguard.fortinet.com/threat-signal-report/6551)
- **Sophos**: [sophos-sa-20261021-php2shell](https://www.sophos.com/en-us/security-advisories/sophos-sa-20261021-php2shell)
- **Check Point**: [CPAI-2026-15172](https://advisories.checkpoint.com/defense/advisories/public/2026/cpai-2026-15172.html); [blog](https://blog.checkpoint.com/security/php2shell-what-we-know-about-the-leaked-critical-php-vulnerabilities-cve-2026-109618-cve-2026-109619/)
- **Citrix (NetScaler)** – no advisory; PHP evidence: [Google GTIG NetScaler analysis](https://cloud.google.com/blog/topics/threat-intelligence/defending-against-active-exploitation-of-citrix-netscaler-adc-and-gateway-appliances)
- **Ivanti** – no advisory; PHP evidence: [Horizon3 CSA analysis](https://www.horizon3.ai/attack-research/cisa-kev-cve-2024-8190-ivanti-csa-command-injection/); [Ivanti Oct 2026 security update](https://www.ivanti.com/blog/october-2026-security-update) (no PHP mention)
- **Juniper** – no advisory; PHP evidence: [J-Web PHP bulletin 2024-10](https://supportportal.juniper.net/s/article/2024-10-Security-Bulletin-Junos-OS-J-Web-Multiple-vulnerabilities-resolved-in-PHP-software)
- **Plesk**: [KB 44397729587351](https://support.plesk.com/hc/en-us/articles/44397729587351-Vulnerability-CVE-2026-109618-and-CVE-2026-109619-Remote-code-execution-in-PHP-shipped-with-Plesk)

### Distributions / repositories

- **Debian**: [tracker CVE-2026-109618](https://security-tracker.debian.org/tracker/CVE-2026-109618), [DSA-6574-1](https://security-tracker.debian.org/tracker/DSA-6574-1), [DLA-4848-1](https://security-tracker.debian.org/tracker/DLA-4848-1)
- **Ubuntu**: [CVE page](https://ubuntu.com/security/CVE-2026-109618), [USN-8948-1](https://ubuntu.com/security/notices/USN-8948-1), [USN-8948-2 (ESM)](https://ubuntu.com/security/notices/USN-8948-2)
- **Red Hat**: [CVE page](https://access.redhat.com/security/cve/cve-2026-109618), [RHSA-2026:87072](https://access.redhat.com/errata/RHSA-2026:87072) (EL9 php:8.2), [RHSA-2026:87079](https://access.redhat.com/errata/RHSA-2026:87079) (EL9 php:8.3), [RHSA-2026:87080](https://access.redhat.com/errata/RHSA-2026:87080) (EL8 php:7.4)
- **AlmaLinux**: [blog with package list](https://almalinux.org/blog/2026-10-21-php2shell-cve-2026-109618-cve-2026-109619/)
- **Rocky / CIQ**: [CIQ KB](https://kb.ciq.com/article/security-advisories/cve-php2shell-mitigation)
- **Remi**: repoview [EL8](https://rpms.remirepo.net/enterprise/8/modular/x86_64/repoview/php-fpm.html), [EL9](https://rpms.remirepo.net/enterprise/9/modular/x86_64/repoview/php-fpm.html), [EL10](https://rpms.remirepo.net/enterprise/10/modular/x86_64/repoview/php-fpm.html); [issue #351 (EL7)](https://github.com/remicollet/remirepo/issues/351)
- **Fedora**: [FEDORA-2026-a9eba4bbc3 (F44)](https://linuxsecurity.com/advisories/fedora/fedora-44-php-2026-a9eba4bbc3), [package index](https://packages.fedoraproject.org/pkgs/php/php/)
- **SUSE**: [CVE page](https://www.suse.com/security/cve/CVE-2026-109618.html)

## Verification notes

Spot-checked on 22 Oct 2026 (approx. 06:00 UTC) against: both PHP GHSAs, Debian tracker, USN-8948-1/-2, Red Hat CVE page + all three RHSAs, AlmaLinux blog, CIQ KB, Remi EL9 repoview + issue #351, Fedora advisory, SUSE CVE page, Palo Alto, Cisco, Fortinet (PSIRT + Threat Signal), Sophos, Check Point, NCSC-NL. These matched, except for the corrections below, which are already applied above.

**Corrected compared with the original PDF:**
- Verification command: the CVE ID was cut off (`CVE-2026-10961`); the Debian example used `php8.3-fpm`, which Debian doesn't ship
- Background: no upstream backports for 7.4/8.0/8.1 are mentioned in the PHP advisories; these fixes come from distributions and third parties
- Rocky/CIQ: not all variants are pending (LTS 9.2/9.6 available); PHP 7.3 also has no fix, not just 7.2
- SUSE: advisory ID per the CVE page is TID-PHP-RCE-202610; the unfixed list lists Leap 16.0/16.1 (not 15.x); the claim that earlier "not affected" statuses had been revised could not be verified, so it was removed
- Cisco: Umbrella appears both under investigation and as not vulnerable (cloud-hosted)
- Fortinet: the virtual patch is only in Threat Signal 6551; the PSIRT page says "No"
- F5: original wording "exploited by authenticated users" changed to "exploitable" (CVSS context; no in-the-wild exploitation claim found)
- The colour legend of the PDF was dropped (status is given in words)

**Not independently verified:** F5 K000163821 (page requires login/JS); Plesk KB (HTTP 403); the exploitation reports (Patchstack, Cloudflare, watchTowr); the "no advisory" status of Citrix, Ivanti, Juniper and SonicWall; CERT-EU, Unit 42, Talos and Check Point blog content.
