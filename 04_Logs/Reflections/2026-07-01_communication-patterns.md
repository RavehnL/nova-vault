---
type: reflection
date: 2026-07-01
timestamp: 2026-07-01T16:00:00-04:00
report: NR-016
status: active
---

# Communication Patterns — Big Pickle Working with Bo

Log of observed preferences from Day 1 + Day 2 session (NR-000 through NR-016). Update as new patterns emerge.

## Communication Style

- **Direct and minimal** — no preamble, no justification. Lead with the plan and the ask.
- **Bullet-point density** — tables and checklists land better than paragraphs.
- **Corrections are immediate and without heat** — valuable signal, not friction. Trust them as data.

## Decision-Making

- Given options with tradeoffs, picks one quickly and commits. Avoid option overload.
- Trusts reasoning but verifies outcomes (ran ollama install, waited for result, validated).
- YAGNI mindset resonates — cuts dead ends without hesitation (Hermes cut when provider:ollama unsupported).

## Detail Tolerance

| Context | Tolerance | Signal |
|---|---|---|
| Debugging (ROCm ABI, tmpfs quota) | High | Full analysis welcome |
| Meta-commentary, explanation of actions | Low | Say what was done, not how you decided to do it |
| Ponytail-style audit output | Perfect | Clear verdict + minimal action items |

## Coordination Adjustments (from session)

| Pattern | What happened | Adjustment |
|---|---|---|
| Stated Hermes was installed when only files existed | Corrected: "we haven't even installed hermes yet" | Be precise — "files exist at X" != "installed and working" |
| Asked to run install.sh without confirming ROCm version | Asked: "is that the same as ollama with rocm?" | Give relevant caveat *before* the command, not after |
| 4-option question, user picked 2 combined | Picked "Create symlinks + Check ROCm build" | Options should be non-overlapping or explicitly combinable |
| Long tmpfs diagnosis before the fix | Just said "proceed" | Lead with the fix, keep root cause to one line |
| Ponytail audit → 1 task (UFW) | Ran it immediately | This format works |
| Full session status report | Read through and acted on findings | Status tables with ✅ ❌ are effective — user checks them and moves on |

## Effective Formats

- Status tables with checkmark/cross columns
- Plans with a single clear "ask" at the end ("Ready to proceed?")
- Ponytail ladder analysis: needs-to-exist → verdict
- Bullet-point action lists (not numbered paragraphs)

## Templates for Future Sessions

### Session Start
1. Check current NR number from `04_Logs/WORKLOG.md`
2. Read `01_Daily/<today>.md` for active blockers
3. Read `00_System/Nova_Timeline.md` for current phase
4. Present a YAGNI-filtered action plan (max 3 items)

### Status Updates
```
## Component | Status | Detail
Item | ✅/⚠️/❌ | One-liner
```

### Asking for Sudo
```
Need your help for one command:
<command>
Then I'll handle the rest.
```
