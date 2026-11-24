# PortSwigger Web Security Academy: JWT Authentication Bypass

**2 Apprentice-level labs** · November 2026

**Topic:** authentication bypass through flaws in how the server verifies JSON Web Tokens (JWT).

## JWT Structure in Brief

A JWT has three parts separated by dots:

```
Header . Payload . Signature
```

| Part | Encoding | Contents |
|---|---|---|
| **Header** | Base64URL | `alg` (signing algorithm), `kid` (key ID) |
| **Payload** | Base64URL | Claims, including `sub`, which identifies the user |
| **Signature** | — | Proves the token was not tampered with; computed with a secret key |

**Core idea:** the header and payload are only **encoded**, not encrypted, so anyone can read and change them. Only the **signature** protects the token. If the server does not verify it properly, the token can be forged.

> **Base64URL** is a URL-safe Base64 variant: `+` → `-`, `/` → `_`, trailing `=` dropped. Decode in the browser console with `atob()`, encode with `btoa()`.

## Labs Overview

| # | Lab | Flaw | Exploit |
|---|-----|------|---------|
| 1 | JWT authentication bypass via unverified signature | Server never verifies the signature | Changed `sub` to `administrator`, kept the old signature |
| 2 | JWT authentication bypass via flawed signature verification | Server accepts unsigned tokens (`alg: none`) | Set `alg` to `none`, `sub` to `administrator`, empty signature |

Goal in both labs: escalate to administrator, reach `/admin` and delete the user `carlos`.

## Lab 1: Unverified Signature

**Flaw:** the server checks that the token is well-formed but **never checks that the signature is valid**. The content can be changed while a stale signature is left in place, and the server still accepts it.

**Steps:**
1. Retrieved the `session` cookie in DevTools (Storage → Cookies).
2. Split the token in the Console: `token.split(".")` gives `[0]` header, `[1]` payload and `[2]` signature.
3. Decoded the payload: `atob(part[1])` → `{"iss":"portswigger","exp":...,"sub":"wiener"}`
4. Built a new payload with `"sub":"administrator"` and encoded it with `btoa(...)`.
5. Reassembled `header + "." + newPayload + "." + oldSignature`.
6. Replaced the cookie, refreshed, accessed `/admin` and deleted `carlos`.

**Key point:** the signature no longer matched the modified payload, yet the attack worked because the server never checked it.

## Lab 2: Flawed Signature Verification (`alg: none`)

**Flaw:** the server accepts tokens with `"alg": "none"`, meaning **unsigned tokens**. A secure server rejects these immediately.

**Steps (using jwt.io):**
1. Pasted the token into the jwt.io debugger.
2. Changed the header from `"alg": "RS256"` to `"alg": "none"`.
3. Changed the payload from `"sub": "wiener"` to `"sub": "administrator"`.
4. The result is a token ending in a **trailing dot** with no signature (`header.payload.`), an "Unsecured JWT" per RFC 7519 §6.
5. Replaced the cookie, refreshed, accessed `/admin` and deleted `carlos`.

**Difference from Lab 1:** two modifications (header `alg` and payload `sub`) and an empty signature.

## Tools & Techniques

- **DevTools → Console:** `atob()` / `btoa()` for Base64URL decoding and encoding, `split(".")` to separate token parts, string concatenation to rebuild the token
- **DevTools → Storage → Cookies:** view and edit the `session` cookie
- **jwt.io debugger:** visual decoding and rebuilding, especially useful when the header must change
- **HttpOnly cookies:** the `session` cookie is HttpOnly, so JavaScript cannot read it (`document.cookie` returns empty). It must be edited manually in Storage or through a proxy such as Burp.

## Defensive Takeaways

- **Root cause (both labs):** broken server-side signature verification.
  - Lab 1: the signature is never checked.
  - Lab 2: `alg: none` is accepted.
- **Fix:** verify the signature on every request, reject `alg: none`, and enforce an **allowlist** of expected algorithms.
- **SOC detection ideas:**
  - Tokens whose header contains `"alg": "none"`
  - A sudden change in the `sub` claim for an existing session
  - Maps to **privilege escalation / account takeover** scenarios

## Next Up

**JWT authentication bypass via weak signing key** (Practitioner): cracking the HMAC secret with hashcat (`-m 16500`) and a wordlist, then re-signing a forged token. In progress.

---
*All work was performed in PortSwigger Web Security Academy's intentionally vulnerable lab environments.*
