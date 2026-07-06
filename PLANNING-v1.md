# [STUDIO] — Planning Doc

> Working name: **[STUDIO]** (placeholder — see Open Questions).
> A web building & management company whose own website is a self-demonstrating
> showroom of website "vibes." Every demo teaches by *doing the thing it describes*
> — and gives an honest verdict on whether the technique is actually worth it.

---

## 1. North Star: the self-demonstrating showroom

Two mechanics working together:

1. **Show, then name.** Each feature is executed in front of the visitor, then a
   caption names the technique. Huge text loads and says *"This is huge display
   type — the first thing you noticed, which is the point."* The page scrolls and
   says *"Feel that glide? Lenis smooth-scroll."*
2. **Then judge it.** Every feature carries an honest **verdict** —
   essential / situational / vanity — so the site doubles as candid advice, not a
   trend catalog. This candor is the brand: we tell clients when a feature works
   *against* them. Most agencies won't.

Why this wins as a business site: the demos **are** the portfolio. A prospect
doesn't read "we build beautiful sites" — they *feel* it, and they trust us
because we're the ones saying "that parallax is vanity, skip it."

---

## 2. Core architectural insight: it's the same engine, different dials

Most "vibes" are **not** different machines — they're the same primitives with the
settings changed. Luxury is the Brochure engine turned *down* (slow, sparse);
Brochure is it turned *up* (loud, dense). Playful vs. Brutalist vs. Web3 are the
same layout primitives wearing different **skins**.

Consequence: **we don't build 12 demos. We build ~4 demo engines**, each with a
control that morphs it across its sub-vibes. Less code, no duplicated utilities,
and the morph *itself* is a selling point ("watch the same code become an agency
site, then a luxury brand").

---

## 3. Site architecture (sitemap)

```
/                      Landing — company intro + rotating taste of the vibes
/vibes                 The Gallery — one card per category, with overview + verdict-teaser
/vibes/:slug           A demo engine (showpiece, product, store, statement, editorial)
/services              Build from scratch · Database management · Rebrand/refactor
/contact               Lead capture
```

Journey:
`Landing → "Browse the vibes" → Gallery → pick a category → Demo (morph the dial) → "Next" / "Get this for my brand"`

---

## 4. The Narration System (the throughline)

A consistent UI language reused across **every** demo. This is what makes the site
feel like one product and shows off design-system discipline.

- **Spec Tag (caption chip).** Consistent label beside each feature:
  `❯ FEATURE — Parallax · VERDICT: vanity` + one line of plain English.
- **The Verdict stamp.** Every feature is rated:
  - **Essential** — genuinely earns its place.
  - **Situational** — great in the right context, dead weight in the wrong one.
  - **Vanity** — designers love it; most users don't notice or dislike it.
  - **⚠ Manipulative** — converts but erodes trust (flag, don't celebrate).
- **The HUD / Spec Sheet.** Persistent corner panel per demo: category name, a
  live checklist ticking features off as you hit them, a demo progress bar.
- **"How it's done" expand.** Each spec tag can reveal the real tech (Lenis, GSAP
  ScrollTrigger, `clip-path`, IntersectionObserver). Quiet sales pitch: *we know
  this stack.*
- **Demo intro / outro.** Intro restates the category overview; outro says
  *"That's the [category] vibe"* + `Next →` / `Want this for your brand? →`.

---

## 5. The five categories

Each = one demo engine. Verdicts are examples of the house voice.

### 5.1 The Showpiece — motion-first brand
**Absorbs:** Brochure/Agency, Portfolio/Creative, Luxury/Fashion.
**Distinct mechanic:** a **loud ↔ quiet dial** — the same engine reads as a
maximalist agency site or a restrained luxury brand depending on the setting.
**Shared engine:** Lenis smooth scroll, scroll-reveal, parallax, kinetic type,
custom cursor, full-bleed imagery, clip-path masked reveals, marquee, horizontal
scroll; (portfolio adds hover-to-preview + shared-element transitions).
**Self-demo + verdicts:**
- Huge display type — *"20vw. You noticed it first."* — **Essential** (if you have one thing to say, say it big).
- Lenis smooth scroll — *"Feel the glide."* — **Situational** (premium on a showpiece, overhead on a store).
- Parallax — *"I move slower than the background = depth."* — **Vanity** (great in a demo, usually adds jank + scroll-weight).
- Scroll reveals — *"I waited until you got here."* — **Situational** (pacing tool; overused = slow).
- Kinetic type — *"letters. that. move."* — **Vanity**.
- Custom cursor — *"Yours got bigger, didn't it?"* — **Vanity** (designers love it, hurts usability/accessibility).
- The **dial** control — drag from LOUD → QUIET and watch it become luxury: *"Same code. Restraint is just the dial turned down."*

### 5.2 The Product Site — structure & conversion
**Absorbs:** SaaS/Tech, Corporate/Enterprise, Landing/Conversion.
**Distinct mechanic:** an **arrangement/skin swap** — trust (corporate), modern
(SaaS), or single-CTA (conversion) from the same components.
**Shared belt:** grid/bento, feature cards, animated stat counters, testimonial
carousel, logo cloud, pricing table + monthly/annual toggle, FAQ accordion,
sticky CTA bars, dark-mode toggle.
**Self-demo + verdicts:**
- Bento grid — *"Uneven boxes, one story."* — **Situational**.
- Mesh gradient — *"The SaaS sky."* — **Vanity** (looks 2024, dates fast).
- Stat counters — *"10,000+ just counted up."* — **Situational** (persuades B2B, meaningless on a bakery).
- Logo cloud — *"The 'trusted by' wall."* — **Situational** (only if the logos are real and impressive).
- Testimonial carousel — **Situational** (a static grid often converts better).
- Pricing toggle — *"Annual 'saves 20%.'"* — **Essential** (for anything sold by subscription).
- FAQ accordion — **Essential** (objection-handling, genuinely useful).
- Countdown timer — *"Ends in 02:59:59."* — **⚠ Manipulative** (converts; erodes trust if fake).
- Dark-mode toggle — **Situational** (devs expect it; noise for a restaurant).

### 5.3 The Storefront — commerce
**Absorbs:** E-commerce/Retail. Stands alone (only category with real commerce logic).
**Distinct mechanic:** actual cart/product state — the best candidate for a
**genuinely functional** demo.
**Shared belt:** product grid, image hover-swap, color/size swatches, cart drawer,
sale/new badges, star ratings, scarcity, filters/sort, trust badges.
**Self-demo + verdicts:**
- Product grid — **Essential**.
- Hover-swap (front → back) — **Essential** (real purchase-decision help).
- Cart drawer with count bump — **Essential** (beats a full-page cart redirect).
- Swatches — **Essential**.
- Star ratings — **Situational** (only with real reviews).
- Scarcity "only 2 left" — **⚠ Manipulative** (works; be honest or lose trust).
- Sale badge + strikethrough — **Situational** (fake "was" prices are a legal + trust risk).

### 5.4 The Statement — aesthetic personality
**Absorbs:** Playful/Startup, Brutalist, Web3/Futuristic, Retro/Y2K.
**Distinct mechanic:** a **skin-swap** that proves "vibe" is a *theming layer*, not
new machinery — same layout, radically different personality.
**Skins & signatures:**
- **Playful:** spring easing, morphing blobs, wobble-on-hover, confetti. Verdict on confetti: **Vanity** (delightful once, annoying twice).
- **Brutalist:** system/mono fonts, harsh borders, no radius, snap (no-easing) hovers, 1995-blue links. Verdict: **Situational** (memorable, alienates mainstream users).
- **Web3/Futuristic:** dark, aurora glow, Tron grid floor, glowing "Connect Wallet," particles, glitch text. Verdict: **Vanity** (glow ≠ trust).
- **Retro/Y2K:** CRT/dither effects, chrome gradient text, marquees, visitor counter. Verdict: **Vanity** (nostalgia has a short shelf life).
- The swap itself: *"Same skeleton. The 'vibe' is a stylesheet, not an engineering problem."*

### 5.5 The Editorial — content & reading
**Absorbs:** Magazine/Blog, Restaurant/Hospitality (content skin).
**Distinct mechanic:** a genuine **reading/content system**, not a motion showcase.
**Shared belt:** strong typographic scale, drop caps, pull quotes, reading-progress
bar, 65-char measure, bylines + read-time, tag chips, inline newsletter;
(restaurant skin adds food photography, dotted-leader menu, sticky reservation CTA).
**Self-demo + verdicts:**
- Reading-progress bar — **Situational** (nice on long-reads, silly on short pages).
- Drop cap — *"Very Condé Nast."* — **Vanity** (charming, purely decorative).
- Pull quote — **Situational** (breaks the wall of text; overused = choppy).
- 65-char measure — *"Comfortable to read."* — **Essential** (real readability, invisible done right).
- Inline newsletter — **Situational** (the obligatory interrupt; converts, mildly annoys).

---

## 6. The Gallery page (/vibes)

- One card per **category**. Each shows: name, one-line overview, the "distinct
  mechanic," and a hover that gives a *taste* (a micro-morph of the dial/skin).
- **Cards adopt their own vibe** — the showpiece card is cinematic, the brutalist
  skin peeks through the statement card, etc. The gallery is a sampler platter.
- Optional: filter by "energy level" or industry.

---

## 7. The Landing page (/) — built last, after the plan is locked

1. **Hero** — company name + promise ("We build the web in whatever voice your
   brand speaks"). Hero cycles a taste of several vibes.
2. **Services** — Build from scratch · Database management · Rebrand & refactor
   (import existing codebase, refresh brand/stack).
3. **The hook** — *"Not sure what you want it to feel like? Browse the vibes →"*
   (primary CTA into the gallery — the differentiator).
4. **Process · About · Contact.**

Meta-pitch baked into copy: *the site you're on is the portfolio — and we'll tell
you which of these features you actually need.*

---

## 8. Reusable feature library (build once, share everywhere)

Configurable primitives shared across engines: Lenis smooth scroll · scroll-reveal
(IntersectionObserver / GSAP ScrollTrigger) · parallax layer · marquee · custom
cursor · counter · carousel · accordion · countdown · cart drawer · theme/skin
toggle · the **dial** control · the **Spec Tag + Verdict + HUD** narration system.

---

## 9. Tech stack — DECIDED

**Framework: Astro.** Rationale: the site's weight is the animation libs + assets
(GSAP, Lenis, Three.js, fonts, imagery), *not* the framework. Astro is multi-page
and zero-JS by default, so the landing + gallery are near-instant and each heavy
demo's weight is isolated to its own route, loaded only when visited. React islands
only where a single demo earns it (e.g. `react-three-fiber` for the web3 3D).

- **Smooth scroll:** Lenis.
- **Animation:** GSAP + ScrollTrigger (vanilla-friendly, light per-demo).
- **3D (statement/web3, portfolio):** Three.js / react-three-fiber island or Spline.
- **Styling:** Tailwind or CSS modules (decide during setup).
- **Deploy:** Vercel / Netlify.
- **Discipline that actually matters:** code-split per demo, lazy-load heavy libs,
  no autoplaying everything, `prefers-reduced-motion` fallbacks on every demo.

---

## 10. Open questions / decisions

1. **Company name** — [STUDIO] is a placeholder. Real name drives logo/domain/tone.
2. **Launch scope** — recommend the ~4 core engines (Showpiece, Product, Storefront,
   Statement); Editorial optional 5th.
3. **Which demo(s) are genuinely functional?** — recommend making the Storefront
   cart and the contact form real to prove full-stack chops; rest are front-end illusions.
4. **Narration default** — captions/verdicts on by default, with a toggle to
   experience a vibe "clean"? (Recommended.)
5. **Verdict tone** — how blunt? ("Vanity" is punchy; confirm it's on-brand vs.
   softer language like "optional.")
6. **Landing hero** — live embedded vibe snippets vs. curated video/GIF.
