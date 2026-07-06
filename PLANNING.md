# [STUDIO] — Plan v2 (checkpoint: 2026-07-05)

> The original pre-build plan is preserved at `PLANNING-v1.md`. That plan is
> ~90% executed: **all five demo engines are live.** This document restarts the
> plan from where the project actually is, and carries the feature backlog for
> deepening each vibe.

---

## 1. Where we are

**Built and working:**

| Piece | Status |
| --- | --- |
| Design tokens, verdict palette, the `--dial` property | ✅ `src/styles/global.css` |
| Narration system: `SpecTag`, `Hud` (checklist + progress + collapse + auto-hide) | ✅ components |
| `/vibes/showpiece` — 9 features + loud↔quiet dial | ✅ |
| `/vibes/product` — 9 features + 3-way mode swap | ✅ |
| `/vibes/storefront` — 9 features + real cart state | ✅ |
| `/vibes/statement` — skin-swap skeleton + 4 skins | ✅ |
| `/vibes/editorial` — real reading system, 7 features | ✅ |
| `/vibes` gallery | ✅ (now vibe-dressed, see below) |
| `/` landing | ✅ shipped 2026-07-05 (see Phase 1) |
| `/services`, `/contact`, 404 | ✅ shipped 2026-07-05 (see Phase 2) |
| Company name | ✅ **Artifice UI** (was `[STUDIO]`) |

**Added at this checkpoint (2026-07-05):**

- **Gallery cards now wear their own vibe** (v1 §6 promise): showpiece card is
  dark/loud and goes quiet on hover, statement card is brutalist-framed with a
  4-skin strip and a wobble, editorial card has a real miniature drop cap, etc.
- **Verdict legend** on the gallery — the four-color language is taught before
  any demo uses it.
- **`NextVibe` guided tour**: every demo outro chains to the next demo
  (showpiece → product → storefront → statement → editorial → loop), so the
  site walks a prospect through the whole showroom.
- **Narration on/off toggle in the HUD** (v1 open question #4 → resolved:
  default ON, one click hides every spec tag to experience a vibe "clean").
- **Free-shipping meter narrated** — a SpecTag *inside the cart drawer*
  (verdict: situational, the honest nudge), and the HUD ticks it when the
  drawer opens.
- **Social-proof popups** added to Product (verdict: ⚠ manipulative). Inline
  specimen always cycles; a free-roaming corner toast only appears in
  Conversion mode.
- `README.md` created.

**North star (unchanged):** every feature *performs itself*, then gets an
honest verdict. The demos are the portfolio; the candor is the brand.

---

## 2. Phase 1 — The Landing Page (the storefront window)

> **✅ SHIPPED 2026-07-05.** Built as directed below, plus two additions:
> an anti-template section (three identical grey wireframes labelled
> YOUR LOGO / ALSO YOUR LOGO / STILL YOUR LOGO, with an honest "Templates:
> situational" verdict) and an **involvement dial** ("How much say do you
> want?" — Point us at it / Collaborate / Hands on the dials), with a
> "Pricing table: situational" SpecTag explaining why there's no pricing
> page yet. Positioning: anti-template, pro-decision. The outro owns the
> placeholder name: "[STUDIO] is a placeholder name. The work isn't."
> Contact CTA is a mailto placeholder until Phase 2's `/contact` ships.

Original direction (for the record):

1. **Hero = the vibes performing in miniature.** A headline like *"We build
   the web in whatever voice your brand speaks"* where the key word cycles
   through the five engines' typography/palette every few seconds (Anton-loud →
   corporate blue → boutique serif → brutalist mono → editorial italic). The
   site self-demonstrates from second zero — no video, no screenshots, just the
   real tokens.
2. **A SpecTag on the landing's own hero.** The narration system appears on
   page one, stamping our own hero animation (verdict: situational, "we took
   our own advice"). Instantly communicates the whole gimmick.
3. **Services strip** — Build from scratch · Database management · Rebrand &
   refactor. Three cards, plain language, each linking to `/services`.
4. **The hook** — *"Not sure what you want it to feel like? Browse the
   vibes →"* as the primary CTA, plus the five gallery cards (reuse the
   vibe-dressed cards, or a marquee of them).
5. **Meta-pitch outro** — *"The site you just used is the portfolio. And we'll
   tell you which of these features you actually need."* → `/contact`.

Estimated effort: **M** (one page, mostly composition of existing pieces).

## 3. Phase 2 — Trust & lead capture

> **✅ SHIPPED 2026-07-05.** All three pages live, plus shared `SiteHeader` /
> `SiteFooter` chrome (the demos and landing keep their own headers by design;
> these utility pages get consistent nav). The footer carries the "Artifice —
> clever, cunning trickery. We took the name so we'd always be the one to point
> it out." wink, turning the name's tension into the candor thesis.

- **`/services`** ✅ — three services (Build from scratch / Rebrand & refactor /
  Database management), each with a **"Draws on →"** card linking to the demo
  that proves it (Rebrand→Statement skin-swap, Database→Storefront real state,
  Build→gallery), plus an "Honest take" callout per service and the involvement
  recap. One SpecTag: "Discovery call = essential."
- **`/contact`** ✅ — the *genuinely functional* form. Fields mirror the site's
  thesis: **which vibe caught your eye** + **how much say do you want** (the
  involvement dial) alongside name/email/message. Real inline validation
  (blur + submit, aria-invalid, linked error text, focus-first-error). Submit
  builds a **prefilled mailto** to johnathanmoore9066@gmail.com and shows an
  inline confirmation — no backend, and candid about it via two SpecTags
  (inline validation = essential; form-vs-mailto = situational). Swapping to a
  serverless action later won't change the UI. See open decision #2.
- **404** ✅ — `src/pages/404.astro`, self-demo ("a dead end has your whole
  attention — which is exactly why it shouldn't waste it"), two recovery doors,
  SpecTag "The 404 page = situational." Build emits `/404.html`.

Also this pass: retired the `[STUDIO]` placeholder → **Artifice UI** site-wide
(kept the `[ARTIFICE UI]` bracket wordmark treatment); landing outro CTA now
points at the real `/contact`; landing services section links to `/services`.

## 4. Phase 3 — Deepen the demos (the feature backlog)

New examples per vibe, each pre-assigned its house verdict. Rule of thumb kept
from v1: every engine should demo at least one ⚠ manipulative pattern — naming
dark patterns is the differentiator. (S/M/L = effort.)

> **BATCH 1 SHIPPED 2026-07-05** — the three brand-defining ⚠ manipulative
> demos, all verified in browser + clean 10-page build:
> - **Showpiece · Preloader** — fake 0→100 counter over an already-loaded page;
>   at 100 the label flips to "…nothing was actually loading." Hidden without JS
>   (`html.has-js` gate), skipped under reduced-motion, `.sr`-safe (aria-hidden),
>   replay button in a confession section. Showpiece now **10** features.
> - **Product · Exit-intent popup** — fires once on cursor leaving the top edge
>   (mouseout, clientY≤0, null relatedTarget) + a manual trigger for touch; focus
>   trap-safe (focuses the real button, Escape closes, inert/scroll-lock).
>   Product now **10** features.
> - **Editorial · Metered paywall** — lower paragraphs clipped by a CSS mask with
>   a gradient gate card; progressive-enhancement (words always in the page, JS
>   adds the wall, "unlock" lifts it). Editorial now **8** features.
>
> **BATCH 2 SHIPPED 2026-07-05** — vanity delights: Showpiece **film grain**
> (toggleable noise overlay), Statement **3D tilt** cards + **Konami code**
> confetti storm, Storefront **wishlist** heart (persistent, header count).
>
> **BATCH 3 SHIPPED 2026-07-05** — useful patterns, to balance the vanity/
> manipulative weighting: Product **sticky CTA bar** (mode-aware, pushier in
> Conversion) + **comparison table** (situational, "we win every row"),
> Storefront **recently-viewed** row (sessionStorage), Editorial **read-next**
> cards (essential). Feature counts now: Showpiece 11, Product 12, Storefront 11,
> Statement 7, Editorial 9.
>
> NEXT in Phase 3 (remaining backlog): Showpiece text-scramble / scroll-snap /
> hover-preview / View Transitions; Product dark-mode toggle / live-chat bubble;
> Storefront cross-sell / quick-view / size-guide / search; Statement cursor-trail
> / view-source / sound; Editorial sticky-ToC / sidenotes / reading-prefs.

### Showpiece
| Feature | Verdict | Effort | Self-demo angle |
| --- | --- | --- | --- |
| ✅ Preloader / load intro | ⚠ manipulative | S | **DONE.** A percentage counter that admits "nothing was loading — we made you wait to build anticipation." The most honest preloader on the internet. |
| Film-grain / noise overlay | vanity | S | Toggleable grain layer: "feel that 'expensive analog' texture? It's an 8KB PNG on loop." |
| Hover-to-preview portfolio rows | situational | M | Was in v1's portfolio belt, never built: a project list where hovering floats a preview image at the cursor. |
| Text scramble / decode-in | vanity | S | Heading scrambles into legibility: "cool once, unreadable twice." |
| Scroll-snap chapters | situational | S | A snapping sub-section that names the tradeoff: "the page just took control of your wheel." |
| View Transitions between pages | situational | M | Astro's view transitions on the vibes nav — shared-element morph from gallery card to demo hero. |

### Product Site
| Feature | Verdict | Effort | Self-demo angle |
| --- | --- | --- | --- |
| ✅ Sticky CTA bar | situational | S | **DONE.** v1 belt, never built. Appears after the hero scrolls away; in Conversion mode it should be pushier (that's the demo). |
| Dark-mode toggle | situational | S | The SaaS skin *is* dark mode — make the point explicit with a spec tag on the mode switch itself. |
| ✅ Comparison table ("us vs. them") | situational | S | **DONE.** Greyed-out competitor column: "notice whose checkmarks are bigger. Ours. Always ours." |
| ✅ Exit-intent modal | ⚠ manipulative | S | **DONE.** Fires once when the pointer leaves the top of the viewport: "WAIT — see how that felt?" |
| Live-chat bubble | situational | S | A fake chat bubble that answers honestly: "there's no one here. There's usually no one anywhere." |

### Storefront
| Feature | Verdict | Effort | Self-demo angle |
| --- | --- | --- | --- |
| Cross-sell in cart ("pairs well with") | situational | M | Real add-on row in the drawer driven by the actual cart contents. |
| Quick-view modal | situational | M | Peek a product without leaving the grid. |
| ✅ Recently-viewed row | situational | S | **DONE.** Genuinely stateful (sessionStorage) — fits the "this one actually works" brand. |
| Wishlist heart | vanity→situational | S | Hearts that persist; verdict depends on whether anyone ever returns to them. |
| Size guide / fit note | essential (apparel) | S | "The cheapest returns-reduction feature that exists." |
| Search with suggestions | essential at scale | M | Six products make it demonstrably silly — which is itself the verdict lesson. |

### Statement
| Feature | Verdict | Effort | Self-demo angle |
| --- | --- | --- | --- |
| Retro cursor trail | vanity | S | Y2K skin only, sparkles behind the pointer; pointer:fine + reduced-motion gated. |
| Konami-code easter egg | vanity (delight) | S | Playful skin: ↑↑↓↓←→←→BA → confetti storm + a spec tag that admits what just happened. |
| 3D tilt cards | vanity | S | Web3 skin: perspective tilt-on-hover — "depth is the costume, not the feature." |
| "View source" plaque | charm | S | Brutalist skin: a visible link to the page's own source. Peak brutalism. |
| Sound-on toggle | situational | M | Only if a real sound design idea shows up; skip otherwise. |

### Editorial
| Feature | Verdict | Effort | Self-demo angle |
| --- | --- | --- | --- |
| Sticky table of contents | situational | M | Highlights the current section; "essential on docs, furniture on essays." |
| Sidenotes / footnotes | situational | M | Tufte-style margin notes that collapse inline on mobile.¹ (¹Like this.) |
| ✅ "Read next" cards | essential (for publications) | S | **DONE.** The pattern `NextVibe` already uses — name it and stamp it. |
| ✅ Metered paywall demo | ⚠ manipulative | M | **DONE.** Blur-the-rest overlay with honest copy: "the content didn't move; a business decision is standing on it." Editorial's missing manipulative example. |
| Reading preferences (size / theme) | situational | M | Font-size stepper + sepia/dark; persists. |

## 5. Phase 4 — Cohesion & polish

> **✅ MOSTLY SHIPPED 2026-07-05.** Big-ticket a11y + perf done and verified in
> browser + clean 10-page build. Remaining items (OG images, sitemap) are tied
> to the domain/name decisions and belong in Phase 5.

- **A11y pass** ✅ — global `:focus-visible` ring (`--focus: #c8492f`, warm,
  visible on every palette; keyboard-only so it never nags mouse users); `inert`
  on the storefront cart drawer and editorial reserve-bar when hidden (verified:
  closed = focus refused, open = focus works, toggles with aria-hidden);
  heading-order audit across all 10 routes → fixed the three offenders
  (statement `.sig-h` h3→p; showpiece duplicate hero h1→span; storefront grid
  got an `.sr-only` "Products" h2). Added a reusable `.sr-only` utility.
- **Performance pass** ✅ (main win) — **self-hosted the four fonts via
  Fontsource** (`@fontsource/{anton,fraunces,inter,jetbrains-mono}`, imported in
  BaseLayout, minimal weights, lazy by unicode-range). Removed the Google Fonts
  `<link>` + preconnects entirely — build has **zero** `fonts.googleapis` /
  `fonts.gstatic` references; 44 woff2 emitted, only `latin` subset fetched at
  runtime. Demo JS already route-isolated (Astro per-page `<script>`). Lighthouse
  per route = still TODO (needs a run; no blocker expected).
- **Reduced-motion audit** ✅ — already solid: global.css nukes all CSS
  animation/transition under `prefers-reduced-motion`, every demo's JS motion is
  guarded, landing voice-cycle guarded. No unguarded motion introduced by the
  new pages (only hover transitions, which the global rule also covers).
- **Meta / favicon** ✅ — `public/favicon.svg` (the `[ • ]` bracket wordmark:
  dark tile, paper brackets, accent-orange dot); BaseLayout now emits favicon +
  `theme-color` + Open Graph + Twitter card tags; per-page `description`s added
  to all five demos and the gallery.
- **Remaining (→ Phase 5, domain-gated):** per-vibe **OG images** (each card
  wears its vibe — needs an image-gen step, e.g. Satori/`astro-og-canvas`);
  **sitemap** (`@astrojs/sitemap`, needs the real `site` URL); a real
  **Lighthouse** run and **Safari / real-device** pass (can't run in this env).

## 6. Phase 5 — Ship

1. **Name the studio** (blocks logo, domain, OG images, copy voice — the last
   big open decision from v1).
2. Domain + deploy (Vercel or Netlify — static output, no server needed until
   the contact form picks a backend).
3. Privacy-friendly analytics (Plausible/Fathom — on-brand: no cookie banner
   needed, and *that* can be a spec tag in the footer).
4. Soft-launch checklist: all five demos on a real phone, Safari pass
   (backdrop-filter, `color-mix`, `initial-letter` fallbacks already in place).

## 7. Working order

1. ~~Landing page (Phase 1)~~ ✅ done.
2. ~~Contact + services + 404 (Phase 2)~~ ✅ done. The site is now *sellable*.
3. ~~Polish — a11y + perf + meta (Phase 4)~~ ✅ done (bar domain-gated items).
4. Backlog features (Phase 3) — in this order: the cheap manipulative ones
   first (exit-intent, preloader, paywall — they're the brand), then S-effort
   delights, then M-effort systems.
5. Ship (Phase 5) — name is decided; remaining blockers are domain + the
   domain-gated polish (OG images, sitemap, Lighthouse, real-device pass).

**NEXT UP:** Back to Phase 3 (per-vibe backlog, §4) per the user's plan — start
with the cheap ⚠ manipulative examples (exit-intent, honest preloader, paywall).

## 8. Open decisions

1. ~~**Company name**~~ ✅ RESOLVED — **Artifice UI** (set in README by the
   user, propagated site-wide). Bracket wordmark `[ARTIFICE UI]` kept as the
   logotype. Note the deliberate tension: "artifice" = trickery, which the
   footer/landing flip into the candor thesis ("we took the name so we'd always
   be the one to point it out"). Easy to swap if the user wants a different
   direction — one find/replace.
2. **Contact form backend** — currently **mailto** (zero-cost, honest, works
   today). Upgrade path when volume justifies it: Astro Action + serverless
   function (Vercel/Netlify) or a form service (Formspree). The UI won't change.
3. **Verdict tone** — v1 asked "how blunt?"; the shipped voice is blunt-but-warm
   and it works. Confirmed unless client feedback says otherwise.
4. **3D (react-three-fiber) for Web3 skin** — the CSS Tron grid + particles
   already sell it; only add a real 3D island if a client-facing need appears.
   Default: skip.
5. **Editorial imagery** — the reading demo is text-only by design; decide
   whether the restaurant skin eventually earns real photography.
