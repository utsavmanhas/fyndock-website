# Fyndock Website

Marketing website for **Fyndock** — Virtual CFO and MIS reporting service for Indian startups.

## What's in this folder

This is a static HTML/CSS site (8 pages). Just open `index.html` in a browser to view it.

```
fyndock-website/
├── index.html              # Homepage
├── about.html              # About page
├── how-it-works.html       # How It Works
├── case-studies.html       # Case Studies
├── blog.html               # Blog index
├── contact.html            # Contact form
├── services/
│   ├── mis-reports.html    # MIS Reports service page
│   └── virtual-cfo.html    # Virtual CFO service page
├── colors_and_type.css     # Design tokens (colors, typography)
├── shared.css              # Shared component styles
├── assets/                 # SVG logos
└── DESIGN_HANDOFF_README.md  # Original design handoff notes — read for design system reference
```

## Preview locally

Just double-click `index.html` — it opens in your browser. No build step.

For a slightly nicer experience that handles relative links cleanly, run a tiny local server:

```bash
# Option A — Python (built into Windows once Python is installed)
python -m http.server 8000

# Option B — Node
npx serve .
```

Then open http://localhost:8000

## Deploy to the internet (free)

1. Push this folder to a GitHub repository.
2. Sign in to https://vercel.com with your GitHub account.
3. Click **Add New → Project**, import this repo, click **Deploy**. Done — you'll get a `*.vercel.app` URL in ~30 seconds.
4. To use a custom domain like `fyndock.com`, buy it on Namecheap/GoDaddy (~₹800/yr), add it in Vercel's domain settings, and follow the DNS instructions.

## Tech notes

- 100% static HTML — no framework, no build, no JavaScript framework dependencies.
- Two CSS files: `colors_and_type.css` (design tokens) and `shared.css` (shared components).
- Fonts loaded from Google Fonts: Playfair Display (display), DM Sans (body), JetBrains Mono (numbers).
- See `DESIGN_HANDOFF_README.md` for the full design system documentation.
