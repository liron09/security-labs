# Case Study: Public Figure Intelligence Profile, Rodrigo Duterte

**Type:** Person-of-interest profiling (public figure) · **Program:** OSINT Analyst Program (Reichman University & Google)

## Summary
Rodrigo Roa Duterte: 16th President of the Philippines (2016–2022) and long-time mayor of Davao City. His presidency was defined by the "war on drugs". Government/police figures report about **6,200–6,250** deaths in police operations, while human-rights organizations estimate **12,000–30,000**, including killings attributed to unknown assailants. On **11–12 March 2025** he was arrested on an ICC warrant and transferred to The Hague. In May 2025 he was elected mayor of Davao while in detention.

## 1. Identity baseline
- **Full name:** Rodrigo Roa Duterte · **Born:** 28 March 1945, Maasin, Southern Leyte
- **Key roles:** Mayor of Davao (multiple terms from 1988) · President of the Philippines (2016–2022)

## 2. Timeline
| Date | Event |
|---|---|
| 1945 | Born in Maasin, Southern Leyte |
| 1988–2016 | Multiple terms as Mayor of Davao |
| 30 Jun 2016 | Sworn in as President |
| 2016–2022 | "War on drugs" |
| Mar 2019 | Philippines' withdrawal from the ICC takes effect |
| 11–12 Mar 2025 | Arrested in Manila, transferred to ICC custody |
| May 2025 | Elected Mayor of Davao while detained |

## 3. Digital assets
For each asset I recorded: handle/ID, creation date, verification status, Page Transparency (admins), linked domain/email, posting frequency, plus a screenshot and archive link.
- Facebook "Rody Duterte", X `@RRD_Davao` (watch for impersonators)
- Official archives: RTVM / PCO / Official Gazette, `*.gov.ph`, `icc-cpi.int`

## 4. Network map
| Category | Entities |
|---|---|
| Family / local power base | Sara Duterte (VP, 2022), Paolo Duterte (House, Davao 1st district), Sebastian "Baste" Duterte (Mayor, Davao) |
| Political allies | Sen. Bong Go (former aide), Sen. Ronald "Bato" dela Rosa (former PNP chief) |
| Party / institutions | PDP–Laban · PNP · PDEA · DDB · DOJ · CHR |
| Legal / international | ICC (OTP, Pre-Trial Chamber) · victims' groups / CSOs · shifting relations with the Marcos Jr. administration |

## 5. Information-environment risk
Facebook removed networks of **coordinated inauthentic behavior** in the Philippines (2018–2020), including pro-Duterte pages, and third-party analysis (Cyabra, 2025) found a high share of inauthentic profiles around the ICC arrest. **Rule applied:** a social-media claim enters the report only if it comes from a verified or institutional source or is backed by two independent sources.

**Impersonation and inauthenticity indicators:** slight name misspellings (`RRD_Davao` vs `RRD-Davao`), accounts created right after major events, sudden follower spikes, identical text/images reposted minutes apart, missing political disclaimers.

## 6. Analyst reflection
- **Starting point:** fixed the time window and the central entity, built a biographical baseline and an anchor-event timeline from primary sources (ICC, government, major wire services), then mapped entities.
- **Working assumption:** a gap between state and NGO casualty figures was expected, so figures are presented as **attributed ranges**.
- **Source discipline:** propaganda pages, anonymous accounts and unsourced graphics were excluded.
- **Difficulties:** conflicting casualty numbers, a fast-moving ICC case (tracked by update date and archiving) and many impersonator accounts.
- **With more time:** a tagged event database, a PNP chain-of-command map, FOI requests, SALN (asset declaration) review and geolocation of key scenes.

## Tools & techniques
Google operators (`site:`, `filetype:pdf`, `intitle:`, `before:/after:`) · ICC & GOV.PH primary sources · Reuters/AP/Guardian/Time · TinEye, Google Lens, InVID, ExifTool · Wayback Machine / archive.today · diagrams.net, TimelineJS · Google Alerts · OPSEC: sock-puppet profile, VPN, isolated browser
