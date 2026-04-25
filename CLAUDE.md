# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running locally

No build step. Serve files over HTTP (required — `file://` blocks relative CSS imports):

```bash
python -m http.server 8000
# or
npx serve .
```

Then open http://localhost:8000. The site is live at https://fyndock-website.vercel.app; the repo is at github.com/utsavmanhas/fyndock-website.

## Architecture

100% static HTML — no framework, no bundler, no JS framework. Eight pages share two CSS files:

- **`colors_and_type.css`** — all design tokens as CSS custom properties: color scales (`--plum-*`, `--gold-*`, `--neutral-*`), semantic aliases (`--surface-*`, `--text-*`, `--border-*`), typography vars, spacing scale, radius, shadow, transition easings. Also defines base resets and semantic type elements (`.display`, `.label`, `.caption`, `.mono`). **Always use tokens — never hardcode color values.**
- **`shared.css`** — shared component styles: `.site-nav`, `.section-wrap`, `.section-eyebrow`, `.section-title`, `.section-body`, button variants (`.btn-primary`, `.btn-ghost`, `.btn-lg-primary`, `.btn-lg-outline`, `.btn-lg-ghost`), `.card` with hover lift, `.site-footer`. Every page imports both files in this order: `colors_and_type.css` first, then `shared.css`.

Page-specific styles live in `<style>` blocks inside each HTML file — there are no per-page CSS files.

## External dependencies (CDN only)

- **Lucide icons**: `https://unpkg.com/lucide@latest/dist/umd/lucide.min.js` — called with `lucide.createIcons()` after DOM ready. Use `<i data-lucide="icon-name"></i>` in markup.
- **Google Fonts**: Playfair Display (display/headings), DM Sans (body/UI), JetBrains Mono (numbers). Imported at the top of both CSS files.

## Per-page JS patterns

All JS is vanilla, inline `<script>` at the bottom of each page. Key patterns:

- **MIS Reports** (`services/mis-reports.html`): `showSheet(id)` toggles `.active` on tab sidebar items and swaps the content panel.
- **Blog** (`blog.html`): JS array of article objects; clicking a card hides `.listing-view` and shows `.article-view`. Back button reverses it.
- **Contact** (`contact.html`): Form is wired to Web3Forms (`https://api.web3forms.com/submit`). Access key `52804aab-3e47-440d-87d5-1d8482771c31` routes submissions to smanhas@spmanhas.com. Honeypot checkbox (`name="botcheck"`, hidden) provides spam protection — Web3Forms silently drops any submission where it is filled. `handleSubmit` does a real `fetch` with a JSON payload; on success it hides the form and shows the success div. On API failure, an inline error box appears with a direct email/phone fallback and the submit button re-enables for retry.
- **Homepage** (`index.html`): Chart bars in the hero Excel mock are rendered via JS. A hidden tweaks panel at bottom-right is exposed via `postMessage` — do not remove it.

## Nav active state

Each page sets `.nav-link.active` on its own link manually in the HTML. When adding or renaming pages, update the active class on all eight pages.

## Design rules

- Dark sections use `--plum-900` or `--plum-950` background with `--text-inverse` (#fff) text.
- The featured/middle pricing card uses `--plum-900` background with a floating badge at `top: -13px`.
- Card hover: `translateY(-2px)` + `--shadow-md`, 200ms `var(--ease-out)`. Already defined on `.card` in `shared.css`.
- Marquee animation: `@keyframes marquee` translates `-50%` over 28s linear infinite; the track is doubled for seamless looping.
- The How It Works connecting line is a `::before` pseudo-element on the grid container, with `z-index: 1` on the step dots so they sit above it.
