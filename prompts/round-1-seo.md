# Round 1 — SEO + tiny cleanups

A batched, low-risk set of fixes from the site audit. All changes are confined to `<head>` tags or small HTML tweaks. No layout/CSS work. No JS work.

Goal: ship in one commit titled "Round 1: SEO meta tags, favicon, footer cleanup".

## What to do

### 1. Favicon — every page
Add the favicon link in the `<head>` of every HTML file. Use `assets/logo-mark.svg` as the icon source.

- For files in the root folder (`index.html`, `about.html`, `blog.html`, `case-studies.html`, `contact.html`, `how-it-works.html`):
  ```html
  <link rel="icon" type="image/svg+xml" href="assets/logo-mark.svg">
  ```
- For files in `services/` (`mis-reports.html`, `virtual-cfo.html`):
  ```html
  <link rel="icon" type="image/svg+xml" href="../assets/logo-mark.svg">
  ```

### 2. Meta descriptions — every page (~155 chars each, distinct per page)

Write a sharp, marketer-quality description for each page. Each one should mention the value prop and feel like a SERP snippet a CFO/founder would click.

- `index.html` — the homepage's value prop: CFO-grade financial intelligence + monthly MIS + Virtual CFO for Indian startups
- `services/mis-reports.html` — focused on monthly MIS reports: management reporting, KPI dashboards, board-ready
- `services/virtual-cfo.html` — fractional/Virtual CFO for growth-stage companies: cap table, fundraising prep, board reporting
- `how-it-works.html` — engagement model and process
- `case-studies.html` — proof / outcomes from real engagements
- `about.html` — the firm and the founders
- `blog.html` — insights on financial reporting, fundraising, MIS
- `contact.html` — get a sample MIS / book a discovery call

### 3. Open Graph tags — every page
Add to every page's `<head>`:
```html
<meta property="og:title" content="[same as <title>]">
<meta property="og:description" content="[same as meta description]">
<meta property="og:image" content="https://fyndock-website.vercel.app/assets/logo.svg">
<meta property="og:url" content="https://fyndock-website.vercel.app/[path]">
<meta property="og:type" content="website">
<meta property="og:site_name" content="Fyndock">
```

For each page, set the correct `og:url`:
- index.html → `https://fyndock-website.vercel.app/`
- about.html → `https://fyndock-website.vercel.app/about.html`
- blog.html → `https://fyndock-website.vercel.app/blog.html`
- case-studies.html → `https://fyndock-website.vercel.app/case-studies.html`
- contact.html → `https://fyndock-website.vercel.app/contact.html`
- how-it-works.html → `https://fyndock-website.vercel.app/how-it-works.html`
- services/mis-reports.html → `https://fyndock-website.vercel.app/services/mis-reports.html`
- services/virtual-cfo.html → `https://fyndock-website.vercel.app/services/virtual-cfo.html`

### 4. Twitter Card tags — every page
```html
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="[same as title]">
<meta name="twitter:description" content="[same as meta description]">
<meta name="twitter:image" content="https://fyndock-website.vercel.app/assets/logo.svg">
```

### 5. Canonical URL — every page
```html
<link rel="canonical" href="[same as og:url]">
```

### 6. Fix dead `<a>` tags in footer (audit issue #7)
- `index.html:569–570` — `<a>Dwarka, New Delhi 110078</a>` and `<a>Janakpuri, New Delhi 110058</a>`. Replace each with `<span>...</span>` and copy any styling needed.
- `contact.html:237–238` — same pattern, same fix.

If the same dead-`<a>` pattern exists in any other page's footer, fix those too.

### 7. Fix Virtual CFO nav active label (audit issue #8)
In `services/virtual-cfo.html` near line 49:

Change:
```html
<a class="nav-link active" href="virtual-cfo.html">Services</a>
```
to read "Virtual CFO" instead of "Services" (so the active label matches the page).

## Workflow

Process file by file. For each file:
1. Show me the diff before applying.
2. Wait for my approval (yes / no / change X).
3. Apply, move to next file.

After all 8 files are updated:
1. Show me a single combined summary of what changed.
2. Run `git status` so we both see the change set.
3. Commit with message: `Round 1: SEO meta tags, favicon, footer cleanup`
4. Push to origin/main.

Skip everything outside this scope — no mobile responsiveness, no accessibility, no JS changes, no CSS reorganization. Those are separate rounds.
