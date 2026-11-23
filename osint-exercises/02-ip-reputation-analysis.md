# Case Study: IP Infrastructure & Reputation Analysis

**Type:** Network / infrastructure OSINT · **Program:** OSINT Analyst Program (Reichman University & Google)

## Task
Resolve `mail.spamcop.net`, identify other domains sharing its IP, and assess whether the IP is safe to interact with.

**Resolved IP:** `23.205.4.122`

## 1. Reverse-IP: who else lives on this address?
I cross-checked three reverse-IP tools, because each relies on a different dataset:

| Tool | Result |
|---|---|
| WhoisXML API (reverse IP) | `e8912.dscg.akamaiedge.net` and a related `akamaiedge.net` edge hostname |
| HackerTarget | `a23-205-4-122.deploy.static.akamaitechnologies.com` |
| DNSlytics | No results |

**Interpretation:** every hostname found belongs to **Akamai** infrastructure, so the service sits behind a CDN edge node rather than a dedicated server. DNSlytics' empty result is a reminder that reverse-IP coverage depends on each tool's database, so one tool is never enough.

## 2. Reputation & blacklist checks
| Platform | Result |
|---|---|
| MXToolbox | Not listed |
| Spamhaus | Not listed |
| Barracuda | Good reputation |
| Blacklist Checker | Clean on all DNSBLs |

## Conclusion
The IP is **not associated with spam, malware or attack activity**, and its related domains are legitimate Akamai CDN infrastructure. Risk of interacting with it is **low**.

## Lessons
- Always corroborate across several tools, since coverage gaps are normal.
- A CDN IP is shared by many tenants, so a clean or dirty IP reputation says more about the edge network than about a single site.

## Tools
WhoisXML API · HackerTarget · DNSlytics · MXToolbox · Spamhaus · Barracuda Reputation · Blacklist Checker
