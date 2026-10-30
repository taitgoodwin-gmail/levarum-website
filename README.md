# Levarum website

Pre-launch marketing site for Levarum, a trade name of IT Associates, LLC. Plans open Friday, November 13, 2026; the first reports go out Monday, November 16.

Live preview: https://levarum-website.vercel.app

Static site: Home, Pricing, About, Methodology, Terms, Privacy, DPA and a 404 page. Plain HTML and CSS, no build step, no JavaScript, no cookies or analytics.

## Deploy on Vercel
1. Vercel → Add New → Project → import this repository.
2. Framework preset: **Other**. Leave build command and output directory empty.
3. Deploy. Add your domain under Project → Settings → Domains.

Pushing to `main` deploys to production; any other branch gets a preview URL.

## How it is set up
- `vercel.json` turns on clean URLs (`/pricing` serves `pricing.html`). Internal links use clean root paths (`/`, `/pricing`, `/#how`), so no click goes through a redirect.
- Security headers (CSP, HSTS, nosniff, referrer and permissions policies) and cache headers are set in `vercel.json`.
- `levarum-website.vercel.app` is served with `X-Robots-Tag: noindex` so the preview host stays out of search until the real domain is live.
- Fonts (Newsreader, Figtree; SIL OFL 1.1) are self-hosted in `assets/fonts/`.
- Icons: `favicon.ico`, `img/icon.svg` and `apple-touch-icon.png` come from the Levarum design system's favicon and app tile. `img/og-image.png` (1200 × 630) is the share image.
- `img/frame-*.webp` are the compressed frame textures; the PNGs stay as a fallback.
- `/assets/` is cached for 7 days, so every page links the stylesheet as `levarum.css?v=<hash>`. After any change to `levarum.css`, update the `?v=` value on every page (first 8 characters of `sha256sum assets/levarum.css`), or visitors keep the old styles for up to a week.

## Before launch
- **Buy and sign-in:** the plan cards say "Opens Friday, November 13". "Sign in" (header, phone menu, footer) goes to `/signin`, a holding page that says sign-in opens with the plans. At launch, point the plan buttons at Stripe Checkout and change every `href="/signin"` to the app's login URL (or turn `signin.html` into a redirect).
- **Contact address:** none on the site yet. Add a monitored address to Terms, Privacy, DPA and a footer Contact link.
- **Legal:** Terms, Privacy and DPA carry 11 `[COUNSEL TO SUPPLY]` blocks and a "Draft of Oct 29, 2026" line. Counsel completes them; then replace the draft line with "Effective November 13, 2026" and remove the draft notes on those pages and on Methodology.
- **Model name:** Methodology says the exact OpenAI model will be named before launch. Add it there.
- **Domain:** when the real domain is live, replace `https://levarum-website.vercel.app` in every page's `og:url` and `og:image`, the JSON-LD, `robots.txt` and `sitemap.xml`, add canonical tags, and remove the noindex header.
- **Remove the pre-launch lines** ("Plans open Friday, November 13, 2026…") on Home, About and Pricing.
- **Confirm launch scope** for features the site describes: rival suggestions, topic grouping, rolling trend from week four, searchable answers, 15-point alerts, CSV export and emailed-code sign-in.

Source of truth for design changes: the "Levarum website" design canvas in Claude.
