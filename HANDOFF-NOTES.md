# Handoff: CatalystOS — Marketing Platform Overview Page + Demos

## Overview
A single-page marketing/proposal site for **CatalystOS: The AI Marketing Platform**. It presents the product vision, the problem/solution framing, the range of deliverables the platform produces, ROI stats, a "Founding Pilot Partner" offer, and three embedded interactive product demos (opened in modal/laptop views).

## About the Design Files
The files in this bundle are **design references created in HTML** — a working prototype showing the intended look, copy, and behavior. They are **not** production code to ship directly. The task is to **recreate this design in the target codebase's environment** (React, Vue, Svelte, etc.) using its established patterns, component library, and conventions. If no environment exists yet, pick the most appropriate framework and implement there.

Note: the HTML is authored as a "Design Component" (a custom `<x-dc>` runtime driven by `support.js`). **Do not port the runtime.** Treat the rendered output as the spec — read the inline styles and copy, and rebuild with normal components. The `support.js` file is included only so the prototype renders when served.

## Fidelity
**High-fidelity (hifi).** Final colors, typography, spacing, copy, and interactions are all present. Recreate the UI pixel-accurately using the target codebase's libraries.

## Brand & Design Tokens

### Colors
- Page background: `#F5F7FA` (with subtle white + purple radial gradients)
- Primary navy (text/ink): `#081A53`, secondary body text `#132A63`, muted `#59627A`, light muted `#A6AEC0`
- Brand accent purple: `#6D28D9` (also `#6818F8` / `#8A2BD4` in gradients)
- Brand gradient (used on "OS", accents, checkmarks): `linear-gradient(120deg, #1921FE, #6818F8, #C1229C, #FD5920)` — blue → purple → magenta → orange
- Highlight yellow (pastel check bg): `#FEF3C7` with stroke `#D9A404`; gold accent `#FDBD5A`
- Card surfaces: white `#FFFFFF`; light chip/list bg `#F4F6FA` / `#EEF1F8`; border `rgba(8,26,83,0.09–0.18)`
- Dark section (pilot): navy gradient background, text `#FFFFFF` / `#CBD4EC` / `#AEB9D8`

### Typography
- Headings/display: **Manrope** (weights 400–800; headings use 800)
- Body/UI: **Inter** (weights 400–600)
- Loaded from Google Fonts.
- Section headings: `clamp(25px, 6vw, 38px)`, weight 800. Pilot header `clamp(28px, 7vw, 40px)`.
- Body copy: 15–16px, line-height ~1.5–1.65. List items 13px.

### Spacing / Radius / Shadow
- Top-level content column: `max-width: 940px`, centered.
- Card radius: 14–16px; chips 6–7px.
- Shadows: soft, e.g. `0 30px 60px -30px rgba(8,26,83,0.7)` for elevated cards.
- Animations: `hcFade`, `hcRise` (translateY 14px), `hcPop`, glow/pulse keyframes — subtle entrance transitions, ~0.5s ease.

## Screens / Sections (top to bottom)
1. **Header** — centered CatalystOS logo (`brand/logo-t.png`, transparent). No auth/gate — page is open to all.
2. **Hero / vision** — headline + supporting copy.
3. **Stats row** — three stat cards: `10–100 Apps`, `~10× Capacity`, `85–90% Less production time`, each with a caption (one word/phrase gradient-highlighted, e.g. the "OS" in CatalystOS).
4. **"What CatalystOS does" + deliverable grid** — intro line, then a responsive grid (`.hc-deliv-grid`, `repeat(auto-fill, minmax(150px,1fr))`, 2 cols on mobile) of 20 deliverables each with a small gradient dot, ending in a bold "& much more". Current order: Websites, Landing Pages, Social Media Posts & Graphics, Presentation Decks, Fact Sheets & One-Pagers, Webinar & Event Campaign Assets, Blog Articles, Email Campaigns & Newsletters, Campaign Creative Kits, Calls to Action (CTAs), Case Studies, Executive Thought Leadership, White Papers & eBooks, Infographics, Proposal & RFP Templates, Brand Guidelines, Brochures & Booklets, Annual Reports, Marketing Dashboards, LinkedIn Profile Optimization.
5. **Problem → Fix → What you get rows** (`.psr-row`, 4 rows labeled **Problem 1–4**), separated by rule dividers with generous vertical spacing. On mobile each row stacks vertically and the connecting arrow rotates 90°.
6. **Interactive demos** — three clickable thumbnails that open product demos:
   - `demos/CatalystOS Interactive Laptop.dc.html` — Platform Dashboard
   - `demos/Post Builder Laptop.dc.html` — Post Builder
   - `demos/event-graphics/Event Graphics Laptop.dc.html` — Event Graphics
7. **Founding Pilot Partner** (dark navy section) — "A limited 3-month joint-venture pilot, by invitation only." with subsections: *How we'll work together*, *How to choose your two projects* (3 criteria w/ gradient checkmarks), *What's included* (2 items with gradient checkmarks).
8. **The ask / finale**.

(A "Reclaim the time" model section was removed from the live page but preserved at `saved-blocks/reclaim-the-time.html` in the source project.)

## Interactions & Behavior
- Entrance animations on scroll/load (`hcRise`, `hcFade`, `hcPop`).
- Demo thumbnails: click → open the corresponding demo in a modal/laptop frame.
- Fully responsive: a single `@media (max-width: 768px)` block restructures nearly every section to a single column (see the source `<style>` for exact per-section overrides).
- Hover states on chips/cards (subtle bg shifts).

## ⚠️ Critical: demos require HTTP, not file://
The page and demos load content and nested builders via `fetch()`. `fetch()` is **blocked on `file://`**, so the demos appear blank if the HTML is opened by double-clicking. Serve over HTTP (`python3 -m http.server`, any static host, or GitHub Pages). This is a property of the prototype runtime — in a real app the demo content would be rendered as components/routes and this constraint disappears.

## Assets
- `brand/logo-t.png` — CatalystOS logo (transparent).
- Demo assets live under `demos/**` (fonts, images, inner builder HTML).
- Fonts: Manrope + Inter (Google Fonts).

## Files
- `Demo Access.dc.html` — the overview page (main design reference).
- `support.js` — prototype runtime (reference only; do not port).
- `brand/` — logo assets.
- `demos/` — the three linked interactive demos + their assets.
