# Handoff: Fyndock Website — Full 8-Page Marketing Site

## Overview
A complete marketing website for Fyndock, a Virtual CFO and MIS reporting service for Indian startups. Built as high-fidelity HTML prototypes with full navigation, interactive components, and a working contact form. The task is to recreate these designs in your target environment (e.g. Next.js, Astro, plain HTML hosted on Vercel/Netlify, etc.).

## About the Design Files
The files in this bundle are **design references created in HTML** — high-fidelity prototypes showing the intended look, content, and behaviour. They are not production-ready code. Your task is to **recreate these designs in your target codebase** using its established framework and patterns.

Open the HTML files in a browser to see the full design. They are self-contained and reference only two shared CSS files (`colors_and_type.css` and `shared.css`) plus the `assets/` folder for logos.

## Fidelity
**High-fidelity.** Final colors, typography, spacing, copy, and interactions are all defined. Implement pixel-closely using your codebase's component library — or directly ship the HTML if you are using a static site approach.

---

## Pages & Files

| Page | File | URL path |
|------|------|----------|
| Homepage | `index.html` | `/` |
| MIS Reports | `services/mis-reports.html` | `/services/mis-reports` |
| Virtual CFO | `services/virtual-cfo.html` | `/services/virtual-cfo` |
| How It Works | `how-it-works.html` | `/how-it-works` |
| Case Studies | `case-studies.html` | `/case-studies` |
| About | `about.html` | `/about` |
| Blog | `blog.html` | `/blog` |
| Contact | `contact.html` | `/contact` |

---

## Design Tokens

All tokens are in `colors_and_type.css`. Key values:

### Colors
```
--plum-900: #1C1527   (dark backgrounds, hero)
--plum-800: #2A1F3D   (primary CTA buttons)
--plum-50:  #F6F4FA   (subtle backgrounds)
--gold-500: #C4A35A   (primary accent)
--gold-400: #D4B878   (hero italic, hover)
--gold-600: #B8852A   (links, labels)
--neutral-50: #FAF9F6 (page background)
```

### Typography
```
Display / H1 / H2: 'Playfair Display', serif (weights 400, 500)
Body / UI:         'DM Sans', sans-serif (weights 300, 400, 500, 600)
Numbers / Mono:    'JetBrains Mono', monospace (weights 400, 500)
```

### Spacing Scale
```
4 / 8 / 12 / 16 / 20 / 24 / 32 / 40 / 48 / 64 / 80 / 96px
```

### Border Radius
```
--radius-sm: 4px  --radius-md: 6px  --radius-lg: 10px  --radius-xl: 16px  --radius-full: 9999px
```

### Shadows
```
--shadow-xs: 0 1px 2px rgba(42,31,61,0.06)
--shadow-sm: 0 1px 4px rgba(42,31,61,0.08), 0 1px 2px rgba(42,31,61,0.06)
--shadow-md: 0 4px 16px rgba(42,31,61,0.10), 0 1px 4px rgba(42,31,61,0.06)
--shadow-lg: 0 8px 32px rgba(42,31,61,0.12), 0 2px 8px rgba(42,31,61,0.08)
```

---

## Page-by-Page Notes

### Homepage (`index.html`)
The most complex page. Key sections:

1. **Sticky Nav** — Logo left, 5 nav links center, "Book a Call" (ghost) + "Get Free Sample" (gold-on-plum) right. Backdrop blur on scroll.

2. **Hero** — Plum-900 background. Left: eyebrow + Playfair 54px headline with italic gold word, body copy, two CTAs, proof bar. Right: faux Excel window showing an MIS report (crafted in HTML/CSS — not a screenshot). The Excel mock has: macOS titlebar, Excel green ribbon, formula bar, KPI tiles (green/red tinted), a bar chart (JS-generated), a CFO narrative box with a red-flag callout, and 8 sheet tabs at the bottom.

3. **Marquee** — Infinite-scroll marquee strip on `--plum-950` background. CSS `@keyframes marquee` animation.

4. **Problem Section** — Plum-900 bg. 3-column cards, each with a numbered "problem" and a "Fyndock Fix." No icons — pure text hierarchy.

5. **Services** — White bg. 3 pricing cards. Middle card is "featured" (plum-900 bg). Has a floating badge positioned `top: -13px`.

6. **How It Works** — 3 steps with a horizontal line connecting their circular step numbers. `::before` pseudo-element on the grid container.

7. **Industries** — 4-column grid of 8 tiles. Each has an icon, name, and 2 lines of KPI labels in JetBrains Mono.

8. **Credibility** — Plum-900 bg. 4-stat bar, body copy, and a gold-bordered italic callout quote.

9. **CTA Banner** — Gold-100 background. Centered. Single heading, body, one button.

10. **Footer** — Plum-950. 2-column layout: brand left, links right in 3 columns.

**Tweaks Panel:** A hidden panel (shown via postMessage protocol) with 3 controls: hero font toggle, featured card style, section density. Lives bottom-right, `position: fixed`.

---

### MIS Reports (`services/mis-reports.html`)
Interactive **8-sheet tab explainer** — clicking a sheet name in the left sidebar swaps the content panel on the right. Implemented with a simple JS `showSheet()` function toggling `.active` class. No framework needed.

Below: a standard 3-tier pricing grid (Starter / Growth / Enterprise).

---

### Virtual CFO (`services/virtual-cfo.html`)
Three-column deliverables grid — Monthly / On Demand / Strategic Advisory. Each column has icon+text rows.

Dark "differentiators" section on plum-900 with 4 cards (2×2 grid).

---

### How It Works (`how-it-works.html`)
**Two-column sticky layout per phase** — left column is `position: sticky; top: 88px` with phase name/number/timeline badge. Right column is a vertical list of steps with a connecting line (`::before` on container, `z-index: 1` on dots so they sit above the line).

---

### Case Studies (`case-studies.html`)
Each case card uses a **2-column inner grid** — sidebar (220px, plum-50 bg) + body. The body itself is a 3-column grid for Problem/What We Did/Result, with a full-width outcome row at the bottom.

---

### About (`about.html`)
Two-column origin section. Team cards with avatar initials (plum-800 circle, gold letter). Offices section on plum-900.

---

### Blog (`blog.html`)
3-column card grid. Clicking a card **hides the listing view and shows an article view** (same page, no navigation). Article view has a 2-column layout with a sticky sidebar CTA. Back button returns to listing.

All 6 articles have full body content written into a JS array — no CMS needed for the prototype.

---

### Contact (`contact.html`)
Two-column layout: contact details left, form right. Form has a **success state** — on submit, the form is hidden and a success message shown. Wire the form to a backend (Formspree, Resend, etc.) before shipping.

---

## Shared Components

### `shared.css`
Contains: site nav styles, section primitives, button variants (`.btn-primary`, `.btn-ghost`, `.btn-lg-primary`, `.btn-lg-outline`, `.btn-lg-ghost`), card base, footer, and mono utility classes.

### Nav
Same nav on every page. Active state: `.nav-link.active` class on the current page's link. Sticky with `backdrop-filter: blur(16px)`.

### Footer
Same footer on every page. Three link columns: Services / Company / Contact.

---

## Assets
- `assets/logo.svg` — full logo (dark bg)
- `assets/logo-light.svg` — full logo (light bg)
- `assets/logo-mark.svg` — mark only

External CDN:
- Lucide icons: `https://unpkg.com/lucide@latest/dist/umd/lucide.min.js` — called with `lucide.createIcons()` after DOM ready
- Google Fonts: Playfair Display, DM Sans, JetBrains Mono

---

## Interactions & Animations
- **Card hover:** `transform: translateY(-2px)` + `box-shadow` transition, 200ms `cubic-bezier(0.2, 0, 0, 1)`
- **Nav link hover:** color transition 150ms
- **Marquee:** `@keyframes marquee` — translate `-50%` over 28s linear infinite. Track is doubled so it loops seamlessly.
- **Accordion (MIS page):** JS class toggle, no animation needed
- **Blog article toggle:** JS `.active` / `.hidden` class toggle
- **Contact form:** JS `e.preventDefault()` → hide form → show success div

---

## How to Run Locally
```bash
# Option 1: Python (no install needed)
python3 -m http.server 8080
# Then open http://localhost:8080

# Option 2: Node
npx serve .
# Then open the printed URL

# Option 3: VS Code
# Install the "Live Server" extension, right-click index.html → Open with Live Server
```

> ⚠️ The files **must be served over HTTP**, not opened as `file://` URLs — some browsers block relative CSS imports on file:// protocol.

---

## Contact Form Backend
The form currently shows a success state on submit without sending data. To wire it up:
- **Formspree**: add `action="https://formspree.io/f/YOUR_ID"` and `method="POST"` to the `<form>` tag, remove the JS `handleSubmit`
- **Resend / Postmark**: add a serverless function (Vercel, Netlify Functions) that POSTs to the API
- **EmailJS**: drop in the SDK and call `emailjs.sendForm()` in `handleSubmit`
