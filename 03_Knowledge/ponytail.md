---
type: skill_reference
tool: ponytail
date: 2026-07-01
status: active
version: 4.8.4
source: https://github.com/DietrichGebert/ponytail
---

# Ponytail — Lazy Senior Dev Skill

"The best code is the code you never wrote."

## What It Is

A YAGNI-first ruleset that makes the agent think like a lazy senior dev. Before writing code, it climbs a ladder:

1. Does this need to exist? → no: skip it (YAGNI)
2. Already in this codebase? → reuse it, don't rewrite
3. Stdlib does it? → use it
4. Native platform feature? → use it
5. Installed dependency? → use it
6. One line? → one line
7. Only then: the minimum that works

## Commands

| Command | What It Does |
|---|---|
| `/ponytail [lite/full/ultra/off]` | Set intensity or toggle off |
| `/ponytail-review` | Review current diff for over-engineering |
| `/ponytail-audit` | Audit whole repo for over-engineering |
| `/ponytail-debt` | Harvest deferred shortcuts into a ledger |
| `/ponytail-gain` | Show measured impact scoreboard |
| `/ponytail-help` | Quick reference |

## Key Rules

- No abstractions not explicitly requested
- No new dependency if avoidable
- No boilerplate nobody asked for
- Deletion over addition. Boring over clever. Fewest files possible.
- Shortest working diff wins (after understanding the problem)
- Bug fix = fix the root cause once, not each symptom
- Mark intentional simplifications with `ponytail:` comments naming the ceiling and upgrade path
- Non-trivial logic leaves ONE runnable check behind

## Installation

Installed globally in OpenCode at `~/.config/opencode/opencode.jsonc` pointing to `~/.local/share/ponytail/`.

## Results (per benchmark)

- 54% less code (up to 94% on over-build traps)
- 22% fewer tokens
- 20% cheaper
- 27% faster
- 100% safety retained
