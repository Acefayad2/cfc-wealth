# CFC — Where Vision Meets Prosperity

Static marketing site for CFC, led by Edlawit Sefiu. Single `index.html`, no
build step, deployed on Netlify.

## Design direction

Deliberately **not** a recolour of `amg-wealth`. Where AMG alternates dark and
cream sections around a bento grid, CFC is **night-first** — no light sections
at all, tonal navy bands under a fixed starfield, with a cool silver-blue
running alongside the champagne so it never reads as "AMG in blue".

The moon is the organising idea, not a decoration:

- **The Phases** — the client process told as lunar phases (new -> waxing
  crescent -> first quarter -> full), drawn as real SVG moons. The signature
  section, and the thing AMG has no equivalent of.
- **Disciplines** carry moon-phase glyphs instead of line icons.
- **Centred hero** under orbital rings and a moon glow, rather than AMG's
  left-text / right-photo split.
- **Arched portrait frames** — a dome crop echoing the crescent.
- **A scroll-progress moon**, bottom right, that waxes as you move down.
- Type is Bodoni Moda (kept: it matches the didone in her logo) + **Outfit**,
  replacing AMG's Jost.

## Structure

```
index.html       full site (intro, hero, services, founder, process, contact)
thank-you.html   Netlify form redirect target
netlify.toml     publish root + security headers
assets/          logo.webp       full lockup, background matted out (transparent)
                 logo-mark.webp  crowned CC only, for nav/footer/watermark
                 favicon.png     64x64 square
```

## The intro

First visit plays a ~4s moon-eclipse sequence: two champagne crescents drift in
from opposite edges, settle into the interlocked CC monogram, the crown drops
in, a shimmer sweeps across, then the wordmark and tagline open underneath.

- Skippable by click, Esc, or Space
- Plays once per browser session (`sessionStorage.cfcIntroSeen`)
- Fully disabled under `prefers-reduced-motion`

The mark is **her real logo**, not a redraw. The source only exists as a 198x176
tile with a navy background baked in (pulled from AMG's brokerage marquee), so
`assets/logo.webp` was made by estimating that background per row, subtracting it,
and keeping the gold as an alpha matte — then upscaled 4x. It is genuine but soft
above ~300px on screen. **Replace it with the original high-res file when available.**

The two crescent moons that sweep in ahead of the logo are still SVG, since a
raster mark cannot be split apart to animate.

## Before launch — placeholders to replace

| What | Where | Current value |
|---|---|---|
| **Headshot** | `assets/edlawit.jpg` | missing — shows a monogram placeholder panel |
| **High-res logo** | `assets/logo.webp` | recovered from a 198px tile — soft when large |
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
