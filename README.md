# CatalystOS Pilot Offer

Single-page static site. The whole page is self-contained in `index.html`
(fonts, images, and the laptop demo are inlined — no build step, no runtime files).

## Deploy
- **Vercel / Netlify / GitHub Pages:** point the host at the repo root.
  There is no build command and no output directory — it is plain static HTML.
- The production URL always serves the latest push. Preview URLs that contain a
  random hash (e.g. `-huk5hp48j`) are frozen snapshots and never update.

## Update
Replace `index.html` at the repo root, commit, and push.
