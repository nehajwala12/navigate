# Project Navigate — Final Package (creditswan.ai)

Static single-page deployment of `CREDITSWAN_NAVIGATE_FINAL_PACKAGE.md`
(Revision 2, 27 Jul 2026), branded to the creditswan.ai document system.

## Deploy to Vercel

Option A — CLI (from this folder):

    npm i -g vercel
    vercel          # preview
    vercel --prod   # production

Option B — dashboard: vercel.com → Add New → Project → drag this folder in.
No framework, no build step; Vercel serves `index.html` as-is.

## ⚠ Before sharing any URL

This document is CONFIDENTIAL — ARES INTERNAL and derives from a live
auction VDR. A Vercel deployment is publicly reachable by default.

1. In the Vercel project: Settings → Deployment Protection → enable
   Vercel Authentication (or Password Protection on paid plans) BEFORE
   circulating the link.
2. `noindex` headers and meta tags are included, but they are not access
   control — they only ask crawlers to stay away.
3. The safest distribution remains the file itself, not a URL.

## Contents

- `index.html` — the branded, self-contained page (fonts via Google Fonts CDN,
  degrades to system fonts offline; print stylesheet included)
- `CREDITSWAN_NAVIGATE_FINAL_PACKAGE.md` — the verbatim source document
- `vercel.json` — noindex/security headers
