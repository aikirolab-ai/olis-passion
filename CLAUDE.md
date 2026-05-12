# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Context

Demo and test project for Aikiro Lab clients. Work is frontend-focused: polished web experiences, UI components, and scroll-driven animations. No build system — all output is **vanilla HTML/CSS/JS served via HTTP**.

## Local Development

```bash
# Serve locally (required — canvas frames won't load via file://)
npx serve .
# or
python -m http.server 8000
```

Frame extraction (macOS, FFmpeg required):
```bash
ffprobe -v error -select_streams v:0 -show_entries stream=width,height,duration,r_frame_rate,nb_frames -of csv=p=0 "<VIDEO>"
ffmpeg -i "<VIDEO>" -vf "fps=<FPS>,scale=<WIDTH>:-1" -c:v libwebp -quality 80 "frames/frame_%04d.webp"
```
Target 150–300 frames; cap width at 1920px.

## MCP Configuration

**Active:** `magic` (UI component generation), `stitch` (UI design / screen generation)

**Ignore:** Supabase, Twilio, Gmail, Google Calendar, Granola, Spotify — not authorized for this project.

## Available Skills

### Global
- `ui-ux-pro-max` — UI/UX design with style/palette/font libraries
- `ckm-design` — Brand identity, logo, banners, icons
- `ckm-ui-styling` — shadcn/ui + Tailwind component implementation

### Local (invoke via Skill tool)
- `frontend-design` — Production-grade frontend with intentional aesthetic direction. Use for any web component, page, or application. Commit to a bold conceptual direction; avoid generic AI aesthetics (no Inter/Roboto, no purple gradients, no cookie-cutter layouts).
- `video-to-website` — Converts a video into a scroll-driven animated website. See architecture below.

## Default Design System: Midnight Copper Luxury

`Design.md` defines the full token specification. Key values:

| Token | Value |
|-------|-------|
| Background | `#121416` Cool Charcoal |
| Primary accent (CTA) | `#B87333` Deep Copper |
| Hover accent | `#D9975D` Brushed Copper |
| Body text | `#e2e2e5` Off-White |
| Secondary text | `#8A9196` Slate |
| Card surface | `#1A1D1F` |
| Border | 1px muted copper-tinted grey, brightens on hover |

**Typography:** Headlines → `Playfair Display` (tight tracking, editorial). Body/labels → `Manrope` (line-height 1.6). Labels uppercase with `letter-spacing: 0.1em`.

**Layout:** 1280px container, 8px spacing scale, 24px gutters, 120px+ section gaps. Depth via tonal layering — no drop shadows. Modals use `backdrop-blur: 20px`.

**Components:** Primary button = solid Copper fill. Secondary = transparent + 1px Copper border. Inputs = underlined style, focus transitions underline to Copper. Cards = `#1A1D1F` + 1px border. Checkboxes/Radios = soft Copper outer glow on active (2px blur).

## Video-to-Website Architecture

Output structure (no bundler):
```
project-root/
  index.html
  css/style.css
  js/app.js
  frames/frame_0001.webp ...
```

CDN stack — **load order is mandatory:**
```html
<script src="https://cdn.jsdelivr.net/npm/lenis@1/dist/lenis.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/gsap@3/dist/gsap.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/gsap@3/dist/ScrollTrigger.min.js"></script>
<script src="js/app.js"></script>
```

### 14 Non-Negotiables

1. **Lenis smooth scroll** — always connect `lenis.on("scroll", ScrollTrigger.update)`
2. **4+ animation types** — never repeat the same entrance animation consecutively
3. **Staggered reveals** — label → heading → body → CTA, never all at once
4. **No glassmorphism cards** — hierarchy via font size/weight/color only
5. **Direction variety** — sections enter from different directions
6. **Dark overlay for stats** — 0.88–0.92 opacity; only place centered text is allowed
7. **Horizontal marquee** — at least one oversized text element (12vw+) sliding on scroll
8. **Counter animations** — all numbers count from 0, never static
9. **Massive typography** — hero 12rem+, section headings 4rem+, marquee 10vw+
10. **CTA persists** — `data-persist="true"` keeps final section visible after scroll-past
11. **Hero prominence** — hero gets 20%+ scroll range; total 800vh+ for 6 sections
12. **Side-aligned text only** — all text in outer 40% zones (`align-left`/`align-right`); never centered except stats with dark overlay
13. **Circle-wipe hero reveal** — hero is standalone 100vh; canvas reveals via `clip-path: circle()` as hero scrolls away
14. **Frame speed 1.8–2.2** — product animation completes by ~55% scroll; below 1.8 feels sluggish

### Key JS Patterns

**Canvas renderer (padded cover mode):**
```js
const IMAGE_SCALE = 0.85; // sweet spot 0.82–0.90
// scale = Math.max(cw/iw, ch/ih) * IMAGE_SCALE
// fill canvas with sampled bg color BEFORE drawing frame
```

**Frame-to-scroll binding:**
```js
const FRAME_SPEED = 2.0;
// accelerated = Math.min(self.progress * FRAME_SPEED, 1)
```

**Section animation types:**

| `data-animation` | Initial state | Duration |
|-----------------|---------------|----------|
| `fade-up` | y:50, opacity:0 | 0.9s |
| `slide-left` | x:-80, opacity:0 | 0.9s |
| `slide-right` | x:80, opacity:0 | 0.9s |
| `scale-up` | scale:0.85, opacity:0 | 1.0s |
| `rotate-in` | y:40, rotation:3, opacity:0 | 0.9s |
| `stagger-up` | y:60, opacity:0 | 0.8s |
| `clip-reveal` | clipPath:inset(100% 0 0 0) | 1.2s |

All types use stagger 0.10–0.15s. Default ease: `power3.out` (scale-up: `power2.out`, clip-reveal: `power4.inOut`).

**Anti-patterns:**
- `IMAGE_SCALE` at 1.0 (pure cover) — product clips into header
- `FRAME_SPEED` < 1.8 — sluggish
- Same animation type for consecutive sections
- Centered text grids over canvas — use vertical lists in the 40% side zone
- Serving via `file://` — breaks canvas frame loading

## Dual-Theme Architecture

Le projet utilise deux thèmes distincts définis dans `Design.md` :

1. **Midnight Copper Luxury** (Manrope / Cuivre) : 
   - Cible : `index.html` et dossier `/dashboard/`.
2. **Midnight Creole Luxury** (Hanken Grotesk / Or) : 
   - Cible : `menu.html`, `vin.html`, `cocktails.html`.

**Règle d'implémentation :** Appliquer la classe `.theme-copper` ou `.theme-creole` sur le `<body>` pour piloter les variables CSS des tokens.