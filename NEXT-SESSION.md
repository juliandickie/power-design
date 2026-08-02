# Next session - power-design fork

Nothing is queued and nothing is in flight **in this repo**. The 0.3.0 build shipped on 2026-08-02 and landed through push and tag. The open items below are candidates, not a queue.

**One thing is in flight elsewhere.** `~/code/pro-marketing-web-agency` is ahead of its origin by two unpushed commits, one of them from this session and one from a parallel session sitting on top of it. Read **Not landable from here** below before touching that repo.

## Read before touching anything

1. `CLAUDE.md` here - the fork contract. Upstream files are NEVER edited. All customisation goes in `skills/power-design/SKILL.md`, in NEW files under `brands/`, or in `skills/power-design/references/`.
2. `SESSION-HANDOFF-2026-08-02-B.md` - the 0.3.0 build, its decisions, the corrections it made to previously recorded facts, and the footguns.
3. `SESSION-HANDOFF-2026-08-02.md` - the 0.2.0 build that preceded it the same day.
4. This file.
5. `~/code/repos/CLAUDE.md`, the `ItsssssJack/power-design` and `ItsssssJack/power-design-web` entries - the review verdicts, the licence position, and the correction to both.
6. `pro-marketing-web-agency/docs/superpowers/specs/2026-07-29-design-toolchain-analysis.md` - why this skill sits where it does in the four-layer split. **It carries a dated correction note at the top**; read that before its section 1.

## State

**Verified 2026-08-02, session `7190de54-c486-4560-9364-de75eb148c24`.** Verify it again with `git log` rather than trusting this prose.

- `main` in sync with `origin/main`, working tree clean, no branches local or remote beyond `main`. **Read the HEAD sha from `git log`, it is deliberately not quoted** - handoff commits land after the tag, so any sha written into this file is stale the moment it is committed.
- Tagged `v0.3.0`, annotated and pushed. `v0.2.0` is also tagged and has a GitHub release at https://github.com/juliandickie/power-design/releases/tag/v0.2.0. **`v0.3.0` has no release**, by design, that is Julian's call.
- Upstream remote wired to `ItsssssJack/power-design`, last merged against `26d1492`.
- Ledger `diff SKILL.md skills/power-design/SKILL.md` is **135 added, 3 modified**.
- `claude plugin validate .` passes with one expected warning about root `CLAUDE.md`. Do not try to fix that warning.

## Already done, do not redo

- **0.2.0 and 0.3.0 both shipped and are recorded in `CLAUDE.md`.** Four customisations plus the brand file schema in 0.2.0; the build stack reference and the motion reconciliation in 0.3.0.
- **`power-design-web` is distilled.** It is `skills/power-design/references/build-stack.md`. Do not distil it again, and read that file rather than the 1290-line HTML page at `~/code/repos/ItsssssJack/power-design-web/`.
- **The two marketplace catalogs are current enough.** `~/code/outfit` (`49842d1`) and `~/code/ai-loadout` (`332ffe7`), pushed 2026-08-02 and verified live via the GitHub contents API. Neither pins a version, so the 0.3.0 bump did not stale them. Their descriptions do not mention the build stack reference, which is a nice-to-have, not a defect. Both entries are byte-identical to each other; keep them that way if either changes.
- **The design-toolchain analysis and both hub CLAUDE.md files are corrected.** The census is 43 spec-ordered / 27 numbered / 2 short-template, with the classifier recorded so it stays reproducible.

## Not landable from here

`~/code/pro-marketing-web-agency` is **ahead of `origin/main` by 3**, all unpushed:

- `f423b12` - this session's correction to the design-toolchain analysis. One file.
- `c0f9afc` - a **parallel session's** "Session close 2026-08-02" commit, sitting on top of it.
- `1670557` - this session's matching correction to that repo's hub `CLAUDE.md`, which was still asserting the disproven premise. One file.

Mine sandwich theirs, so neither of mine can be pushed without pushing their session close too, and landing another session's work is against the standing rules. That repo also still carries three modified and ten untracked paths belonging to that session or a third one. **Leave all of it.** The resolution is Julian's call, or the owning session pushes and carries mine along correctly.

## Candidates, ranked

1. **Decide whether to cut a GitHub release for `v0.3.0`.** Tag is pushed, release is not created. A publish action, needs Julian's go.
2. **Decide what, if anything, goes upstream.** House style guard and motion doctrine are general-purpose. The build stack reference is now a third candidate and is also general-purpose, but it embeds house positions (GSAP as the engine, the fork's motion table, the deferral to `web-principles.md`) that would need stripping first. Positioning boundary and client brand systems are house-specific and should not be offered. The orphaned `{colors.x}` references in `brands/apple` and its siblings are a genuine upstream defect worth reporting either way. Touches a third party's repo, so it needs its own go.
3. **Refresh the two marketplace catalog descriptions** to name the build stack reference. Optional, cosmetic.
4. **Add more client brand systems** as new `brands/<slug>/brand-style.md` files, to the schema in the shipping skill's **New brand files** section. Needs Julian to name the clients and supply URLs or existing DESIGN.md files.

## Standing rules

- Upstream files are pristine and stay that way - root `SKILL.md`, `principles/`, `lib/`, `README.md`, `LICENSE`, `.gitignore`, and the 72 upstream `brands/*` entries. Verify with `git diff 26d1492 HEAD -- <paths>`; it must come back empty.
- House formatting applies to fork-authored files and fork-added lines only - no em or en dashes, straight quotes, no colons in headings. Upstream lines keep upstream's style. The check reports **one expected false positive**, the `brands/_template.md` line, whose em dash is inherited from upstream's line 180. Confirm any hit against `git show HEAD:SKILL.md` before treating it as new.
- Every `gh` command in this repo needs `-R juliandickie/power-design`. It is a fork with no default repo set, so `gh` otherwise resolves to `ItsssssJack/power-design`.
- Verify against the rendered artifact, never a status line. For the symlinks that means reading a file **through** the link, not checking the link exists.
- `skills/power-design/references/` is a real directory, not a symlink. Do not convert it.
- `power-design-web` is a SECONDARY source. Verify its claims against the primary before letting them bind anything; two of the three checked so far were wrong.
- Never push unasked. Commit, push, merge and tag are separate mid-session actions, each needing an explicit go. The `/handoff` ritual is what authorises landing.
- Subagent fan-outs run on Sonnet; judgement and final QA stay in the main session.

## Kickoff prompt

Working directory `/Users/juliandickie/code/power-design` (Julian's fork of ItsssssJack/power-design, its own repo, on `main`, clean and in sync with origin, tagged `v0.3.0`; read the current HEAD from `git log` rather than assuming a sha, since handoff commits land after the tag). READ FIRST, in the order listed under "Read before touching anything" in `NEXT-SESSION.md`, and treat those over any assumption. The 0.2.0 and 0.3.0 builds are both DONE, tagged and pushed; `power-design-web` is already distilled into `skills/power-design/references/build-stack.md`, and the two marketplace catalogs are current. Do not rebuild or re-audit any of it. DO NOT TOUCH `~/code/pro-marketing-web-agency` beyond reading - it is ahead of its origin by two unpushed commits, one mine and one a parallel session's session-close sitting on top of mine, plus that session's uncommitted WIP across thirteen paths; none of it is yours to land or tidy, and its hub `CLAUDE.md` carries a deliberate uncommitted correction. Pick work from the ranked candidates in `NEXT-SESSION.md`, confirming with me first, since candidates 1 and 2 are publish actions and candidate 2 touches a third party's repo. Do NOT edit any upstream file - root `SKILL.md`, `principles/`, `lib/` and the 72 existing `brands/*` entries must stay pristine so future merges never conflict; verify with `git diff 26d1492 HEAD` and expect empty. House formatting rules (no em or en dashes, straight quotes, no colons in headings) apply to fork-authored files and fork-added lines only, and the checker's one hit on the `brands/_template.md` line is an expected false positive inherited from upstream. Treat `power-design-web` as a secondary source and verify its claims against the primary before letting them bind anything. Every `gh` command needs `-R juliandickie/power-design` or it resolves to upstream. Run `claude plugin validate .` and confirm the three symlinks resolve by reading a file THROUGH each one before calling anything done. Never push unasked.
