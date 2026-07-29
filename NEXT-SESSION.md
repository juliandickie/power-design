# Next session - power-design customisation build

Kickoff prompt below; state verified as of 2026-07-29, the session that created this fork.

## State

- This repo = juliandickie/power-design, main at 260f9c4, pushed, clean, upstream remote wired to ItsssssJack/power-design (fork == upstream 26d1492 plus the packaging commit).
- Plugin packaging DONE and validated - .claude-plugin/plugin.json (version 0.1.0, fork-owned), skills/power-design/SKILL.md (shipping copy, currently byte-identical to root SKILL.md), asset symlinks (principles, brands, lib) verified resolving and recorded as git symlinks.
- Listed in the outfit and ai-loadout catalogs (pushed, cache-verified). Deliberately NOT installed on Julian's machine yet.
- The customisation ledger (`diff SKILL.md skills/power-design/SKILL.md`) is EMPTY - pure upstream.

## Kickoff prompt

Working directory /Users/juliandickie/code/power-design (Julian's fork, main, its own repo). READ FIRST, in order - CLAUDE.md here (the fork contract - upstream files are NEVER edited, all customisation goes in skills/power-design/SKILL.md or NEW files under brands/), then this file, then the planned-customisations section of CLAUDE.md - treat those over any assumption. The work - build the planned customisations - (1) Ascot Real Estate brand system as brands/ascot-real-estate/brand-style.md from clients/ascot-re-2026/site/DESIGN.md in the pro-marketing-web-agency repo, using brands/_template.md as the schema; (2) iDD brand system from the recorded tokens (#052648 navy, #1EB5BD teal, #EFC319 gold, Montserrat); (3) house style guard in the shipping SKILL.md copy - no em or en dashes in generated copy, straight quotes, AU English for Pro Marketing clients and US for iDD; (4) motion guidance in the shipping copy routed to GSAP and The Motion Index (never scrollreveal). Each customisation = its own commit with the ledger diff quoted in the message. Bump plugin version to 0.2.0 at the end. Never push unasked. Verify the plugin still validates (`claude plugin validate .`) and the symlinks still resolve before calling anything done. House formatting rules apply to fork-authored files only - upstream files keep upstream style.
