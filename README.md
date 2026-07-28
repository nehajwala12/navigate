# Project Navigate — Final Credit Diligence Package (Final, client edition) · Vercel deployment

Static, zero-build deployment of `creditswan_navigate_ares.html` (renamed `index.html`).
Everything — CSS, JS, charts — is inline in the single file. The only external requests
are Google Fonts (Source Serif 4, Inter); without internet the page still renders on
system serif/sans fallbacks.

## Built-in password gate

`index.html` is **encrypted** (AES-256-GCM; key derived in-browser from the access
password via PBKDF2-SHA256, 600,000 iterations). Without the password the file is
ciphertext — viewing source reveals nothing. Decryption happens locally in the
recipient's browser; nothing is transmitted. The password is **not** written in this
package — distribute it through a separate channel. To change the password, the file
must be re-issued (there is no server-side reset).

## ⚠ Read this before deploying

This document is **CONFIDENTIAL — ARES INTERNAL** and contains material derived from a
live auction VDR. A Vercel deployment is **publicly reachable by anyone with the URL**
unless you enable access protection. The `noindex` meta, `robots.txt` and `X-Robots-Tag`
header in this package prevent search-engine *indexing* — they do **not** prevent
*access*. An unguessable `*.vercel.app` URL is obscurity, not security.

**After the first deploy, immediately enable one of:**

1. **Vercel Authentication** (all plans): Project → Settings → Deployment Protection →
   enable for **Production and Preview**. Only logged-in members of your Vercel
   team can open the page.
2. **Password Protection** (Pro/Enterprise): same screen — sets a shared password,
   usable for people outside your Vercel team (e.g. the Ares deal team).
3. If neither is acceptable, do not deploy publicly — open `index.html` locally or
   host it behind your own SSO.

## Deploy — Option A: CLI (no Git needed)

```bash
cd creditswan-navigate-vercel
npx vercel          # first run: log in, accept defaults ("Other" framework, no build)
npx vercel --prod   # promote to production
```

## Deploy — Option B: Git import

1. Push this folder to a **private** repository.
2. vercel.com/new → import the repo.
3. Framework preset: **Other** · Build command: *(none)* · Output directory: `./`
4. Deploy, then enable Deployment Protection as above.

## What's in the package

| File | Purpose |
|---|---|
| `index.html` | The client-edition dashboard-memo, sealed behind the password gate (AES-256-GCM) |
| `vercel.json` | Response headers: `X-Robots-Tag: noindex`, `X-Frame-Options: DENY`, `nosniff`, `no-referrer`, `Cache-Control: no-store`, CSP scoped to self + Google Fonts |
| `robots.txt` | Disallows all crawlers |
| `README.md` | This file |

## Local preview

```bash
npx serve creditswan-navigate-vercel
# or simply open index.html in a browser
```

## Updating to a future revision

Replace `index.html` with the new revision's HTML (keep the filename), re-run
`npx vercel --prod`. Nothing else changes.
