# CFC — Where Vision Meets Prosperity

Static marketing site for CFC, led by Edlawit Sefiu. Built on the same
architecture as `amg-wealth`: a single `index.html`, no build step, deployed
on Netlify.

## Structure

```
index.html       full site (intro, hero, services, founder, process, contact)
thank-you.html   Netlify form redirect target
netlify.toml     publish root + security headers
assets/          logo-original.webp (source logo, from the AMG brokerage marquee)
```

## The intro

First visit plays a ~4s moon-eclipse sequence: two champagne crescents drift in
from opposite edges, settle into the interlocked CC monogram, the crown drops
in, a shimmer sweeps across, then the wordmark and tagline open underneath.

- Skippable by click, Esc, or Space
- Plays once per browser session (`sessionStorage.cfcIntroSeen`)
- Fully disabled under `prefers-reduced-motion`

The monogram is inline SVG, not an image — the crescents are real paths
(circle-minus-offset-circle) so they can animate independently. The same mark is
reused in the nav, footer, favicon, thank-you page, and the photo placeholder.

## Before launch — placeholders to replace

| What | Where | Current value |
|---|---|---|
| **Headshot** | `assets/edlawit.jpg` | missing — shows a monogram placeholder panel |
| Email | `index.html` contact + footer | `hello@cfcwealth.com` |
| Phone | `index.html` contact + footer | `(000) 000-0000` |
| Instagram | `index.html` contact + footer | generic instagram.com link |
| Stats | `.stats` section | 140+ / $45M+ / 22 / 97% — invented |
| Testimonial | `.quote-sec` | written, unattributed |
| Her title | `.founder-plate` | "Founder" |
| What CFC stands for | nowhere | never spelled out — acronym only |

Drop the headshot in as `assets/edlawit.jpg` and both the hero and founder
sections pick it up automatically; the placeholder disappears on its own.

## Local preview

```
python3 -m http.server 4187
```
