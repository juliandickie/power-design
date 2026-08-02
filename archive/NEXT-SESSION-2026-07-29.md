# Next session - power-design customisation build (QUEUED)

Julian queued this build on 2026-07-29. State verified as of that date; the session that created the fork also wrote this.

## State

- This repo = juliandickie/power-design, main at bb2c5c9, PUSHED, clean. Upstream remote wired to ItsssssJack/power-design (fork == upstream 26d1492 plus the packaging and kickoff commits).
- Plugin packaging DONE and validated - `.claude-plugin/plugin.json` (version 0.1.0, FORK-OWNED because upstream carries no version anywhere), `skills/power-design/SKILL.md` (the shipping copy, currently byte-identical to root `SKILL.md`), and the asset symlinks (`principles`, `brands`, `lib`) verified resolving and recorded in git as mode 120000.
- LISTED in the outfit and ai-loadout catalogs (pushed, cache-verified, installable). Deliberately NOT installed on Julian's machine - see the positioning note below.
- The customisation ledger, `diff SKILL.md skills/power-design/SKILL.md`, is EMPTY. Pure upstream. That diff is the whole point of the fork layout; it stays the standing record of what is ours.

## Read before touching anything

1. `CLAUDE.md` here - the fork contract. Upstream files are NEVER edited. All customisation goes in `skills/power-design/SKILL.md` or in NEW files under `brands/`.
2. This file.
3. `~/code/repos/CLAUDE.md`, the `ItsssssJack/power-design` entry - the review verdict and the licence position.
4. `pro-marketing-web-agency/docs/superpowers/specs/2026-07-29-design-toolchain-analysis.md` - why this skill sits where it does in the four-layer split, and the correction that its brand library is a restructured, NON-spec-compliant copy of VoltAgent/awesome-design-md.

## The work, in priority order

**1. Ascot Real Estate brand system** as `brands/ascot-real-estate/brand-style.md`, from `clients/ascot-re-2026/site/DESIGN.md` in the pro-marketing-web-agency repo, using `brands/_template.md` as the schema. A NEW file, so zero upstream conflict. Tokens are already exact - primary `#9E1B2E`, surface `#F7F4EF`, on-surface `#211F1B`, secondary `#1B1A17`, tertiary `#E3DCCF`, outline-variant `#DAD4C8`; Newsreader display serif over Rubik.

**2. iDD brand system** as `brands/idd/brand-style.md` from the recorded tokens - `#052648` navy, `#1EB5BD` teal, `#EFC319` star gold, Montserrat.

**3. House style guard** in the shipping SKILL.md copy - never emit em or en dashes in generated copy, straight quotes only, no colons in headings, AU English for Pro Marketing clients and US English for iDD. This is the first real ledger entry, so quote the diff in the commit message.

**4. Motion routed to the house engine** in the shipping copy - GSAP and The Motion Index catalogue, never scrollreveal (GPL-3.0 plus a paid commercial licence, unusable on closed-source client work). Worth folding in the timing discipline from impeccable's `animate.md` while here - one authored focal moment rather than a reveal on every section, 100-150ms feedback, 150-300ms routine, 300-500ms layout, 500-800ms an authored entrance, exit faster than entrance, `cubic-bezier(0.16, 1, 0.3, 1)` for arrivals, bounce and elastic banned by reflex.

**5. Positioning boundary** stated in the shipping copy. In this stack power-design is the DECK and BRAND-EXTRACTION specialist. Everyday web design voice stays with `frontend-design` (taste) plus `ui-ux-pro-max` (knowledge); `impeccable` is deterministic enforcement. Three overlapping design voices arguing is the failure mode this boundary exists to prevent, and it is why the plugin is listed but not installed locally.

Each customisation is its OWN commit with the ledger diff quoted. Bump the plugin version to 0.2.0 at the end.

## Consider, do not assume

The brand library here was restructured out of `VoltAgent/awesome-design-md` into a bespoke nine-section numbered format that is NOT DESIGN.md-spec compliant, so the design.md linter cannot validate it. The originals upstream ARE spec-format. If the goal is brand references rather than this skill's deck routing, awesome-design-md is the better source. Worth deciding deliberately before adding more brands in the non-spec shape.

## Kickoff prompt

Working directory `/Users/juliandickie/code/power-design` (Julian's fork, main, its own repo, in sync with origin). READ FIRST, in the order listed under "Read before touching anything" above, and treat those over any assumption. Then build the customisations in the priority order given, each as its own commit quoting the ledger diff (`diff SKILL.md skills/power-design/SKILL.md`), finishing with a version bump to 0.2.0. Do NOT edit any upstream file - root `SKILL.md`, `principles/`, `lib/` and the existing `brands/*` entries are upstream's and must stay pristine so future merges never conflict. Before calling anything done, run `claude plugin validate .` and confirm the three symlinks still resolve. Never push unasked. House formatting rules (no em or en dashes, straight quotes, no colons in headings) apply to fork-authored files only; upstream files keep upstream's style.
