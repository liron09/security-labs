# Security Labs & OSINT Exercises

Hands-on work from my **OSINT Analyst Program** (InsAIghts Academy by Penlink, with Google and Reichman AI Tech School) and my **cybersecurity training program** and PortSwigger Web Security Academy (Networking, Linux, Python for Security, Web Pentesting, SOC, Incident Response).

## OSINT Exercises

| # | Case study | Skills |
|---|---|---|
| 01 | [Black Friday scam store investigation](osint-exercises/01-black-friday-scam-site.md) | Fraud detection, WHOIS, reverse image search, address verification, review dorking |
| 02 | [IP infrastructure & reputation analysis](osint-exercises/02-ip-reputation-analysis.md) | Reverse IP, CDN identification, blacklist/reputation checks |
| 03 | [Public figure intelligence profile: Rodrigo Duterte](osint-exercises/03-public-figure-profile-duterte.md) | Entity profiling, timeline, network mapping, disinformation awareness |
| 04 | [Image verification: a viral photo out of context](osint-exercises/04-image-verification.md) | Media forensics, metadata, source corroboration |
| 05 | [Image geolocation & metadata extraction](osint-exercises/05-geolocation.md) | GEOINT, EXIF/GPS analysis, anchor decomposition |
| 06 | [Visual anomaly detection & cognitive bias](osint-exercises/06-visual-anomaly-and-cognitive-bias.md) | IMINT, analytic tradecraft, bias awareness |
| 07 | [Social media OPSEC threat model](osint-exercises/07-social-media-opsec-threat-model.md) | Threat modeling, pattern-of-life, mitigation |

➡️ Flagship project: **[Remotely Exploitable Medical Devices, OSINT investigation](https://github.com/liron09/medical-devices-osint)**

## Web Security

| Lab set | Topics | Tools |
|---|---|---|
| [PortSwigger: Access Control & Information Disclosure (7 labs)](web-security/portswigger-access-control-info-disclosure.md) | IDOR, forgeable cookies, 2FA bypass, broken API access control, backup-file and `.git` exposure | Browser DevTools, git-dumper, git |
| [PortSwigger: JWT Authentication Bypass (2 labs)](web-security/portswigger-jwt-authentication-bypass.md) | Unverified signature, `alg: none` acceptance, Base64URL token forging, SOC detection | DevTools Console, jwt.io |

## Infrastructure & SOC Labs

- **Active Directory lab:** Windows Server domain with users and groups, SMB shares with NTFS + share permissions, and RDP enabled via GPO, tested from Windows 10 and Kali (`smbclient`, `xfreerdp`)
- **OpenCTI deployment:** threat intelligence platform deployed with Docker on WSL2
- **Networking lab (Cisco Packet Tracer):** multi-router topologies, static routing, subnetting, SSH configuration, DNS server

*Detailed write-ups for these labs are being added.*

## Tools Used
Browser DevTools · jwt.io · git-dumper · Maltego · Shodan · WHOIS / DNS tools · Google Lens / Yandex · ExifTool-style metadata tools · Wayback Machine · OpenCTI · Kali Linux · Windows Server / AD · Cisco Packet Tracer · Python

---

*Exercises involving private individuals are intentionally not published. All case studies here cover public figures, organizations, infrastructure or training scenarios.*
