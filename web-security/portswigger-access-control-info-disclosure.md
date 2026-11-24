# PortSwigger Web Security Academy: Access Control & Information Disclosure

**7 Apprentice-level labs** · November 2026

Labs covering broken access control and information disclosure: cases where an application trusts the client, exposes sensitive data or fails to enforce authorization on the server.

**The common thread:** every authentication and access-control check must happen **server-side**, never only in the UI.

## Labs Overview

| # | Lab | Vulnerability class | Tool used |
|---|-----|---------------------|-----------|
| 1 | Unprotected admin functionality with unpredictable URL | Access control / security through obscurity | Browser (view source) |
| 2 | User ID controlled by request parameter | IDOR (horizontal privilege escalation) | Browser (URL editing) |
| 3 | User role controlled by request parameter | Forgeable cookie | DevTools (Storage) |
| 4 | Source code disclosure via backup files | Information disclosure | Browser (`robots.txt`) |
| 5 | 2FA simple bypass | Broken authentication (UI-only control) | Browser (direct navigation) |
| 6 | Exploiting an API endpoint using documentation | Broken API access control | DevTools (Edit and Resend) |
| 7 | Information disclosure in version control history | Exposed `.git` directory | git-dumper + git |

## Lab Details

### 1. Unprotected admin functionality with unpredictable URL
- **Vulnerability:** the admin panel sits at an "unguessable" URL, but the URL is leaked in the home page's JavaScript.
- **Solution:** viewing the page source revealed a JS block setting the admin link (`/admin-<random>`). Browsing to it directly gave full admin access.
- **Lesson:** hiding a URL is not access control; once it leaks there is no protection left. **Fix:** enforce authorization server-side on every admin endpoint.

### 2. User ID controlled by request parameter (IDOR)
- **Vulnerability:** the account page loads user data by a URL parameter (`?id=wiener`) without checking who it belongs to.
- **Solution:** changing the parameter to `?id=carlos` exposed another user's API key.
- **Lesson:** never trust a client-supplied identifier. The server must verify that the logged-in user is allowed to access the requested resource.

### 3. User role controlled by request parameter
- **Vulnerability:** the server decides who is an admin based on a forgeable cookie (`Admin=false`).
- **Solution:** changed the cookie to `Admin=true` in DevTools → Storage, then accessed `/admin`.
- **Lesson:** client-side data such as cookies can be freely modified. Roles must be stored and checked server-side (server-side session).

### 4. Source code disclosure via backup files
- **Vulnerability:** `.bak` backup files in a "hidden" directory expose source code containing a hard-coded secret.
- **Solution:** `robots.txt` revealed `Disallow: /backup`. Inside, `ProductTemplate.java.bak` contained a hard-coded database password.
- **Lesson:** `robots.txt` advertises exactly what you are trying to hide. **Fix:** never leave backup files on a production server, and never store secrets in code.

### 5. 2FA simple bypass
- **Vulnerability:** the 2FA step is enforced only in the UI; the server already logs the user in after the password step.
- **Solution:** logged in with the victim's credentials up to the code prompt, then navigated directly to `/my-account` without entering a code.
- **Lesson:** every authentication step must be enforced server-side. The server must deny access until the code is actually verified.

### 6. Exploiting an API endpoint using documentation
- **Vulnerability:** publicly exposed API documentation reveals endpoints and HTTP methods that the UI hides, including `DELETE`.
- **Solution:** the HTML referenced `/api/user`; browsing to `/api` revealed REST documentation with `GET` / `DELETE` / `PATCH` on `/user/[username]`. In DevTools → Network → **Edit and Resend**, I took a real `PATCH` request, changed the method to `DELETE` and the username to the target, and sent `DELETE /api/user/carlos`.
- **Lesson:** the UI may hide an action that the API still supports. Enforce authorization on every method of every endpoint, and do not expose API documentation publicly.

### 7. Information disclosure in version control history
- **Vulnerability:** an exposed `.git` directory allows reconstruction of the full code history, including secrets that were "deleted".
- **Solution:** `git-dumper https://TARGET/.git/ ./repo` pulled the repository. `git log` showed a commit named *"Remove admin password from config"*, and `git show <commit>` revealed the removed password in the diff, which allowed logging in as `administrator`.
- **Lesson:** nothing is truly deleted in git, and a secret removed in a later commit stays in history. Never expose `.git`, never commit secrets, and if it happens, **rotate** the secret rather than just deleting it.

## When to Use Which Tool

**Browser / DevTools is enough** when the target can be seen and modified directly:
- changing a URL parameter (lab 2)
- editing a visible cookie in Storage (lab 3)
- reading source code, JS or exposed files (labs 1, 4)
- sending a request from the Console (`fetch`) or with **Edit and Resend** (lab 6)

**Burp Suite / a proxy becomes necessary** when manipulating what the browser builds automatically:
- modifying headers, POST bodies or hard-to-edit API requests
- **Repeater**: resending the same request with changes
- **Intruder**: automated brute-force / fuzzing
- capturing traffic from non-browser clients (mobile, CLI)

**CLI / dedicated tools** for automation:
- `git-dumper`: dumping an exposed `.git`
- `git log -p` / `git show`: hunting secrets in history
- `ffuf` / `gobuster`: content discovery (hidden directories and files)

## Tools & Commands Practiced
- **DevTools → Storage**: view and edit cookies
- **DevTools → Network → Edit and Resend**: replay a modified real request (Firefox's alternative to Burp Repeater)
- **DevTools → Console → `fetch(url, {method})`**: send an API request with the existing session
- **`git-dumper <url>/.git/ ./repo`**: reconstruct a repository from an exposed `.git`
- **`git log` / `git log -p` / `git show <commit>`**: investigate commit history and recover deleted changes

## Next Steps
- Practice `ffuf` / `gobuster` for content discovery
- Explore insecure deserialization (`readObject` + `Serializable`), a topic raised by the `.bak` file in lab 4

---
*All work was performed in PortSwigger Web Security Academy's intentionally vulnerable lab environments.*
