# Build stack reference (fork addition)

Distilled from `power-design-web`, this skill's sister repo, so the material travels with the plugin instead of living behind a link.

## When to read this

Read it when the job is a real multi-file project, or when the user explicitly asks for a stack, a framework, or a token pipeline.

**Do not reach for it on the default output.** Path B ships a single self-contained responsive HTML file with no external JS dependencies, and that contract is deliberate. Nothing below is a reason to add a build step to a page that does not need one.

## What governs

`principles/web-principles.md` is the rulebook. Where it and this file cover the same ground, the rulebook wins, without exception. This file exists to add the parts it does not carry, which are the lineage behind design tokens, the tooling that transforms them, and the named layers of a modern stack. The overlap table at the end names the governing source for every point of contact.

---

## Design tokens, the atoms

A design token is a named entity holding a single design decision, one colour, one spacing value, one radius. Author it once, transform it to every platform that needs it.

**2016.** Salesforce coins the term. Jina Anne introduces design tokens in the Lightning Design System, abstracting visual decisions away from any single platform.

**2025.** The W3C Design Tokens Community Group ratifies v1, a JSON interchange format built on three keys.

| Key | Holds |
|---|---|
| `$value` | The decision itself |
| `$type` | What kind of decision it is, so a consumer knows how to read it |
| `$description` | Why, for the humans |

**Why this matters inside this skill.** Every brand file written to the schema in **New brand files** carries a YAML token block for exactly this reason, and it is why prose in those files can say `{colors.primary}` and have it resolve. The DTCG format is the interchange standard that idea comes from, and it is what makes a brand file readable by a linter rather than only by a person.

## The token cascade

Three stages, one source of truth.

**01, author.** One file, DTCG compliant, portable across Figma, code, iOS and Android.

```json
{
  "color.accent": {
    "$value": "#2DD4BF",
    "$type": "color"
  }
}
```

**02, transform.** Style Dictionary or Tokens Studio emits CSS, JS, iOS and Android output from that single source.

```css
:root {
  --color-accent: #2DD4BF;
  --space-4: 16px;
  --radius-md: 8px;
}
```

**03, apply.** Every component references the variable rather than the value, so a change at the top reaches everything below it.

```css
.btn-primary {
  background: var(--color-accent);
  padding: var(--space-4);
}
```

The single-file output already does stage 3 and a hand-written stage 2. Stage 1 only earns its place when more than one platform consumes the same decisions.

## shadcn/ui, source you own

Shipped in 2023 by shadcn. It is a CLI that writes component source code into the repo rather than a package that installs into `node_modules`.

```bash
npx shadcn@latest add button
```

That writes `components/ui/button.tsx` into the project. There is no dependency and no upgrade path, because there is no version to upgrade against. The docs open by saying it is not a component library, it is how you build your own.

| The library model | The shadcn model |
|---|---|
| Opaque dependency, customised through theme overrides and prop drilling | Source in the repo, edited directly |
| Major versions break the UI | No version drift |
| Cannot fork it, it is a dependency | Already forked, it is your file |

Underneath, it is Radix for behaviour and Tailwind for styling. It composes the two rather than replacing either.

## Tailwind v4, CSS-first and token-fluent

Adam Wathan released Tailwind in 2017. Utility-first displaced semantic class naming because naming things semantically was the part of CSS that did not scale.

Version 4, January 2025, moved configuration into CSS itself.

```css
@theme {
  --color-accent: oklch(0.78 0.13 195);
  --radius-md: 0.5rem;
}
```

```html
<button class="bg-accent rounded-md px-4 py-2">Save</button>
```

Four things follow from that.

- `@theme` replaces `tailwind.config.js`, so there is no JavaScript build step in the way of the tokens.
- Every utility name is a token reference. `bg-accent` is not a style, it is a binding to `--color-accent`.
- The default palette is OKLCH, which reaches the wider P3 gamut.
- Builds run through Lightning CSS.

The second point is the one that matters for this skill. In v4 the config file and the token file are the same artifact, which is the same collapse the brand files make.

## Radix, the accessibility backbone

Three layers, and only the top one is visible.

| Layer | What lives there |
|---|---|
| Your styles | Tailwind utilities, CSS variables, brand tokens |
| Component behaviour | State, events, animation |
| Radix primitives | ARIA roles, focus management, keyboard handling, screen reader semantics |

Radix ships the bottom layer unstyled. It handles the part of a component that is genuinely hard and invisible when done right, which leaves only the visible part to design. Maintained by WorkOS. Adobe ships an equivalent as React Aria hooks.

The relevance to a single-file output is indirect but real. It is a checklist of what a hand-rolled dropdown or dialog has to do before it is finished, and web principle #18 is where that obligation is already written down.

## The 12-step scale, what each step is for

A modern colour scale has twelve steps and each one has a documented job. Verified against Radix Colors' own documentation.

| Step | Job |
|---|---|
| 1 | App background |
| 2 | Subtle background |
| 3 | UI element background, normal state |
| 4 | Hovered UI element background |
| 5 | Active or selected UI element background |
| 6 | Subtle borders and separators, non-interactive |
| 7 | UI element border and focus rings |
| 8 | Hovered UI element border, stronger focus rings |
| 9 | Solid backgrounds, the highest chroma step |
| 10 | Hovered solid background, where 9 is the resting state |
| 11 | Low-contrast text |
| 12 | High-contrast text |

Step 9 is the solid action colour and the one a brand's accent usually maps to. Steps 11 and 12 are text. Steps 1 and 2 are canvas.

The point of the model is subtractive. With twelve named jobs there is no moment mid-build where a new colour has to be invented, which is where most palettes lose their coherence. Swapping the scale for its dark counterpart re-themes the whole surface without touching a single component.

## Six canonical systems to study

Public, documented, code-backed, and shipping at scale every day.

| System | Where | What to take from it |
|---|---|---|
| Vercel Geist | vercel.com/geist | High-contrast monochrome, sharp radii, Geist Sans and Mono. The cleanest modern token set to read |
| GitHub Primer | primer.style | Powers GitHub itself. CSS, React and ViewComponents flavours, a decade of production hardening |
| IBM Carbon | carbondesignsystem.com | Enterprise grade, documented exhaustively, backed by the IBM Design Language |
| Material 3 | m3.material.io | Dynamic colour, a full motion token system, expressive theming |
| Apple HIG | developer.apple.com/design | Semantic colour tiers, SF Symbols, native motion. Less to copy, more to study |
| Atlassian | atlassian.design | Voice, illustration, motion and components. End to end at scale |

## The layered stack

The architecture credible teams converge on for a React product surface. Each layer is replaceable, and the discipline is picking one thing per layer rather than two.

| Layer | Default | Role |
|---|---|---|
| L7 | Next.js App Router | Framework |
| L6 | shadcn/ui | Component source you own |
| L5 | Tailwind v4 | Tokens and utilities, CSS-first |
| L4 | Radix Primitives | Accessible behaviour |
| L3 | GSAP (house), Motion in a React codebase | Animation |
| L2 | lucide-react | Icon set on a 24 by 24 grid |
| L1 | next-themes | Dark and light toggle, handles the SSR flash |

**L3 diverges from the sister repo deliberately.** It names Motion, formerly Framer Motion, which is the React-idiomatic choice. The house engine is GSAP, briefed by number from The Motion Index. Either way the **Motion** section of this skill governs which effects earn their place, since that doctrine is engine-agnostic.

## Motion timing, reconciled

The sister repo presents Material 3 as four curves with durations attached. Google's own token file separates them into six easing tokens and a sixteen-step duration ladder, so the pairing below is drawn from the verified source rather than the summary.

M3 durations run `short1-4` at 50, 100, 150 and 200ms, `medium1-4` at 250, 300, 350 and 400ms, `long1-4` at 450, 500, 550 and 600ms, and `extra-long1-4` at 700, 800, 900 and 1000ms.

Every boundary in this skill's motion table is an exact step on that ladder, so no band value changes. The reconciled table lives in the **Motion** section of `SKILL.md` and is the binding one. What follows is the evidence behind it.

| M3 easing token | Verified value |
|---|---|
| `easing-standard` | `cubic-bezier(0.2, 0, 0, 1)` |
| `easing-standard-accelerate` | `cubic-bezier(0.3, 0, 1, 1)` |
| `easing-standard-decelerate` | `cubic-bezier(0, 0, 0, 1)` |
| `easing-emphasized` | `cubic-bezier(0.2, 0, 0, 1)` |
| `easing-emphasized-accelerate` | `cubic-bezier(0.3, 0, 0.8, 0.15)` |
| `easing-emphasized-decelerate` | `cubic-bezier(0.05, 0.7, 0.1, 1)` |

`easing-standard` and `easing-emphasized` are the same curve in Google's current token file. The difference between the two systems is carried by duration and by the accelerate and decelerate variants, not by the base curve.

**These values are reference, not adoption.** The house arrival easing is `cubic-bezier(0.16, 1, 0.3, 1)` and it stays. The M3 names are useful vocabulary for describing intent, and the ladder is useful evidence that the band boundaries are not arbitrary. Neither is a licence to pull Google's bezier values into an output.

---

## Where this file and the rulebook overlap

Every point of contact, with the governing source named. When in doubt the rulebook wins and this column says so.

| Topic | Governs | What this file adds |
|---|---|---|
| OKLCH colour | `web-principles.md` #12 | The 12-step job mapping, and why 9 is the action colour |
| Semantic tokens | `web-principles.md` #12 | The DTCG interchange format and the three-stage cascade above it |
| 8-point spacing | `web-principles.md` #10 | Nothing. Identical rule, stated once |
| Modular type scale | `web-principles.md` #3 and #10 | Nothing. The rulebook's fluid `clamp()` scale supersedes a fixed px ladder |
| Dark mode | `web-principles.md` #12 and the output contract | `next-themes` as the React implementation of the same token swap |
| Motion timing and easing | The **Motion** section of `SKILL.md` | The verified M3 ladder as evidence, above |
| Motion engine | The **Motion** section of `SKILL.md` | GSAP is the house engine. The sister repo's L3 is the React alternative |
| Core Web Vitals and budgets | `web-principles.md` #17 | Nothing |
| Accessible component behaviour | `web-principles.md` #18 | Radix as the reference implementation of what a primitive owes |
| Output format | The Path B output contract | Nothing. A stack is for a real project, never for the default single file |

## Source and licence

Derived from [power-design-web](https://github.com/ItsssssJack/power-design-web) at commit `5fb71a9`, MIT licensed, copyright Jack Roberts.

Two claims were checked against primary sources rather than carried across, because both became normative once they entered this skill.

- Material 3 easing and duration tokens, verified against `material-components/material-web`, `tokens/versions/v0_192/_md-sys-motion.scss`.
- The 12-step scale job mapping, verified against Radix Colors' own scale documentation.

The sister repo predates this skill's current form, so `principles/web-principles.md` is the newer word wherever the two differ.
