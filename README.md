# Levarum website

Static site: Home, Pricing, About, Methodology, Terms, Privacy and DPA. Plain HTML and CSS, no build step.

## Deploy on Vercel
1. Vercel → Add New → Project → import this repository.
2. Framework preset: **Other**. Leave build command and output directory empty.
3. Deploy. Add your domain under Project → Settings → Domains.

`vercel.json` turns on clean URLs, so `/pricing` serves `pricing.html`.

## Before launch
- "Sign in" and the "Start with …" plan buttons link to `#` until the app and Stripe checkout URLs exist.
- Methodology, Terms, Privacy and DPA are marked draft pending legal review.
- Methodology still has the `[MODEL NAME]` placeholder.

Source of truth for design changes: the "Levarum website" design canvas in Claude.
