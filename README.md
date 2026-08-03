# Project Navigate — Final Credit Diligence Package · Rev 2 (locked)

`index.html` is the sealed client edition: the full document is AES-256-GCM
encrypted; the key is derived in-browser (PBKDF2-SHA256, 600,000 iterations,
random salt/IV). A wrong password fails the GCM auth tag; view-source shows
ciphertext only. The access password is distributed separately — it is not
stored in this package.

Deploy: `vercel --prod` from this folder. Vercel Deployment Protection is
recommended as an independent second layer. Client-side crypto protects the
file at rest and in URL transit; anyone holding file + password has the content.
