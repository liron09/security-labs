# Case Study: Black Friday Scam Store Investigation

**Type:** Fraud / e-commerce OSINT · **Program:** OSINT Analyst Program (Reichman University & Google)

## Question
Is the online store `kelys.shop` a legitimate retailer offering a real Black Friday deal, or a short-lived fraud site exploiting seasonal traffic?

**Item examined:** "iPhone 12 Pro Max Soft OLED replacement screen", listed at **$14.68** (marked down from $36.70).

## Investigation

### 1. Product research (VISINT)
- **Reverse image search (Google Lens):** the product photo was not original. It was copied directly from the Chinese manufacturer's site (JK LCD Display), with no credit or authorized-reseller statement. The store holds no photographed stock of its own.
- **Price anomaly:** Soft OLED panels of this model sell for roughly **$50–$100** even from aftermarket brands. $14.68 matches a cheap LCD (TFT/Incell) panel, which points to a likely **bait-and-switch**.

### 2. Company research
| Check | Finding |
|---|---|
| WHOIS | Domain registered **15 Nov 2025**, under three weeks before the check, timed for the sales season |
| Registrant | Hidden behind a privacy proxy ("Super Privacy Service LTD") |
| Physical address | The contact address on the site resolves (Street View) to a **private residential house** in South Carolina, with no business signage or warehouse. It also contradicts the registration address (a mail drop in California). |
| Hosting | Behind Cloudflare CDN; the shared IP hosts **~979 other sites**, typical of cheap shared hosting |
| Look-alike domains | `kelys.cz` / `kelys.eu` exist but are registered with different registrars (Wedos, OVH), so they are unrelated to this store |

### 3. Review analysis
Targeted dorks across review platforms and forums:
```
site:trustpilot.com kelys.shop
site:sitejabber.com kelys.shop
site:reddit.com kelys.shop
"kelys.shop" review OR scam OR fraud
inurl:forum kelys.shop
```
**Result:** zero reviews or mentions anywhere, and no social media presence. That is a strong red flag during peak Black Friday traffic.

## Conclusion
**Risk level: very high.** A brand-new anonymous domain, a residential address, a stolen product image and an economically impossible price all point to a one-off fraud or exploitative drop-shipping operation.

**Recommendation:** do not purchase. If a customer insists, they should use a payment method with buyer protection (e.g. PayPal), demand written proof of product authenticity and document the entire order.

## Tools
Google Lens · WHOIS · Google Maps / Street View · reverse-IP lookup · Google advanced operators · price benchmarking
