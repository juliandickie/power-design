# Session handoff - power-design fork 0.3.0, the build stack reference

**Previous handoff** - `SESSION-HANDOFF-2026-08-02.md`, the 0.2.0 build earlier the same day.

**Nothing is in flight in this repo.** The session landed through push and tag. Working tree clean, no branches, nothing staged.

**One thing is in flight elsewhere and it is not mine to land.** `~/code/pro-marketing-web-agency` sits **ahead of `origin/main` by 3 unpushed commits**, two of them mine with a parallel session's session-close sandwiched between them. See **The sibling repo situation** below before touching that repo.

## Goal

Carry Pro Marketing customisations on the power-design fork while still merging upstream's development, using a layout contract where upstream files are never edited so future merges stay conflict-free. This session closed the last self-contained customisation candidate, folding the sister repo's explainer into the shipping skill.

## State

**Verified 2026-08-02 by `git log`, `git status -sb`, `git ls-remote`, `claude plugin validate` and by reading files through the symlinks. Session `7190de54-c486-4560-9364-de75eb148c24`.**

| Item | Value |
|---|---|
| Branch | `main`, clean, in sync with `origin/main` |
| `main` HEAD | **read it from `git log`.** Handoff commits land after the tag, so any sha written here is stale the moment it is committed |
| Tag | `v0.3.0`, annotated, pushed |
| Plugin version | 0.3.0 |
| PR | none. The work was committed directly to `main` on Julian's explicit choice of the no-branch option, so there was nothing to open a PR against |
| Release | **not created.** `v0.2.0` has a GitHub release; `v0.3.0` has a tag only. Julian's call, see Open work |
| Upstream merged against | `ItsssssJack/power-design` `26d1492`, unchanged since 0.2.0 |
| Ledger | `diff SKILL.md skills/power-design/SKILL.md` is **135 added, 3 modified** |
| `claude plugin validate .` | passes, one expected `CLAUDE.md` warning. Do not try to fix that warning |

The four commits of this session, in build order and stable regardless of later handoff commits:

- `a047167` Add the build stack reference distilled from the sister repo
- `6c0210e` Route the shipping skill at the reference and reconcile motion with M3
- `0861356` Bump plugin to 0.3.0
- `d8dd465` Record 0.3.0 and the re-verified brand file census

**Layout contract held.** `git diff 26d1492 HEAD -- SKILL.md principles/ lib/ README.md LICENSE .gitignore` is empty. The only entries against `brands/` remain the two 0.2.0 adds. The three asset symlinks are still git mode `120000` and were verified by reading a file **through** each link, not by the link existing.

## What shipped

**`skills/power-design/references/build-stack.md`**, new, fork-authored, zero upstream contact. The sister repo `power-design-web` distilled so the material travels with the plugin instead of behind a link.

It carries only the eight things `principles/web-principles.md` does not already govern - design tokens and the DTCG interchange format, the three-stage token cascade, shadcn as source you own, Tailwind v4 `@theme`, the Radix layer model, the 12-step scale job mapping, six canonical systems, and the layered stack. Roughly half the source was already in the rulebook with better numbers, so it is deferred to rather than restated. A closing table names the governing source for all ten points of overlap. MIT attribution to Jack Roberts at `5fb71a9` is carried in the file.

**The motion timing table reconciled with Material 3.** Band values unchanged; each band gained a curve name and a point default.

## Decisions

**Delta only, plus a reconciliation table.** Offered three scopes; Julian took the most thorough. A faithful nine-section distillation was *rejected* because it would have restated OKLCH, semantic tokens, the 8-point scale, the modular ratio, dark mode, motion and Core Web Vitals, all of which `web-principles.md` already governs with better numbers. A skill that says the same thing twice in two voices is worse than one that says it once.

**Line 234 repointed rather than appended beside.** This takes the ledger to three modified upstream lines. The alternative kept it at two but left two pointers to the same subject sitting next to each other. Julian took the cleaner reader experience over the lower merge cost, knowingly. All three modified lines are now documented in `CLAUDE.md` under **Upstream lines touched**.

**Motion reconciled rather than recorded as reference or omitted.** The heaviest of the three options, and the one that touches a checklist-bound rule. It turned out to be safe: **every boundary in the fork's table (100, 150, 300, 500, 800) is an exact step on M3's duration ladder**, so the reconciliation added columns and changed no number. Nothing that shipped at 0.2.0 behaves differently.

*Explicitly not adopted* - M3's bezier values. `cubic-bezier(0.16, 1, 0.3, 1)` remains the house arrival easing, and both the skill and the reference say so outright, because the trap is reading a curve name and pulling Google's values in with it.

**No branch, committed straight to `main`.** Julian's choice from the landing options. The 0.2.0 build used a branch and a PR; this one did not, and that is why there is no PR number above.

**Version 0.3.0, not 0.2.1.** A new file the skill routes to is a minor-version amount of change by the standard in `CLAUDE.md`.

## Corrections made to previously recorded facts

Two recorded claims turned out to be wrong. Both were checked because they were about to become normative.

**Material 3 timings.** `power-design-web` presents M3 as four curves with durations attached ("standard 200ms", "emphasized 500ms"). Google's own token file separates **six easing tokens** from a **16-step duration ladder** (short1-4 50/100/150/200, medium1-4 250/300/350/400, long1-4 450/500/550/600, extra-long1-4 700/800/900/1000). The source had flattened two independent systems into one table. Primary source used, sister repo's version discarded.

**The brand file census.** Recorded at 0.2.0 as 42 spec-ordered / 27 numbered / 3 short-template. Re-running it with an explicit classifier gives **43 / 27 / 2**. The two genuinely template-shaped files are `glaido` and `grind`, which open at `## Colors` with no `## Overview`; every other non-numbered file carries at least six of the canonical eight headings. The `27` is identical under both counts and is the figure every conclusion rests on, so nothing downstream moved. Corrected in this repo's `CLAUDE.md` and in the pro-marketing-web-agency analysis doc, with the classifier recorded so it stays reproducible.

**The lesson worth keeping.** `power-design-web` predates this skill's current form by six weeks and is a secondary source. Verify anything from it against the primary before letting it bind behaviour. Both claims checked this session needed it.

## The sibling repo situation

`~/code/pro-marketing-web-agency` was touched for two files, both carrying the same census correction - the design-toolchain analysis (`f423b12`) and the hub `CLAUDE.md` whose design-tooling paragraph was still asserting the disproven premise (`1670557`). Each commit holds exactly one file, verified with `git show --stat`.

**A parallel session was live in that repo throughout and is still mid-flight.** Sequence observed:

1. At session start it had 6 modified and 10 untracked paths, none mine.
2. Mid-session that session committed `f433a64` and pushed it, so three of those dirty files became theirs and committed.
3. My `f423b12` landed on top.
4. That session then committed `c0f9afc` "Session close 2026-08-02 - handoff, hub docs, and the learnings worth keeping" on top of mine, and **did not push it**.
5. My `1670557` landed on top of that, carrying the same correction into the repo's hub `CLAUDE.md`. It was committed rather than left dirty precisely so it would not sit as an unexplained working-tree change in someone else's session.
6. That session still leaves `research/ascot/design-2026/{CLAUDE.md,NEXT-SESSION.md,concepts/README.md}` modified and ten untracked paths, which is unusual after a session close and may be a third session.

**Net state - that repo is ahead of `origin/main` by 3 unpushed commits, `f423b12` (mine), `c0f9afc` (theirs), `1670557` (mine).** Mine sandwich theirs, so neither of mine can be pushed without pushing their session close too. That would be landing another session's work, which the standing rules forbid, so it was left alone. Julian was told.

Julian's read going into this handoff was that the other session had "cleaned that up". It had not, in the sense that matters - it ran its own close on top of my commit and left everything unpushed, so the repo is more entangled than before, not less.

**Do not push that repo to resolve this.** Ask Julian, or let the session that owns `c0f9afc` push it, which carries mine along correctly.

## Tried and failed

**`WebFetch` cannot read m3.material.io.** The Material 3 docs are JS-rendered and the fetch returns the page title and nothing else. What worked was going to Google's own implementation instead - `gh api "search/code?q=md-sys-motion+repo:material-components/material-web"` to find the path, then fetching `https://raw.githubusercontent.com/material-components/material-web/main/tokens/versions/v0_192/_md-sys-motion.scss`. Note the two levels of indirection: `tokens/_md-sys-motion.scss` and `tokens/v0_192/_md-sys-motion.scss` are both `@forward` stubs, and only `tokens/versions/v0_192/` holds the values.

**`grep --include='*.json'` unquoted fails in zsh** with "no matches found" before grep ever runs. Quote the pattern.

## Julian's feedback this session

- Chose the heavier option at every one of the three design forks, then again on version (0.3.0) and landing. Consistent with "maximum effort, never the path of least resistance"; when offering options here, order them thorough-first.
- "yep build it" - approval came immediately once the design was presented with the trade-offs named and a recommendation attached. The design presentation was worth doing; the ceremony around it was not.
- On landing - took "commit both repos, nothing further", explicitly declining branch, push and tag mid-session. The `/handoff` ritual is what authorised push and tag.

## Recipes and footguns

- `claude plugin validate .` is the gate. One expected warning, that a root `CLAUDE.md` is not loaded as plugin context. Structural, predates all this work. Do not "fix" it by converting it to a skill.
- Any `gh` command in this repo needs `-R juliandickie/power-design`. It is a fork with no default repo set, so `gh` otherwise resolves to `ItsssssJack/power-design` and a PR intended for Julian's fork can be opened against a third party's repo.
- The three asset symlinks must stay git mode `120000`. **Verify by reading a file through the link**, not by checking the link exists. A dangling symlink is indistinguishable from a good one in `ls`.
- `skills/power-design/references/` is a REAL directory, not a symlink, because upstream has no root `references/` to point at. Do not convert it.
- House style applies to fork-authored files and fork-added lines only. The check is `diff SKILL.md skills/power-design/SKILL.md | grep '^>' | grep -P '[\x{2014}\x{2013}\x{2018}\x{2019}\x{201C}\x{201D}]'`. **It reports one false positive**, the `brands/_template.md` line, whose em dash is inherited from upstream's line 180 through a fork modification. That is correct and expected. Confirm any hit against `git show HEAD:SKILL.md` before treating it as new.
- The brand schema block in the shipping skill embeds `---` inside a YAML code fence. If that section is edited, re-check that the skill's own frontmatter still parses and fences still balance (`grep -c '^\`\`\`'` must be even).
- Neither marketplace catalog pins a version, only a description, so a version bump alone never stales them.

## Open work, ranked

1. **Push `~/code/pro-marketing-web-agency`, or decide who does.** Two unpushed commits, one mine and one another session's, mine underneath. Not landable from here without landing theirs. This is the only thing in flight anywhere from this session.
2. **Decide whether to cut a GitHub release for `v0.3.0`.** The tag is pushed; `v0.2.0` has a release and `v0.3.0` does not. Release is a publish action and needs Julian's go.
3. **Decide what, if anything, goes upstream.** The house style guard and the motion doctrine are general-purpose and would likely be welcome. The build stack reference is now a third candidate and is also general-purpose, though it embeds house positions (GSAP as engine, the fork's motion table) that would need stripping first. The positioning boundary and the client brand systems are house-specific and should not be offered. The orphaned `{colors.x}` references in `brands/apple` and its siblings are a genuine upstream defect worth reporting either way. Touches a third party's repo, so it needs its own go.
4. **Refresh the marketplace catalog descriptions**, optional. Both are accurate but neither mentions the build stack reference. `~/code/outfit` and `~/code/ai-loadout`, entries must stay byte-identical to each other.
5. **Add more client brand systems** as new `brands/<slug>/brand-style.md` files, to the schema in the shipping skill's **New brand files** section. Needs Julian to name the clients and supply URLs or existing DESIGN.md files.

## Questions for Julian

- Who pushes `pro-marketing-web-agency`, and is the parallel session's `c0f9afc` finished work or mid-flight?
- Release for `v0.3.0`, or let tags accumulate and release once?
- Is the build stack reference worth offering upstream once the house positions are stripped out, or does it stay a house divergence like the positioning boundary?
