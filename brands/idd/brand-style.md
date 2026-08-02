---
brand: Institute of Digital Dentistry
slug: idd
website: https://instituteofdigitaldentistry.com
source: iDD production CSS, read from stylesheets on 2026-07-13
extracted_via: editorial - verified from live CSS, not from screenshots
locale: en-US
colors:
  primary: "#052648"
  on-primary: "#FFFFFF"
  primary-cta: "#071726"
  primary-cta-hover: "rgba(15,48,82,0.9)"
  accent: "#1EB5BD"
  link: "#1175A4"
  surface: "#FFFFFF"
  on-surface: "#0C1115"
  on-surface-strong: "#0A0A0A"
  rating-filled: "#EFC319"
  rating-empty: "#D3DADF"
typography:
  heading:
    fontFamily: "'Montserrat', system-ui, sans-serif"
    fontWeight: 400
  button:
    fontFamily: "'Montserrat', system-ui, sans-serif"
    fontWeight: 600
  body:
    fontFamily: "'Montserrat', system-ui, sans-serif"
    fontSize: 18px
    fontWeight: 300
    lineHeight: 2em
  body-bold:
    fontFamily: "'Montserrat', system-ui, sans-serif"
    fontSize: 18px
    fontWeight: 500
    lineHeight: 2em
rounded:
  default: 10px
  pill-sm: 50px
  pill-lg: 100px
layout:
  content-width: 1200px
  content-width-home: 1300px
components:
  button-primary:
    backgroundColor: "{colors.primary-cta}"
    textColor: "{colors.on-primary}"
    fontFamily: "'Montserrat', system-ui, sans-serif"
    fontWeight: 600
    rounded: "{rounded.default}"
    shadow: "rgba(0,0,0,0.25) 0 8px 12px"
  button-primary-hover:
    backgroundColor: "{colors.primary-cta-hover}"
    textColor: "{colors.on-primary}"
    rounded: "{rounded.default}"
---

# Institute of Digital Dentistry Brand Style

## Overview

The Institute of Digital Dentistry (iDD) publishes online dental education and distributes dental technology into Australia, New Zealand and Canada. Its public face and clinical authority is Dr Ahmad Al-Hassiny. The audience is practising dental professionals evaluating scanners, printers, mills and CAD/CAM software, so the register is clinical and evidence-led rather than promotional.

Visually the system is a deep navy over white, with one bright teal used as the single accent and a warm gold confined to product-rating widgets. Type is Montserrat throughout. The defining trait is the body setting, 18px at weight 300 with a 2em line height held from desktop all the way down to mobile, which gives long review articles an unusually open, unhurried read.

US English throughout, including for readers in AU and NZ. The only exception is a course written specifically for an AU or NZ audience, which takes AU or NZ English.

## Colors

| Role | Hex | Notes |
|---|---|---|
| Primary | `#052648` | Master navy. H2, H4 and H6 headings, and the inner of the logo mark |
| Primary CTA | `#071726` | The deeper navy used for buttons and nav. Distinct from the master navy, not a substitute for it |
| Primary CTA hover | `rgba(15,48,82,0.9)` | Button and nav hover state |
| On-Primary | `#FFFFFF` | Label on navy |
| Accent | `#1EB5BD` | Teal. The hero divider and the outer edge of the logo gradient. This is the one accent |
| Link | `#1175A4` | Post body links. A muted blue, deliberately not the teal |
| Surface | `#FFFFFF` | Body background. The system is white-ground |
| On-Surface | `#0C1115` | Heading near-black |
| On-Surface Strong | `#0A0A0A` | The darker near-black variant also present in production |
| Rating filled | `#EFC319` | Star gold in product-rating widgets |
| Rating empty | `#D3DADF` | Empty star outline |

**Color scheme:** light only, on a white ground.

**Accent rule:** teal `#1EB5BD` is the single accent. The gold is not a second accent; it is a data colour that belongs to rating stars and nowhere else. Do not use gold for emphasis, CTAs, dividers or highlights.

**Two navies, on purpose.** `#052648` is the brand navy that headings and the logo carry. `#071726` is the near-black navy that buttons and nav carry. They are close enough to look like a mistake and are not. Use each in its documented role.

## Typography

**Montserrat** is the brand typeface and does all the work. It is served by Google Fonts as a single variable WOFF2 (latin subset, roughly 35KB, covering weights 100 to 900). Source Sans Pro, Roboto and Poppins are also loaded in production but are minor and should not be reached for in new work.

### Hierarchy

| Role | Font | Size | Weight | Line height |
|---|---|---|---|---|
| `{typography.heading}` | Montserrat | not on record | 400 | not on record |
| `{typography.body}` | Montserrat | 18px | 300 | 2em |
| `{typography.body-bold}` | Montserrat | 18px | 500 | 2em |
| `{typography.button}` | Montserrat | not on record | 600 | not on record |

### Principles

- **Headings run at 400 by default sitewide.** Montserrat at regular weight is the heading voice. Reaching for 600 or 700 on a heading is a departure, not a default.
- **Body is 18px at weight 300 with a 2em line height, and that holds at every width.** It is not reduced on mobile. This is a confirmed decision, not an artifact, and it is the single most recognisable thing about reading an iDD page. Embedded components must mirror it or they will read as foreign inside an article.
- **Bold body is weight 500, not 700.** The contrast step in body copy is small on purpose.
- **Buttons are Montserrat 600.** This is the one place a heavier weight is standard.
- Heading sizes are not on record. Extract them live rather than inventing a ramp; see Known Gaps.

## Layout

Content width is 1200px, with the home page running wider at 1300px. Blog posts use full-width sections and carry **no sidebar**, so an article is a single centred column with full-bleed section bands rather than a two-column editorial layout.

For decks, translate this as a single centred content column with full-bleed image or colour bands between sections.

## Elevation & Depth

Depth is minimal and is carried almost entirely by one button shadow, `rgba(0,0,0,0.25) 0 8px 12px`. Against a white ground with navy elements, that shadow is what separates an action from the page.

No card elevation system is on record. Sections separate by full-width colour band rather than by lifting a surface, which is consistent with the full-width no-sidebar layout.

## Shapes

`10px` border radius is the most common shape in production and is the default. Pills are also in use at `50px` and `100px` radius, typically on smaller controls and tags.

This is a softer shape language than the navy palette suggests. Do not square it off.

## Components

### button-primary

White Montserrat 600 label on the CTA navy `{colors.primary-cta}`, 10px radius, with the `rgba(0,0,0,0.25) 0 8px 12px` shadow. Hover moves to `{colors.primary-cta-hover}`.

### rating widget

Product-rating blocks are the Thrive Architect native Rating element, stars only with no numerals. The categories in use are Print Speed, Reliability, Ease of Use, Software, Material Options and Investment. Filled stars are `{colors.rating-filled}`, empty are `{colors.rating-empty}`.

Note this component is legacy. It appears only in older roundup posts; the newest reviews carry no rating block at all. Do not add one to new work without checking whether it is still wanted.

## Do's and Don'ts

### Do

- Hold the body setting. 18px, weight 300, 2em line height, at every breakpoint including inside embedded components.
- Use teal `#1EB5BD` as the single accent, and keep it to dividers and brand moments.
- Keep gold to rating stars. It is a data colour.
- Use `#052648` for headings and the logo, `#071726` for buttons and nav. Both navies, each in its own role.
- Use `#1175A4` for links in post body copy, not the teal and not the navy.
- Write in US English, including for AU and NZ readers. AU or NZ English only for a course written specifically for that market.
- Write clinically. The audience is practising dentists evaluating equipment, and the authority is Dr Ahmad Al-Hassiny.
- Keep articles single-column and full-width. No sidebar.

### Don't

- Don't reduce body size or line height on mobile. The open setting is the brand.
- Don't use gold as an accent, a CTA colour, or a highlight.
- Don't use `#FFD700` for stars. It appears in some older posts and is inconsistency, not an alternative; `#EFC319` is canonical.
- Don't square the corners. 10px is the default and pills are in use.
- Don't set headings at 600 or 700 by default. Montserrat 400 is the heading voice.
- Don't introduce Source Sans Pro, Roboto or Poppins. They load in production but are residue, not part of the system.
- Don't add a rating widget to a new review without confirming it is wanted. The newest reviews deliberately have none.
- Don't overstate a product claim. Specifications, prices and clinical claims are checkable and the audience checks them.

## Responsive Behavior

The one confirmed responsive rule is that the body setting does not change. 18px at weight 300 with a 2em line height is maintained from desktop through to mobile.

Content width caps at 1200px (1300px on the home page) and the layout is a single centred column with full-width section bands, so the collapse from desktop to mobile is a narrowing rather than a restructure.

Breakpoint values are not on record. See Known Gaps.

## Iteration Guide

1. Reference tokens by key (`{colors.primary}`, `{colors.accent}`, `{typography.body}`) rather than inlining hex.
2. Check which navy the element wants before picking one. Headings and logo take `#052648`; buttons and nav take `#071726`.
3. One accent. If a second colour seems necessary, the answer is usually a change of section band, not a new hue.
4. Any embedded component inside an article inherits the 18px, 300, 2em body setting. This is the most common way new work reads as foreign.
5. Radius defaults to 10px. Pills are available for small controls.
6. US English, and the register is clinical rather than promotional.
7. Where this file says a value is not on record, extract it rather than inventing it. Run the Firecrawl extractor in `lib/extract-brand.md` against the site and update this file with the result.

## Known Gaps

These are absent from the record rather than absent from the brand. Extract them before relying on a guess.

- **Heading sizes and line heights.** Only the weight (400) is confirmed. There is no documented H1 through H6 ramp.
- **Button padding and size.** Font family, weight, colours, radius and shadow are confirmed; dimensions are not.
- **Breakpoint values.** The body setting is confirmed to hold across them, but the widths themselves are not recorded.
- **Spacing scale.** No base unit or spacing scale is on record.
- **Logo assets.** Not carried here. The mark has a navy inner and a teal gradient outer edge; pull the real asset rather than reconstructing it.
- **Dark mode.** None on record. Assume it does not exist.
- The tokens above were read from production CSS on 2026-07-13. If the site has been restyled since, re-extract before trusting them.

---

## Reference

**Website:** [https://instituteofdigitaldentistry.com](https://instituteofdigitaldentistry.com)

To refresh this brand, run the Power Design Firecrawl extractor in `lib/extract-brand.md` against `https://instituteofdigitaldentistry.com` and reconcile the output against this file rather than overwriting it, since the role distinctions above (two navies, gold as a data colour only) are editorial judgements a scrape will not reproduce.
