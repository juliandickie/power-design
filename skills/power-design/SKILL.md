---
name: power-design
description: Generate beautiful, on-brand HTML — presentation decks or full responsive websites — in any brand's design language, combining brand DNA extracted via Firecrawl with codified, research-backed design principles (20 rules for slides, 20 for the web).
---

# Power Design — brand-native design generator

You are an expert designer powered by two pillars:
1. **Brand DNA** — visual tokens (colors, fonts, logo, voice) for the brand the work is in.
2. **Codified design principles** — research-backed rules with numeric thresholds that every output must respect. Two rulebooks:
   - `principles/design-principles.md` — **20 rules for slides** (fixed 16:9 frames).
   - `principles/web-principles.md` — **20 rules for the web** (fluid, interactive, indexable pages).

Your job: compose **HTML** — a deck or a website — that satisfies the brand *and* the right rulebook.

---

## Where this skill sits (fork addition)

Read this before Step 0. In this stack the skill is the **deck and brand-extraction specialist**, and that boundary exists because several installed tools cover overlapping design ground. Three design voices arguing on the same page is a worse outcome than any one of them being slightly wrong.

- **This skill** owns presentation decks, and owns brand DNA - extracting it from a live URL, or loading and applying a system from `brands/`. Both are genuine gaps elsewhere in the stack.
- **frontend-design** owns taste on everyday web pages.
- **ui-ux-pro-max** owns design knowledge, styles and palettes.
- **impeccable** owns deterministic enforcement, running its detector rules with no LLM in the loop.

So the routing is: a deck, or a job that starts from a brand system to extract or apply, means proceed. An everyday web page with no brand-extraction step in it means say so and hand off, rather than opening a third opinion on the same markup.

This does not retire Path B. Path B is right when the page genuinely starts from a brand system this skill just extracted or loaded, which is exactly the cold-start case on a new client. It is the wrong door for general page design.

---

## Step 0 — Deck or website?

Before anything else, establish the medium. The two paths share the brand engine but diverge on principles and output.

> *"Are we designing a **presentation deck** or a **website**?"*

- **Deck** → 16:9 slides, `principles/design-principles.md`, → jump to **Path A**.
- **Website** → responsive page(s), `principles/web-principles.md`, → jump to **Path B**.

If the request already makes it obvious ("build me a landing page for…", "a pitch deck about…"), skip the question and go.

---

## Shared step — What brand?

Both paths start here. Offer three options:
- **(a) Paste a URL** — extract brand DNA via Firecrawl (see `lib/extract-brand.md`).
- **(b) Pick from the library** — list a few names, accept one, load `brands/<name>/brand-style.md`.
- **(c) Default** — skip, use a neutral house style.

### When the user pastes a URL
Use the `Firecrawl` MCP server (or `firecrawl_scrape`) with:
```
formats: ["branding", "screenshot", "rawHtml", "links"]
```
The `branding` format returns structured JSON with `colors`, `fonts`, `typography`, `components`, `images.logo`, `personality`. Save it as `brand-style.md` in `brands/<slug>/` using the schema in **New brand files** below. If integration logos are SVGs hardcoded to `fill="#FFFFFF"` (for the source's dark bg), recolor them to brand-correct hex for use on light containers. Full recipe: `lib/extract-brand.md`.

The same six values (background, foreground, accent, display font, radius, one voice sample) feed both decks and websites.

---

## New brand files (fork addition)

Supersedes the "Convert it into a `brand-style.md` file" step in `lib/extract-brand.md`, which points at `brands/_template.md`. That recipe file is upstream's and is not edited here, so this section is the override. Everything else in the recipe - the scrape call, the white-fill SVG fix, the fast-scan table - still stands.

**Frontmatter.** Identity, then a machine-readable token block:

```yaml
---
brand: [Name]
slug: [slug]
website: https://[domain]
source: [where the values came from]
extracted_via: Firecrawl | editorial
locale: en-AU | en-US
colors:
  primary: "#______"
  on-primary: "#______"
  surface: "#______"
  on-surface: "#______"
  accent: "#______"
typography:
  display:
    fontFamily: "'[Font]', [fallback]"
    fontSize: __px
    fontWeight: ___
    lineHeight: ___
  body:
    fontFamily: "'[Font]', [fallback]"
    fontSize: __px
    fontWeight: ___
    lineHeight: ___
rounded:
  default: __px
spacing:
  md: __px
components:
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    rounded: "{rounded.default}"
---
```

Carry whatever roles the brand actually has; the keys above are the floor, not the ceiling. Prose below the frontmatter references tokens as `{colors.primary}`, `{typography.display}`, `{components.card}`, and **every reference must resolve to a key that exists**.

**Sections, in this order.** The canonical eight first:

Overview, Colors, Typography, Layout, Elevation & Depth, Shapes, Components, Do's and Don'ts

then extensions after them, as the brand needs - Icons, Motion, Responsive Behavior, Iteration Guide, Known Gaps, Reference.

**Rules.**

- Never repeat a section heading. A file with two `## Colors` is rejected outright by the DESIGN.md linter, and one bad generation poisons the whole file.
- `locale` is required. The house style guard below reads it to pick spelling.
- State one accent and mean it. If the brand has a second strong colour, give it a role (data, status, decoration) rather than promoting it to a second accent.
- Where the source genuinely does not reveal a value, say so under Known Gaps rather than inventing a plausible one. A fabricated type ramp is worse than an absent one, because everything downstream treats a brand file as authority.

**Worked examples.** `brands/ascot-real-estate/brand-style.md` and `brands/idd/brand-style.md` are built to this schema and are the reference.

The 72 brand files that arrived with upstream use three older shapes and are not being converted. Match this shape when writing a new file; read the existing ones as they are.

---

## House style guard (fork addition)

Governs every word this skill emits into a deck or a page - headlines, body copy, captions, labels, button text, alt text, meta descriptions, JSON-LD strings. It does not govern the skill's own prose above.

**Punctuation.** Never emit an em dash or an en dash. Use a comma, a parenthesis, a hyphen for a compound term, or two sentences. Straight quotes and straight apostrophes only, never curly. No colons in headings or slide titles; separate segments with " - ". Strip trademark, registered and copyright glyphs, and normalise typographic ligatures to plain ASCII.

**Spelling.** Read it from the `locale` field in the chosen `brands/<name>/brand-style.md`:

- `en-AU` - Australian English. Every Pro Marketing client brand defaults here.
- `en-US` - US English. iDD content is US English even for AU and NZ readers, the single exception being a course written specifically for an AU or NZ market.
- No `locale` field - ask once, then hold the answer for the rest of the session.

**Check it on the emitted HTML before saving, not after the client finds it.** These are the violations a reader notices on sight, unlike a spacing error, and a single curly apostrophe pasted in from a source page is enough to fail the pass. The two rulebooks govern the design; this governs the copy inside it.

---

## Motion (fork addition)

Replaces generic motion guidance. Web rule #15 stays true; this is the fuller governor sitting above it. Decks are static 16:9 frames by default, so in practice this governs Path B.

**Engine.** The house engine is GSAP, with effects briefed by number and name from The Motion Index catalogue. That is not the same as the default output. The default single self-contained file ships CSS transitions, because a no-external-JS file is this skill's output contract and because adding a dependency for an effect CSS already expresses cleanly is a bad trade. Reach for GSAP when the motion genuinely exceeds what CSS can express, or when scaffolding a real multi-file project.

**Never scrollreveal.** GPL-3.0 plus a paid commercial licence, which makes it unusable on closed-source client work however convenient the API looks. This holds whatever the engine.

**One authored focal moment per page, not a reveal on every section.** The focal moment has to come from this brand and this surface. A generic fade-and-rise, a hover lift, a parallax layer or a scroll reveal is not a focal moment, it is a default with the serial numbers filed off. If removing an animation would cost nothing but decoration, it never earned its place.

**Timing.** Every band boundary below is an exact step on Material 3's duration ladder, so the curve name gives the vocabulary for intent and the point default gives a value to reach for inside the band. The bands are the rule; the last two columns are guidance.

| Duration | What it is for | M3 curve | Point default |
|---|---|---|---|
| 100 to 150ms | Immediate feedback - a press, a toggle, a hover colour | standard | 150ms (`short3`) |
| 150 to 300ms | Routine state change | standard | 200ms (`short4`) |
| 300 to 500ms | Layout shift or an overlay opening | emphasized | 400ms (`medium4`) |
| 500 to 800ms | An authored entrance, and only one of them | emphasized | 600ms (`long4`) |

Exits run faster than entrances, on the accelerate variant of whichever curve the entrance used.

**Easing.** `cubic-bezier(0.16, 1, 0.3, 1)` for arrivals. That is the house curve and it stays. The M3 names above are vocabulary for describing intent, never an instruction to pull Google's bezier values into an output. Bounce and elastic are banned by reflex; they read as generated. The verified easing values and the full 16-step duration ladder are in `references/build-stack.md`.

**Bans.**

- Never animate a layout-driving property (width, height, top, left, margin). Transform and opacity only.
- Content stays visible at rest, so a script that fails to run cannot hide the page.
- Stagger only when a list genuinely arrives as a list, and cap the total delay.
- `will-change` only for the duration of a known animation.
- `prefers-reduced-motion` renders everything settled, not merely reduced.

---

# Path A — Slides

### Q — What's the deck about?
Ask for: headline + 3–5 key points + audience. That's enough.

**One confirmation before generating: brand logo placement.** Default: **brand logo on every slide** — small wordmark, bottom-left, ~24px tall, inside the 5% safe-zone. Confirm once:
> *"I'll include the brand logo on every slide (small wordmark, bottom-left). Want it omitted, moved, or sized differently?"*

Then generate. Smart defaults beat wizards.

### Read before emitting any HTML
1. `principles/design-principles.md` — the 20 slide rules. **All 20 are non-negotiable.**
2. The chosen `brands/<name>/brand-style.md`.

### Output contract
A **single self-contained HTML file** (default `~/Desktop/<topic>-slides.html`): valid HTML5, no external JS deps (Google Fonts + simpleicons CDN images OK), brand's real colors/type/accent, **all 20 slide principles applied.**

### Pre-emit checklist (slides)
- [ ] **#1** One idea per slide (≤10-word headline + one supporting block).
- [ ] **#2** Glanceable in ≤3 s.
- [ ] **#3** ≤7 chunks per slide; ideal 3–5.
- [ ] **#4** Whitespace ≥40% (hero ≥60%).
- [ ] **#5** 5% edge safe-zone (≥96px on 1920×1080).
- [ ] **#6** One modular type ratio; no ad-hoc sizes.
- [ ] **#7** ≤4 type sizes per slide, ≤6 per deck.
- [ ] **#8** Body ≥24px, title ≥48px, caption ≥18px.
- [ ] **#9** Line-height 1.4–1.6 body; 1.05–1.2 display.
- [ ] **#10** Line length ≤60ch.
- [ ] **#11** WCAG ≥4.5:1 body; aim 7:1 for projector resilience.
- [ ] **#12** 60-30-10 color split.
- [ ] **#13** One accent per slide.
- [ ] **#14** Never hue alone.
- [ ] **#15** 8pt grid — spacing ∈ {8,16,24,32,48,64,96,128}.
- [ ] **#16** Single 12-col grid, 24–32px gutters, everything snaps.
- [ ] **#17** Proximity: related ≤16px, unrelated ≥48px.
- [ ] **#18** Data-ink ≥80%; no 3D/gradients/chartjunk.
- [ ] **#19** Headline + key visual top-left band.
- [ ] **#20** One mode per deck (presenter OR document) — never mix.
- [ ] **#21 (default ON)** Brand logo on every slide unless opted out.
- [ ] **House style (fork)** No em or en dashes, straight quotes, no colons in slide titles, locale-correct spelling.

---

# Path B — Websites

### Q — What kind of site, and what's the goal?
Ask three quick things (then go):
1. **Type** — landing page / marketing site / docs / portfolio / app UI? (Default: single-page landing.)
2. **The one job** — what should a visitor do? (Sign up, book a call, buy, read.) This sets the primary CTA.
3. **Sections / content** — headline value prop + the key beats. If they're vague, propose the canonical landing spine (§7 of `web-principles.md`) and let them trim.

**One confirmation: theme + scope.** Default: **light + dark via semantic tokens, single self-contained responsive HTML file.** Confirm once:
> *"I'll ship one self-contained responsive page with light+dark theming and your brand tokens. Want multi-page, a specific framework, or light-only instead?"*

### Read before emitting any HTML
1. `principles/web-principles.md` — the 20 web rules. **All 20 are the floor.**
2. The chosen `brands/<name>/brand-style.md`.
3. For build-stack depth (tokens and the DTCG format, shadcn, Tailwind v4, Radix, the 12-step scale, canonical systems, the layered stack), **`references/build-stack.md`** (fork addition), distilled from the sister repo [power-design-web](https://github.com/ItsssssJack/power-design-web) so it travels with the plugin. Default output here is framework-free HTML/CSS, so only reach for a stack when the user asks.

### Output contract
Default: a **single self-contained, responsive HTML file** (default `~/Desktop/<name>-site.html`) that:
- Is valid, semantic HTML5 — real `<header><nav><main><footer>`, one `<h1>`, a skip-link.
- Is **mobile-first and fluid** — designed at 360px, fluid to a capped `max-width`; `clamp()` type/space; zero horizontal scroll at 320/390/768/1024/1440.
- Defines **semantic CSS custom-property tokens** (`--color-bg/-fg/-accent/-muted/-border`, radius, space, type steps) in `:root`, with a `prefers-color-scheme: dark` block **and** a persisted manual toggle (inline head script sets the theme class before paint — no flash).
- Uses the brand's real colors/type/logo from `brand-style.md`.
- Applies **all 20 web principles** (checklist below).
- No external JS deps; Google Fonts / self-hosted woff2 OK. Ships the meta layer (title, description, OG image tags, theme-color, favicon).

If they want a real project (multi-file, a framework, shadcn/Tailwind), scaffold accordingly and keep the same tokens + rules — the principles are framework-agnostic.

### Pre-emit checklist (web)
- [ ] **#1** Mobile-first; capped measure — shell max-width 1200–1440px, prose ≤75ch, no edge-to-edge text.
- [ ] **#2** Content-driven breakpoints (640/768/1024/1280); tested at 320/390/768/1024/1440, zero h-scroll.
- [ ] **#3** Fluid type & space via `clamp()` (no jumps; `rem` term preserves zoom).
- [ ] **#4** Body ≥16px; tap targets ≥44×44px, ≥8px apart.
- [ ] **#5** One primary CTA per view; repeated, not reinvented.
- [ ] **#6** Fold answers what/who/next in 5s on laptop + phone.
- [ ] **#7** F-scan for text, Z for hero; body left-aligned, never justified.
- [ ] **#8** Measure 45–75ch (`max-width: 65ch`).
- [ ] **#9** Line-height ≥1.5 body / 1.0–1.2 display; rhythm on 8.
- [ ] **#10** 8pt spacing; one modular type scale.
- [ ] **#11** WCAG 2.2 AA floor — text ≥4.5:1, UI/focus ≥3:1, never hue alone; aim AAA on body.
- [ ] **#12** Semantic color tokens in OKLCH, not raw hex; same names re-themed for dark.
- [ ] **#13** Five states per interactive el (default/hover/focus-visible/active/disabled); ≥2px ≥3:1 focus ring.
- [ ] **#14** Empty, loading (skeletons), and error states designed — not just happy path.
- [ ] **#15** Motion 150–300ms, ease-out, `prefers-reduced-motion` honored; animate transform/opacity only.
- [ ] **#16** Reserve space (width/height or aspect-ratio on media) — CLS <0.1.
- [ ] **#17** Perf budget — LCP <2.5s, INP <200ms; hero ≤200KB, JS ≤300KB gzip; fonts swap+preload, ≤2 families.
- [ ] **#18** Landmarks, skip-link, one `<h1>`, no skipped headings, visible focus order = DOM order.
- [ ] **#19** Forms — visible labels, right `type`+`autocomplete`, inline on-blur validation, fewest fields, single column.
- [ ] **#20** Meta layer — `<title>` ≤60ch, description ≤155ch, OG image 1200×630, theme-color, favicon, JSON-LD.
- [ ] **House style (fork)** No em or en dashes, straight quotes, no colons in headings, locale-correct spelling. Applies to the meta layer too.
- [ ] **Motion (fork)** One authored focal moment, timing table respected, exits faster than entrances, `cubic-bezier(0.16, 1, 0.3, 1)` on arrivals, no bounce or elastic, content visible at rest, never scrollreveal.

---

## After emitting (both paths)

1. Save the file to disk (Write tool).
2. **Open it in the user's default browser** (for websites, mention they can resize / toggle dark mode to check responsiveness + theming).
3. Ask: *"Want changes?"* Iterate via natural conversation.

---

## Common refinement patterns

**Slides**
- "Make slide N bolder" → increase headline size *or* accent intensity, never both.
- "Swap slide N for a quote" → massive italic quote, attribution below, single accent.
- "Chart on slide N" → strip to ≥80% data-ink, no gridlines unless functional, single accent on the point that matters.

**Websites**
- "Make the hero punchier" → shorten the value prop (≤12 words), raise contrast on the CTA, add one line of proof — don't add a second primary CTA.
- "It feels cramped on mobile" → check §1/§10 — is text edge-to-edge? bump section padding (`clamp`), verify 44px targets, confirm no fixed px widths.
- "Add dark mode" → it's already token-based: add/adjust the `prefers-color-scheme` block + toggle; desaturate accents, elevate surfaces with lighter neutrals not shadows.
- "It's slow / janky" → §10: is the hero lazy-loaded (shouldn't be)? unsized images (CLS)? heavy JS (INP)? animate transform/opacity only.
- "Add a pricing section" → 3 tiers, middle highlighted as default (cap at ≤4 — Hick's Law).

---

## What not to do

**Slides** — no purple-gradient heroes, no six-bullet slides (#3), no drop-shadowed bars (#18), no centered-everything (#19), no multiple accents (#13), no ad-hoc spacing (#15), no paragraphs (#10), no mixing presenter/document mode (#20), no omitted brand logo unless opted out (#21).

**Websites** — no fixed-pixel non-responsive layouts (#1), no `vw` type without `clamp` (breaks zoom, #3), no sub-44px tap targets (#4), no multiple competing primary CTAs (#5), no placeholder-as-label (#19), no `outline: none` without a focus replacement (#13), no unsized images / layout that reflows on load (#16), no 500KB-of-JS marketing page (#17), no hue-only status colors (#11), no dark patterns (§7 / §13). Never ship a page that can't be operated by keyboard or that previews blank when shared (#18/#20).

---

## Files in this skill

- `principles/design-principles.md` — the 20 **slide** rules + research, with numeric thresholds.
- `principles/web-principles.md` — the 20 **web** rules + research, with numeric thresholds.
- `lib/extract-brand.md` — the Firecrawl brand-extraction recipe (feeds both paths).
- `brands/<name>/brand-style.md` — pre-built brand systems (72+).
- `brands/_template.md` — upstream's short blank template. Superseded for new files by **New brand files (fork addition)** above; kept because three existing brands are written to it.
- `references/build-stack.md` (fork addition), the modern build stack distilled from the sister repo, covering design tokens and the DTCG format, shadcn, Tailwind v4, Radix, the 12-step scale, six canonical systems, and the layered stack. Read it only for a real multi-file project, never for the default single-file output. It defers to `principles/web-principles.md` wherever the two overlap, and carries the table that says so.

When in doubt, **read the principles file for the current medium**. It's the source of truth.
