# Next session - power-design fork

Nothing is queued and nothing is in flight. The 0.2.0 customisation build shipped on 2026-08-02 and landed completely. This file exists so a fresh session can pick the repo up cold; the open items below are candidates, not a queue.

## Read before touching anything

1. `CLAUDE.md` here - the fork contract. Upstream files are NEVER edited. All customisation goes in `skills/power-design/SKILL.md` or in NEW files under `brands/`.
2. `SESSION-HANDOFF-2026-08-02.md` - what shipped in 0.2.0, the decisions behind it, and the footguns.
3. This file.
4. `~/code/repos/CLAUDE.md`, the `ItsssssJack/power-design` entry - the review verdict and the licence position.
5. `pro-marketing-web-agency/docs/superpowers/specs/2026-07-29-design-toolchain-analysis.md` - why this skill sits where it does in the four-layer split. **Note one correction**, recorded in `CLAUDE.md` - its claim that the brand library is uniformly a non-spec nine-section format is true of 27 of 72 files; 42 already follow canonical DESIGN.md order.

## State

**Verified 2026-08-02.** Verify it again with `git log` rather than trusting this prose.

- `main` is in sync with `origin/main`, working tree clean, no other branches local or remote. **Read the HEAD sha from `git log`, it is not quoted here on purpose** - handoff commits land after the release, so any sha written into this file is stale the moment it is committed. The stable anchors below are the ones to trust.
- Tagged `v0.2.0` at `bbd8f6c`, released at https://github.com/juliandickie/power-design/releases/tag/v0.2.0. PR #1 merged. `main` sits a little ahead of the tag; that is the handoff documentation, not unreleased code.
- Upstream remote wired to `ItsssssJack/power-design`, last merged against `26d1492`.
- Customisation ledger, `diff SKILL.md skills/power-design/SKILL.md`, is **133 added, 2 modified**. It is no longer empty; that diff is the standing record of what is ours.
- `claude plugin validate .` passes with one expected warning about root `CLAUDE.md`. Do not try to fix that warning.

## Already done, do not redo

**The two marketplace catalog descriptions are current.** `~/code/outfit` (`49842d1`) and `~/code/ai-loadout` (`332ffe7`), both pushed 2026-08-02 and verified live via the GitHub contents API. They now read 74 brands and name the fork's additions. Both entries are byte-identical to each other, which is how they have been maintained; keep them that way if either changes again.

## Candidates, ranked

1. **Decide what, if anything, goes upstream.** House style guard and motion doctrine are general-purpose. Positioning boundary and client brands are not. The orphaned `{colors.x}` references in `brands/apple` and its siblings are an upstream defect worth reporting either way. Touches a third party's repo, so it needs its own go from Julian.
2. **Fold `power-design-web` into a `references/` file** in the shipping skill.
3. **Add more client brand systems** as new `brands/<slug>/brand-style.md` files, to the schema in the shipping skill's **New brand files** section.

## Standing rules

- Upstream files are pristine and stay that way - root `SKILL.md`, `principles/`, `lib/`, `README.md`, `LICENSE`, `.gitignore`, and the 72 upstream `brands/*` entries. Verify with `git diff 26d1492 HEAD -- <paths>`; it must come back empty.
- House formatting applies to fork-authored files and fork-added lines only - no em or en dashes, straight quotes, no colons in headings. Upstream lines keep upstream's style.
- Every `gh` command in this repo needs `-R juliandickie/power-design`. It is a fork with no default repo set, so `gh` otherwise resolves to `ItsssssJack/power-design`.
- Verify against the rendered artifact, never a status line. For the symlinks that means reading a file through the link, not checking the link exists.
- Never push unasked. Commit, push, merge, tag are separate mid-session actions, each needing an explicit go.
- Subagent fan-outs run on Sonnet; judgement and final QA stay in the main session.

## Kickoff prompt

Working directory `/Users/juliandickie/code/power-design` (Julian's fork of ItsssssJack/power-design, its own repo, on `main`, clean and in sync with origin, tagged `v0.2.0` at `bbd8f6c`; read the current HEAD from `git log` rather than assuming a sha, since the handoff commits land after the tag). READ FIRST, in the order listed under "Read before touching anything" in `NEXT-SESSION.md`, and treat those over any assumption - note especially the recorded correction to the design-toolchain analysis about the brand library's format. The 0.2.0 build is DONE, merged, tagged and released, and the two marketplace catalogs are already updated and pushed; do not rebuild or redo either, and do not re-audit what `SESSION-HANDOFF-2026-08-02.md` marks as verified. Nothing is in flight and there is no other session's WIP here. Pick work from the ranked candidates in `NEXT-SESSION.md`, confirming with me first, since candidate 1 touches a third party's repo and needs its own go. Do NOT edit any upstream file - root `SKILL.md`, `principles/`, `lib/` and the 72 existing `brands/*` entries must stay pristine so future merges never conflict; verify with `git diff 26d1492 HEAD` and expect empty. House formatting rules (no em or en dashes, straight quotes, no colons in headings) apply to fork-authored files and fork-added lines only. Every `gh` command needs `-R juliandickie/power-design` or it resolves to upstream. Run `claude plugin validate .` and confirm the three symlinks resolve before calling anything done. Never push unasked.
