# CatalystOS — Overview Page (Vercel-ready static site)

A responsive single-page marketing/proposal site for **CatalystOS: The AI Marketing Platform**,
with three embedded interactive product demos (Platform Dashboard, Event Graphics Builder, Post Builder).

This is a pure **static site** — no build step, no server code. It renders entirely in the browser.

## Deploy to Vercel

### Option A — Drag & drop (fastest)
1. Go to https://vercel.com/new
2. Drag this whole folder onto the page (or zip it and upload).
3. When asked for framework, choose **Other** (no framework / no build command).
4. Click **Deploy**. Done — Vercel serves `index.html` at `/`.

### Option B — Vercel CLI
```bash
npm i -g vercel      # if you don't have it
cd catalystos-site   # this folder
vercel               # follow the prompts, accept defaults
vercel --prod        # promote to production
```
There is no build command and no output directory to set — it's a static folder.

### Option C — Git
Push this folder to a GitHub/GitLab repo and "Import Project" in Vercel.
Framework preset: **Other**. Build command: *(leave empty)*. Output dir: *(leave empty / `.`)*.

## How it works / notes
- `index.html` is the overview page. The three demos live under `demos/` and open in a
  laptop-style modal when you click a thumbnail.
- The page uses a small client-side runtime (`support.js`) that loads React from a CDN at
  runtime and renders the design. **It requires HTTP(S)** — opening the files by double-clicking
  (`file://`) will show blank demos because browsers block `fetch()` on `file://`. Vercel (or any
  static host) serves over HTTPS, so everything works once deployed.
- The page is marked `noindex, nofollow` (confidential preview). Remove those meta tags in
  `index.html` if you want it publicly indexable.
- `HANDOFF-NOTES.md` is the original design handoff documentation (brand tokens, section spec).

## Local preview
```bash
cd catalystos-site
python3 -m http.server 8080
# open http://localhost:8080
```
