# power-design fork - project guide

Julian Dickie's fork of [ItsssssJack/power-design](https://github.com/ItsssssJack/power-design), packaged as a Claude Code plugin and carrying Pro Marketing customisations while still merging upstream's development. Same contract as the juliandickie/no-ai-slop fork, which proved the pattern.

## Layout contract

Upstream files are never edited here. That single rule keeps every future upstream merge conflict-free.

- `SKILL.md` (repo root), `principles/`, `brands/` (upstream's), `lib/` - UPSTREAM'S source of truth. Change only via merges from upstream.
- `skills/power-design/SKILL.md` - THE SHIPPING SKILL the plugin loads. Starts byte-identical to root `SKILL.md`; all customisation happens here.
- `skills/power-design/{principles,brands,lib}` - relative SYMLINKS to the repo-root dirs, so the shipping skill's references (`principles/design-principles.md`, `brands/<name>/brand-style.md`, `lib/extract-brand.md`) resolve from the skill's own base directory without duplicating 20M of assets. Git preserves the symlinks through the plugin-install clone. macOS and Linux only; if a Windows consumer ever matters, replace the links with copies at that point.
- `skills/power-design/references/` - a REAL directory, not a symlink, because upstream has no root `references/` to point at. Fork-authored material that belongs to the shipping skill rather than to the asset tree.
- `.claude-plugin/plugin.json`, `CLAUDE.md` - additive, upstream has no equivalents.

`diff SKILL.md skills/power-design/SKILL.md` is the standing customisation ledger and upstream-contribution candidate list. Empty diff = pure upstream. It stopped being empty at 0.2.0; see Delivered customisations below.

## Versioning

Upstream carries no version anywhere (no manifest, no tags), so the plugin version is FORK-OWNED - semver starting 0.1.0, bumped when the shipping skill or packaging changes materially. Record the upstream commit merged against in the bump commit message.

## Sync ritual

1. `git fetch upstream` (remote configured to ItsssssJack/power-design)
2. `git merge upstream/main` - should never conflict
3. `diff SKILL.md skills/power-design/SKILL.md` - port upstream improvements into the shipping copy by hand, keep deliberate divergences
4. New upstream brands or principles arrive through the symlinks automatically - review them rather than assuming they fit
5. Commit the port separately from the merge commit

## Delivered customisations (0.2.0, built 2026-08-02 against upstream 26d1492)

All four planned items shipped, plus one follow-on. Four changes live in the shipping copy and show in the ledger diff; the brand systems are new files with zero upstream contact.

- **Pro Marketing client brand systems** as new `brands/<slug>/brand-style.md` entries - `ascot-real-estate` (ported from the ascot-re-2026 DESIGN.md, which stays the source of record) and `idd` (from tokens read off production CSS on 2026-07-13). Library is now 74.
- **House style guard** in the shipping skill - no em or en dashes in generated copy, straight quotes, no colons in headings, spelling read from a `locale` field in the brand file (`en-AU` for Pro Marketing clients, `en-US` for iDD). Enforced by a line on both pre-emit checklists, not just stated in prose.
- **Motion routed to the house engine** - GSAP plus The Motion Index catalogue, never scrollreveal, with impeccable's timing table, `cubic-bezier(0.16, 1, 0.3, 1)` arrivals, and the one-authored-focal-moment rule. The default single-file output stays on CSS because a no-external-JS file is upstream's own output contract; GSAP is for when motion exceeds what CSS expresses cleanly, or for a real multi-file project.
- **Positioning boundary** stated before Step 0 - this skill is the DECK and BRAND-EXTRACTION specialist, frontend-design owns taste, ui-ux-pro-max owns knowledge, impeccable owns enforcement. Path B is retained for pages that genuinely start from a brand system, which is the cold-start case.

### Brand file format, decided 2026-08-02

New brand files use the **spec-ordered shape** (Overview, Colors, Typography, Layout, Elevation & Depth, Shapes, Components, Do's and Don'ts, then extensions), **plus a full YAML token block in frontmatter**.

This corrects a premise carried in NEXT-SESSION.md and the design-toolchain analysis, which both described the library as a bespoke non-spec nine-section numbered format. A census of the 72 upstream files found three shapes, not one. The spec-ordered majority is the right neighbour to match.

| Shape | Count |
|---|---|
| Canonical DESIGN.md section order | 43 |
| Nine-section numbered | 27 |
| Short `brands/_template.md` form (`glaido`, `grind`) | 2 |

**Re-verified 2026-08-02 with an explicit classifier**, which moved one file and superseded the 42/27/3 first recorded here. A file is numbered if any heading matches `^## [0-9]+\.`, otherwise spec-ordered if it carries six or more of the canonical eight headings, otherwise short template. The 27 is identical under both counts and is the figure the conclusion rests on, so nothing downstream changes. The design-toolchain analysis in pro-marketing-web-agency carries the same corrected table.

The token block is a fork improvement with no upstream equivalent. Upstream's restructure out of awesome-design-md left orphaned `{colors.x}` and `{typography.x}` references in files like `brands/apple` with no token block to resolve them. Ours resolve, and the `google-labs-code/design.md` linter can read them.

The shipping skill's **New brand files (fork addition)** section carries the schema, so the Firecrawl extractor writes new brands to this shape rather than to the short template. `lib/extract-brand.md` is upstream's and still points at `brands/_template.md`; it stays pristine and is overridden from the skill rather than edited. The 72 files that arrived with upstream are not being converted.

## Delivered in 0.3.0, built 2026-08-02 against upstream 26d1492

- **Build stack reference** as a new `skills/power-design/references/build-stack.md`, the sister repo `power-design-web` distilled so the material travels with the plugin instead of sitting behind a link. It carries only what `principles/web-principles.md` does not already govern - design tokens and the DTCG interchange format, the three-stage token cascade, shadcn, Tailwind v4 `@theme`, the Radix layer model, the 12-step scale job mapping, six canonical systems, and the layered stack. It ends with a table naming the governing source for all ten points of overlap, so nothing in it can be read as competing with the rulebook. MIT attribution to Jack Roberts is carried in the file, since a derived work redistributed inside a plugin has to carry the notice.
- **Motion table reconciled with Material 3.** The four bands are unchanged. Each gained a curve name and a point default, because every band boundary already sat on an exact step of M3's duration ladder, so nothing that shipped at 0.2.0 behaves differently. `cubic-bezier(0.16, 1, 0.3, 1)` remains the house arrival easing, and the file says outright that M3's bezier values are not adopted.

**Prefer the primary source over the sister repo.** Two claims were verified rather than carried across, because both became normative on entering the skill, and both turned out to need it. `power-design-web` presents M3 as four curves with durations attached; Google's own token file (`material-components/material-web`, `tokens/versions/v0_192/_md-sys-motion.scss`) separates six easing tokens from a 16-step duration ladder. The 12-step scale mapping came from Radix Colors' own scale documentation. The sister repo predates this skill's current form by six weeks, which is why it is a starting point and not an authority.

### Upstream lines touched

The fork mostly appends, which is what keeps merges clean. Three places modify an upstream line instead, and those three are the only spots where a future upstream merge needs a real decision rather than a clean re-append. The ledger reads three `<` against 135 `>`.

- `43c58` - the "Save it as `brand-style.md`" sentence in the shared brand step, repointed from `brands/_template.md` to the fork's schema section.
- `105c234` - the `power-design-web` pointer in Path B's read-before-emitting list, repointed from the GitHub link to the local `references/build-stack.md`.
- `180c311,312` - the `brands/_template.md` entry in "Files in this skill", relabelled as upstream's short template and marked superseded for new files, with the `references/build-stack.md` entry appended directly after it.

### Next candidates

- Consider whether the house style guard and the motion doctrine are worth offering upstream. Both are general-purpose; the positioning boundary and the client brand systems are not. The orphaned `{colors.x}` references in `brands/apple` and its siblings are an upstream defect worth reporting either way. Touches a third party's repo, so it needs its own go.
- Add more client brand systems as new `brands/<slug>/brand-style.md` files, to the schema in the shipping skill's **New brand files** section.

## Sibling repo

juliandickie/power-design-web (also forked) is the same author's cited HTML explainer of the web design stack - reference material, not a skill. **Distilled into `skills/power-design/references/build-stack.md` on 2026-08-02**, from the upstream clone at `~/code/repos/ItsssssJack/power-design-web` (commit `5fb71a9`). The fork stays as upstream-sync insurance; it is not packaged as its own plugin and should not be. Read the distilled file rather than the 1290-line HTML page, and treat `principles/web-principles.md` as the newer word wherever the two differ.

## House style

Fork-authored files follow Julian's formatting rules - no em or en dashes, straight quotes, no colons in headings. Upstream files keep upstream's style untouched.
