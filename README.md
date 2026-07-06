# [ARTIFICE UI] — the self-demonstrating showroom

The company site for a web building & management studio, built to be its own
portfolio: a showroom of website **"vibes"** where every demo teaches by *doing
the thing it describes* — huge text loads and tells you it's huge text — and
every feature is stamped with an honest **verdict**:

- **Essential** — earns its place
- **Situational** — right context only
- **Vanity** — looks great, does little
- **⚠ Manipulative** — converts, costs trust

The candor is the brand: we tell clients which features work *against* them.

## The five demo engines

| Route | Engine | Distinct mechanic |
| --- | --- | --- |
| `/vibes/showpiece` | The Showpiece | loud ↔ quiet **dial** (agency ↔ luxury from one engine) |
| `/vibes/product` | The Product Site | Corporate / SaaS / Conversion **arrangement swap** |
| `/vibes/storefront` | The Storefront | a **real working cart** (variants, qty, subtotal, drawer) |
| `/vibes/statement` | The Statement | Playful / Brutalist / Web3 / Y2K **skin-swap** — vibe is a stylesheet |
| `/vibes/editorial` | The Editorial | a genuine **reading system** (the demo is the article) |

Shared narration UI: `SpecTag` (verdict chip + "how it's done"), `Hud` (live
feature checklist, progress bar, narration on/off toggle), `NextVibe` (the
demo-to-demo guided tour).

## Stack

[Astro](https://astro.build) (zero-JS by default; each demo's weight is isolated
to its own route) + GSAP/ScrollTrigger + Lenis (Showpiece only — smooth scroll
is "overhead" elsewhere, per our own verdict). No UI framework; every demo is
vanilla TS in an Astro `<script>`. All motion is gated behind
`prefers-reduced-motion`.

## Develop

```sh
npm install
npm run dev      # http://localhost:4321
npm run build    # static build to dist/
```

## Plan

Current roadmap: [PLANNING.md](PLANNING.md). Original pre-build plan preserved
at [PLANNING-v1.md](PLANNING-v1.md).
