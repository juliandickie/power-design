# Session handoff - power-design fork 0.2.0 shipped

**Previous handoff** - `archive/NEXT-SESSION-2026-07-29.md`, the kickoff that queued this build.

**Nothing is in flight.** The session landed completely - merged, tagged, released, branch deleted local and remote, working tree clean. The next session starts from a clean `main` with no WIP to inherit.

## Goal

Carry Pro Marketing customisations on the power-design fork while still merging upstream's development, using a layout contract where upstream files are never edited so future merges stay conflict-free.

## State

**Verified as of 2026-08-02, by `git log`, `git ls-remote`, `gh pr view`, `gh release view` and `claude plugin validate`, not from memory of the conversation.**

Repo `/Users/juliandickie/code/power-design`, the only repo touched this session.

| Item | Value |
|---|---|
| `main` HEAD | `bbd8f6c` Merge pull request #1 |
| `origin/main` | `bbd8f6c`, in sync |
| Tag | `v0.2.0` (annotated, object `c4c3378`) pointing at `bbd8f6c`, pushed |
| PR | [#1](https://github.com/juliandickie/power-design/pull/1), MERGED 2026-08-02 |
| Release | [v0.2.0](https://github.com/juliandickie/power-design/releases/tag/v0.2.0), published, not a draft |
| Branch `customisations-0.2.0` | deleted, local and remote. `origin` carries only `main` |
| Working tree | clean |
| Plugin version | 0.2.0 |
| Upstream merged against | `ItsssssJack/power-design` `26d1492`, unchanged since |

The nine commits, in build order - `61e6c7d` Ascot brand, `3c276d7` iDD brand, `4f45ca9` house style guard, `edc313a` motion, `e382b75` positioning boundary, `ee5d9a9` bump to 0.2.0, `9824a00` extractor schema, `a363105` CLAUDE.md current, `4750bae` sync note corrected.

**Layout contract held.** `git diff 26d1492 HEAD -- SKILL.md principles/ lib/ README.md LICENSE .gitignore` is empty; those files are byte-identical to upstream. The only entries against `brands/` are the two adds. The three asset symlinks are still git mode `120000` and resolve.

**Ledger** (`diff SKILL.md skills/power-design/SKILL.md`) is **133 added, 2 modified**.

## Decisions

**Brand file format - spec-ordered shape plus a YAML token block.** Chosen by Julian after a census corrected the premise the build was queued on. `archive/NEXT-SESSION-2026-07-29.md` and the design-toolchain analysis both state the brand library was restructured into a bespoke nine-section numbered format that is not DESIGN.md-spec compliant. That is true of 27 of the 72 files. **42 already follow canonical DESIGN.md section order exactly** (Overview, Colors, Typography, Layout, Elevation & Depth, Shapes, Components, Do's and Don'ts) and 3 use the short `brands/_template.md` form. New files match the spec-ordered majority.

*Rejected* - the short `_template.md` shape that the kickoff literally named, because only 3 of 72 files use it and it would have discarded most of the Ascot DESIGN.md detail. Also rejected, the nine-section numbered shape, as the non-spec form the analysis warned against extending.

**Token block in frontmatter, a fork addition with no upstream equivalent.** Upstream's restructure out of awesome-design-md left orphaned `{colors.x}` and `{typography.x}` references in files like `brands/apple` with no token block to resolve them. Ours resolve, and the `google-labs-code/design.md` linter can read them.

**Motion - GSAP named as the house engine, but the default output stays CSS.** A literal "always GSAP" would break upstream's own output contract (a single self-contained HTML file, no external JS deps, on both paths) and contradict two positions already on record - impeccable's anti-dependency rule and the Ascot DESIGN.md's own "keep motion in CSS". So scrollreveal is banned outright and GSAP is named as the engine for when motion exceeds what CSS expresses cleanly or when scaffolding a real project. The timing table, easing and bans are engine-agnostic and bind either way.

**Positioning boundary placed before Step 0, not with the other fork blocks.** It is a routing decision and has to fire before the skill commits to a path. Path B was deliberately NOT retired - the distinction that matters is whether the job starts from brand DNA, not whether the output is a deck or a page.

**`lib/extract-brand.md` overridden, not edited.** It is upstream's file and carries the same `_template.md` instruction. The skill's new **New brand files** section says explicitly that it supersedes that step, because the skill still sends the reader to that recipe for the scrape itself and a silent contradiction would be worse than the original problem.

**Merge commit rather than squash or rebase.** The brief required one commit per customisation with the ledger diff quoted; squashing would destroy that, and rebasing would change SHAs already reported and recorded here. The repo's prior history is linear, so this is the first merge commit in it - a deliberate trade of style consistency for traceability.

**Version stayed 0.2.0 through the extractor fix.** Nothing had been pushed, merged or tagged at that point, so 0.2.0 had never existed outside the branch and the fix belonged to that release rather than a bump on top of it.

## Tried and failed

**`gh pr create` failed with "No commits between main and customisations-0.2.0".** This repo is a fork and no default repo is set, so `gh` resolved to the PARENT, `ItsssssJack/power-design`. Always pass `-R juliandickie/power-design` explicitly. This matters beyond convenience - without `-R`, a PR intended for Julian's fork can be opened against a third party's repo.

## Julian's feedback this session

- On the loose end left after the version bump - "fix the extractor to point at the same shape". Confirmed the extractor should follow the same brand schema as the two new files.
- On landing - "push it and open the PR and merge and tag and release". Explicit authorisation through release, which is why this session went past the usual mid-session commit gate.
- Both format questions answered with the recommended option, spec-ordered shape and full token block.

## Recipes and footguns

- `claude plugin validate .` is the gate. It passes with one warning, that a root `CLAUDE.md` is not loaded as plugin context. That is structural, expected, and predates this work; `CLAUDE.md` here is the fork contract for developers in the repo, deliberately not shipped context. Do not "fix" it by converting it to a skill.
- Any `gh` command in this repo needs `-R juliandickie/power-design`. See Tried and failed.
- The three asset symlinks (`principles`, `brands`, `lib` inside `skills/power-design/`) must stay git mode `120000`. Verify by reading a file THROUGH the link, not by checking the link exists. macOS and Linux only.
- House style applies to fork-authored files and to fork-added lines only. Upstream's em dashes in the shipping `SKILL.md` stay untouched. The check that respects that boundary is `diff SKILL.md skills/power-design/SKILL.md | grep '^>' | grep -P '[\x{2014}\x{2013}\x{2018}\x{2019}\x{201C}\x{201D}]'`.
- The new schema block in the shipping skill embeds `---` inside a YAML code fence. If that section is edited, re-check that the skill's own frontmatter still parses and fences still balance.

## Open work, ranked

1. **The two marketplace catalogs carry stale descriptions.** `~/code/outfit/.claude-plugin/marketplace.json` and `~/code/ai-loadout/.claude-plugin/marketplace.json` (line 415 in each, both repos clean and in sync) describe power-design as "72+ pre-built brand systems ... packaged as a Claude Code plugin, tracking upstream". It is now 74 brands and carries real customisations. **They source by git URL with no version pin, so 0.2.0 is already live to consumers** - this is description accuracy, not a distribution blocker. Separate repos, so it needs its own go.
2. **Decide whether to offer anything upstream.** The house style guard and the motion doctrine are general-purpose and would likely be welcome. The positioning boundary and the client brand systems are house-specific and should not be offered. The orphaned `{colors.x}` token references in files like `brands/apple` are a genuine upstream defect worth reporting regardless.
3. **Fold `power-design-web` into a `references/` file** in the shipping skill, per the sibling-repo note in `CLAUDE.md`.
4. **Consider `brands/_template.md`.** It is upstream's and stays pristine, but it now describes a shape only 3 of 74 files use, and the skill has to route around it. If more brands get added, the routing note is doing real work and should be checked for clarity.

## Questions for Julian

- Should the catalog descriptions be refreshed now, or left until more accumulates in the fork?
- Is the house style guard worth a PR to `ItsssssJack/power-design`, or does it stay a house divergence? Same question for the motion doctrine.
- The 27 nine-section brand files and the 3 short-template ones were left as they are. Worth converting to the spec-ordered shape at some point, or is inconsistency in upstream's files acceptable given they are upstream's to change?
