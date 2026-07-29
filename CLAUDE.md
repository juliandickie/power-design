# power-design fork - project guide

Julian Dickie's fork of [ItsssssJack/power-design](https://github.com/ItsssssJack/power-design), packaged as a Claude Code plugin and carrying Pro Marketing customisations while still merging upstream's development. Same contract as the juliandickie/no-ai-slop fork, which proved the pattern.

## Layout contract

Upstream files are never edited here. That single rule keeps every future upstream merge conflict-free.

- `SKILL.md` (repo root), `principles/`, `brands/` (upstream's), `lib/` - UPSTREAM'S source of truth. Change only via merges from upstream.
- `skills/power-design/SKILL.md` - THE SHIPPING SKILL the plugin loads. Starts byte-identical to root `SKILL.md`; all customisation happens here.
- `skills/power-design/{principles,brands,lib}` - relative SYMLINKS to the repo-root dirs, so the shipping skill's references (`principles/design-principles.md`, `brands/<name>/brand-style.md`, `lib/extract-brand.md`) resolve from the skill's own base directory without duplicating 20M of assets. Git preserves the symlinks through the plugin-install clone. macOS and Linux only; if a Windows consumer ever matters, replace the links with copies at that point.
- `.claude-plugin/plugin.json`, `CLAUDE.md` - additive, upstream has no equivalents.

`diff SKILL.md skills/power-design/SKILL.md` is the standing customisation ledger and upstream-contribution candidate list. Empty diff = pure upstream.

## Versioning

Upstream carries no version anywhere (no manifest, no tags), so the plugin version is FORK-OWNED - semver starting 0.1.0, bumped when the shipping skill or packaging changes materially. Record the upstream commit merged against in the bump commit message.

## Sync ritual

1. `git fetch upstream` (remote configured to ItsssssJack/power-design)
2. `git merge upstream/main` - should never conflict
3. `diff SKILL.md skills/power-design/SKILL.md` - port upstream improvements into the shipping copy by hand, keep deliberate divergences
4. New upstream brands or principles arrive through the symlinks automatically - review them rather than assuming they fit
5. Commit the port separately from the merge commit

## Planned customisations (all go in the shipping copy or as NEW files under brands/)

- Pro Marketing client brand systems as new `brands/<slug>/brand-style.md` entries (Ascot Real Estate tokens exist in the ascot-re-2026 DESIGN.md; iDD brand tokens are on record) - new files, zero upstream conflict.
- House style guard in the shipping skill - no em or en dashes in generated copy, straight quotes, AU English for Pro Marketing clients, US for iDD.
- Motion routed to GSAP and The Motion Index catalogue (house engine; never scrollreveal), replacing any generic motion guidance.
- Positioning boundary - in Julian's stack this skill is the DECK and BRAND-EXTRACTION specialist. Everyday web-page design voice stays with frontend-design plus ui-ux-pro-max; do not let three overlapping design voices argue.

## Sibling repo

juliandickie/power-design-web (also forked) is the same author's cited HTML explainer of the web design stack - reference material, not a skill. If distilled, it lands here as a references/ file in the shipping skill, not as its own plugin.

## House style

Fork-authored files follow Julian's formatting rules - no em or en dashes, straight quotes, no colons in headings. Upstream files keep upstream's style untouched.
