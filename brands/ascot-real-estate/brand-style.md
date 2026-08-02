---
brand: Ascot Real Estate
slug: ascot-real-estate
website: https://ascot.net.au
source: Pro Marketing client design system (clients/ascot-re-2026/site/DESIGN.md)
extracted_via: editorial - ported from the production DESIGN.md of record
locale: en-AU
colors:
  primary: "#9E1B2E"
  on-primary: "#FFFFFF"
  primary-container: "#F3DDE0"
  on-primary-container: "#7C1526"
  secondary: "#1B1A17"
  on-secondary: "#F3EFE8"
  tertiary: "#E3DCCF"
  on-tertiary: "#211F1B"
  surface: "#F7F4EF"
  on-surface: "#211F1B"
  surface-variant: "#ECE7DF"
  on-surface-variant: "#6B6459"
  outline: "#6E6658"
  outline-variant: "#DAD4C8"
  error: "#BA1A1A"
  on-error: "#FFFFFF"
typography:
  display:
    fontFamily: "'Newsreader', Georgia, serif"
    fontSize: 60px
    fontWeight: 400
    lineHeight: 1.08
    letterSpacing: "-0.01em"
  headline-lg:
    fontFamily: "'Newsreader', Georgia, serif"
    fontSize: 40px
    fontWeight: 400
    lineHeight: 1.15
    letterSpacing: "-0.01em"
  headline-md:
    fontFamily: "'Newsreader', Georgia, serif"
    fontSize: 30px
    fontWeight: 400
    lineHeight: 1.2
  title-lg:
    fontFamily: "'Rubik', system-ui, sans-serif"
    fontSize: 21px
    fontWeight: 600
    lineHeight: 1.3
  title-md:
    fontFamily: "'Rubik', system-ui, sans-serif"
    fontSize: 17px
    fontWeight: 600
    lineHeight: 1.4
  body-lg:
    fontFamily: "'Rubik', system-ui, sans-serif"
    fontSize: 18px
    fontWeight: 300
    lineHeight: 1.65
  body-md:
    fontFamily: "'Rubik', system-ui, sans-serif"
    fontSize: 16px
    fontWeight: 300
    lineHeight: 1.65
  body-sm:
    fontFamily: "'Rubik', system-ui, sans-serif"
    fontSize: 14px
    fontWeight: 400
    lineHeight: 1.5
  label-lg:
    fontFamily: "'Rubik', system-ui, sans-serif"
    fontSize: 14.5px
    fontWeight: 600
    lineHeight: 1.2
    letterSpacing: "0.02em"
  label-md:
    fontFamily: "'Rubik', system-ui, sans-serif"
    fontSize: 12px
    fontWeight: 700
    lineHeight: 1.2
    letterSpacing: "0.26em"
  label-sm:
    fontFamily: "'Rubik', system-ui, sans-serif"
    fontSize: 11px
    fontWeight: 500
    lineHeight: 1.2
    letterSpacing: "0.08em"
rounded:
  none: 0px
  sm: 2px
  md: 4px
  lg: 8px
  xl: 16px
  full: 9999px
spacing:
  xs: 4px
  sm: 8px
  md: 16px
  lg: 24px
  xl: 40px
  xxl: 64px
components:
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    rounded: "{rounded.none}"
    padding: 14px
  button-primary-hover:
    backgroundColor: "{colors.on-primary-container}"
    textColor: "{colors.on-primary}"
    rounded: "{rounded.none}"
    padding: 14px
  button-secondary:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.on-surface}"
    rounded: "{rounded.none}"
    padding: 14px
  card:
    backgroundColor: "#FFFFFF"
    textColor: "{colors.on-surface}"
    rounded: "{rounded.none}"
    padding: 24px
  input-field:
    backgroundColor: "#FFFFFF"
    textColor: "{colors.on-surface}"
    rounded: "{rounded.none}"
    padding: 12px
---

# Ascot Real Estate Brand Style

## Overview

Ascot Real Estate is a Brisbane agency whose design system was settled by the client team on 2026-07-16 and shipped as the Ascot 2026 production build. The character is light and warm, with photography doing the selling. One deep luxury red is reserved for actions and small accents, shapes are square and architectural, whitespace is generous, and an editorial serif sits over a clean light-weight sans.

The single most important restraint is that the red is a splash, never a wash. The team explicitly rejected a red footer. Large surfaces belong to warm paper and charcoal; red belongs to the thing you want clicked.

Australian English throughout. This is a Pro Marketing client, so copy uses AU spelling (colour, realise, organisation) and AU conventions for dates, phone numbers and addresses.

## Colors

| Role | Hex | Notes |
|---|---|---|
| Primary | `#9E1B2E` | The deep luxury red. Actions, active nav underline, category labels, step numerals, trust-bar highlight. Never a large background wash |
| On-Primary | `#FFFFFF` | Label on filled red |
| Primary Container | `#F3DDE0` | Softest red tint, sparing use |
| On-Primary Container | `#7C1526` | The darker red, hover depth for primary actions |
| Secondary | `#1B1A17` | Charcoal. Footer, the dark boxed filter bar, structural dark strips |
| On-Secondary | `#F3EFE8` | Text on charcoal |
| Tertiary | `#E3DCCF` | Sand, the deepest warm neutral. Grid gaps and decorative bands only, never a text ground |
| Surface | `#F7F4EF` | Warm paper. The page ground and the header band |
| On-Surface | `#211F1B` | Warm near-black body text. Never pure black |
| Surface Variant | `#ECE7DF` | Stone. Secondary panels, soft section breaks |
| On-Surface Variant | `#6B6459` | Muted supporting text |
| Outline | `#6E6658` | Darkest caption tone. AA 4.5+ on paper, stone and white |
| Outline Variant | `#DAD4C8` | Hairlines and borders, the structural workhorse |
| Error | `#BA1A1A` | Validation and destructive states only |

**Color scheme:** light only. There is no dark mode in this system; the charcoal sections are a structural device, not a theme.

**Accent rule:** one accent, `#9E1B2E`. Never introduce a second. Emphasis that is not the accent comes from weight, size, or a change of surface.

**Contrast:** the palette is AA by construction, proven across 420 pages during the design study. Sand (`#E3DCCF`) and the hairline tone (`#DAD4C8`) are never text backgrounds.

## Typography

**Newsreader** (variable 200 to 800, self-hosted WOFF2) is the display serif for headlines, listing prices and editorial moments. Regular weight at large sizes with tight -0.01em tracking. A light Google Fonts substitute is Newsreader itself, which is freely available.

**Rubik** (variable 300 to 900, self-hosted WOFF2) is the workhorse sans. Body sits at light 300, UI and labels at 500 to 700.

### Hierarchy

| Role | Font | Size | Weight | Line height | Tracking |
|---|---|---|---|---|---|
| `{typography.display}` | Newsreader | 60px | 400 | 1.08 | -0.01em |
| `{typography.headline-lg}` | Newsreader | 40px | 400 | 1.15 | -0.01em |
| `{typography.headline-md}` | Newsreader | 30px | 400 | 1.2 | normal |
| `{typography.title-lg}` | Rubik | 21px | 600 | 1.3 | normal |
| `{typography.title-md}` | Rubik | 17px | 600 | 1.4 | normal |
| `{typography.body-lg}` | Rubik | 18px | 300 | 1.65 | normal |
| `{typography.body-md}` | Rubik | 16px | 300 | 1.65 | normal |
| `{typography.body-sm}` | Rubik | 14px | 400 | 1.5 | normal |
| `{typography.label-lg}` | Rubik | 14.5px | 600 | 1.2 | 0.02em |
| `{typography.label-md}` | Rubik | 12px | 700 | 1.2 | 0.26em |
| `{typography.label-sm}` | Rubik | 11px | 500 | 1.2 | 0.08em |

### Principles

- **The eyebrow is a documented style.** `{typography.label-md}` above a heading (12px, 700, 0.26em tracking, uppercase, usually primary red) is part of the editorial language the client chose. Several design linters ban an eyebrow above a heading outright. On this brand that ban is wrong and is a standing, deliberate override.
- **Serif for the idea, sans for the interface.** Newsreader carries headlines, prices and pull quotes. Rubik carries everything a visitor reads at length or operates.
- **Body runs light.** Rubik 300 at 1.65 line height is the reading default. Do not bump body to 400 to make it "clearer"; the lightness plus the generous leading is the voice.
- **Nothing bold in the serif.** Newsreader stays at 400. Weight is not how this brand emphasises.

### Documented off-ramp sizes

The ramp above covers editorial type. Six literal in-between sizes are documented as intentional rather than left as drift, and they fill gaps the ramp leaves.

- **19px** intro and lead paragraphs, one notch above `{typography.body-lg}`.
- **20px** sub-lead body in long-form service and story pages. The most-used of the six.
- **22px** card and section sub-headings sitting just above `{typography.title-lg}`.
- **23px** a one-off emphasis pair.
- **26px** a step below `{typography.headline-md}` for tighter headings.
- **28px** modal and form headings, where 30px crowds the dialog.

Two further literal sizes are control dimensions, not type, and must never be folded into the ramp: **24px** icon and control glyph size, and **44px** the minimum tap target.

A size that is neither on the ramp nor on this list is drift. Fix it or document it.

## Layout

8px base grid. 1200px content max-width, 12 columns, 24px gutters.

Listing grids are TWO columns on desktop and single below 768px. Three columns was explicitly rejected by the client team as a squeeze that cheapens the photography.

Hero photography runs about 80 percent of viewport height with content peeking below the fold, so the page announces itself as an image before it announces itself as text.

For decks, translate this as a two-column maximum for any card or listing grid, and a full-bleed image band for the opening frame.

## Elevation & Depth

Depth comes from hairline borders and photography, not from shadows. The `{colors.outline-variant}` hairline does the structural work and carries the system, with 67 uses across the production source against a single shadow.

That one shadow is a soft hover lift, `0 18px 40px rgba(20,18,15,0.14)`, and it appears in exactly three places, all of them card grids that link onward. Adding a second elevation step is a design decision, not a convenience.

Hero headings and their eyebrows carry a `text-shadow` for legibility over photography. That is a contrast device for text on an image, not an elevation step, and it does not make shadow part of the depth language.

## Shapes

Square is the brand. Buttons, cards, inputs and images all render at 0 radius. The production source reaches for a radius utility only six times across the whole site.

The `rounded` scale (2, 4, 8, 16px, plus a 9999px `full`) exists for rare soft elements. Note that `full` is currently UNUSED. There is no pill or chip in this build and `border-radius: 9999px` appears nowhere in the compiled CSS. Reaching for it is a deliberate addition to the language, not a default that already exists.

## Components

### button-primary

Red fill, white label, square, 14px by 24px padding. At most one filled action per composition. Hover deepens to `{colors.on-primary-container}`.

### button-secondary

The ghost. Transparent on its surface with a 1.3px `{colors.on-surface}` border. Hover swaps border and text to primary red. On dark photography the border and text go white.

### ulink (prose action)

The premium non-filled action, used for a Learn More integrated into a paragraph rather than bolted beside it. 600-weight text with a 1.5px primary-red underline offset 3px; hover colours the text red.

### card

White on the paper ground, hairline border, square, 24px padding. Listing cards make the ENTIRE card clickable with no View Listing button, and carry a corner status label over the image.

### input-field

White fill, square, hairline border, focus ring in primary red. Form inputs match the card language.

## Do's and Don'ts

### Do

- Use the eyebrow. `{typography.label-md}` above a heading is a documented style and a standing override of the generic ban.
- Let property photography zoom on hover. A subtle scale on listing imagery is deliberate and a real-estate convention. A common generated-UI rule says never animate an image on hover; here it is overridden on purpose.
- Keep text on the warm near-black `{colors.on-surface}`, never pure black. The whole palette is warm and `#000000` reads cold against paper.
- Put the logo on warm paper in full colour. The header band exists so the logo has its correct ground. Never use the white knockout logo on this brand's own surfaces.
- Spend motion on one authored moment rather than a reveal on every section.
- Hold 44px as the tap-target floor. It is an accessibility floor, not a design preference.
- Write to house style. No em or en dashes, straight quotes, no colons in headings, Australian English.

### Don't

- No gradient text. Emphasis comes from weight, size and colour.
- No cards nested inside cards. Nesting muddies the single elevation step the system defines.
- No red as a large background wash. The client rejected a red footer; splashes only.
- No three-column listing grids. Two on desktop, one below 768px.
- Never `scrollreveal`. GPL-3.0 plus a paid commercial licence, unusable on closed-source client work.
- No grey text on a coloured surface. Derive muted text from that surface's own hue; the palette already provides `{colors.on-surface-variant}` and `{colors.on-primary-container}` for exactly this.
- No pure black, no cold greys, no second accent.

## Icons

Font Awesome **light** family line icons, exclusively. One family per surface, never mixed weights. Primary surfaces are the listing feature grid (beds, baths, cars and the extended features vocabulary), the trust bar, contact details and service cards. Icons render as build-time inline SVG inheriting `currentColor`.

## Motion

The production site's own motion is CSS transitions (`transition-colors` most, then `transition-transform`, at 300, 500 and 700ms), and a motion library should not be added for an effect CSS already expresses cleanly.

The settled grammar is reveal rises, group staggers, counters, and the listing-card zoom-on-hover punch-in that the client explicitly kept. `prefers-reduced-motion` renders everything settled.

Where a Pro Marketing concept or campaign piece calls for authored motion beyond what CSS covers, the house engine is GSAP with effects briefed by number from The Motion Index catalogue. That is the agency's wider stack, not this site's, and introducing it here needs a reason.

Timing, in every case: roughly 100 to 150ms for immediate feedback, 150 to 300ms for a routine state change, 300 to 500ms for layout or overlay, and 500 to 800ms only for a genuinely authored entrance. Exits are faster than entrances.

## Responsive Behavior

| Name | Width | Key changes |
|---|---|---|
| Phone | < 768px | Listing grid collapses to one column. Hero photography keeps its dominance but reduces height. Section padding tightens |
| Tablet | 768 to 1024px | Listing grid at two columns, tighter gutters |
| Desktop | 1024 to 1200px | Full 12-column layout, two-column listings, 24px gutters |
| Wide | > 1200px | Content locks at 1200px, margins absorb the extra width |

**Touch targets:** 44px minimum on gallery controls, lightbox controls and the header toggle. Never reduced.

**Collapsing strategy:** listing grid two columns to one at 768px. Header links collapse to a toggle. The dark filter bar keeps its full-width treatment and reduces internal padding rather than restructuring.

**Image behavior:** hero photography holds roughly 80 percent viewport height on desktop and reduces on phone without surrendering its position above the content. Listing imagery keeps its aspect ratio and its hover zoom at every width.

## Iteration Guide

1. Reference tokens by key (`{colors.primary}`, `{typography.headline-lg}`, `{components.card}`) rather than inlining hex or px.
2. One filled red action per composition. If a second action is needed it is `button-secondary` or `ulink`, never a second fill.
3. Square by default. Radius is an exception that needs a reason.
4. Reach for a hairline before reaching for a shadow. The system has exactly one shadow and it is a hover lift on linking card grids.
5. When a section feels flat, change the surface (paper to stone, or paper to charcoal) before adding chrome.
6. Serif for the idea, sans for the interface. Do not let Newsreader creep into UI labels or Rubik into a headline.
7. Copy is Australian English and house style. No em or en dashes, straight quotes, no colons in headings.

## Known Gaps

- `prefers-reduced-motion` is honoured in exactly one place in the production build and is not handled globally. Any new work should honour it properly rather than assume the site already does.
- There is no dark mode. Requests for one are a design decision for the client, not a token exercise; the charcoal sections are structural and are not a theme to invert into.
- The `rounded.full` token exists but is unused. It is not an established part of the language.
- Logo assets are not carried in this file. Pull them from the client repo rather than recolouring or reconstructing a mark.

---

## Reference

**Website:** [https://ascot.net.au](https://ascot.net.au)

**Source of record:** `clients/ascot-re-2026/site/DESIGN.md` in the Pro Marketing web agency repo. That file owns the tokens; this one is the power-design port. If they disagree, the client repo wins and this file should be re-ported.
