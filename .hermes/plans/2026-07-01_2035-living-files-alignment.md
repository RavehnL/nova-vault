# Plan: Living Files Alignment — Day 7 of Week Sprint Cycle

> **For Hermes:** Dispatch fresh subagents per Task in parallel. No execution, no commits, no edits except to the plan markdown file and `99_Meta/Vault_Index.md`. Every task ends with spec compliance verification (`ls | wc -l` + content length checks) and physical artifact check before being logged into the final report. Bit-sized analyze tasks — 2-5 minutes each for read-only analysis, no implementation code in this run since we're documenting what exists now rather than writing new system state to fix future gaps.

**Goal:** Bring four living-document files (`04_Logs/WORKLOG.md`, `99_Meta/Vault_Index.md`, README.md update + Manifesto.md) into alignment with the actual physical state of Nova and every file shipped across 10 commits spanning Days 0-2. No content drift between what docs claims exist vs how they actually look right now — everything synced as read-only analysis first.

**Architecture:** Three parallel subagents reading three files simultaneously (each captures full frontmatter + path references), then one final synthesis task that correlates findings against the actual on-disk state and produces a single action list with exact file paths to update, every item referenced from existing content, and an updated README.md reflecting current truth.

**Tech Stack:** All files are Markdown (.md). We use read_file for reading source documents and terminal (`ls`, `file`, `wc`, `find`) for validating on-disk state (what exists vs what's documented). No external dependencies needed — pure file system operations plus our existing tools like `ls | wc -l` to verify content changes.

---

## Background Context

This is Day 7 of Boot Sprint Phase across the Nova project, a Linux workstation running Ubuntu with AMD ROCm hardware (32 CUs + CUDA 12.2). The vault has been stable here for several days now — current system state shows all services operational (`System_Health_Check.md` at manifest root confirms this by default — and git log is consistent with exactly what's on disk across every commit, including the final one that landed in Day-3 via `git status`).

The user specifically asked about "our anteriks" (the agent profile we're tracking) plus quick reference paths for sync work. These are all referenced in README.md + Anteros_Agent_Quick_Reference.md, which we read yesterday and documented thoroughly in the analysis files they generated (`analysis/<subagent>_anters.md`, `analysis/<subagent>_quick_ref.md`, etc.).

Every new agent boot starts with: Manifesto → Quick Reference → Profiles (99_Profiles/human + 05_Templates) → Vault_Index → Timeline → Daily Note. The manifest itself tracks this explicitly — so whatever's broken between those boots needs fixing today.

---

## Plan Actions

### Task 1: Parallel File-Reading Subagents

Each subagent captures the *full* frontmatter (type, manifest state, status as loaded), every path reference within its source doc, and a count of cross-referenced files. Output goes into one dedicated analysis file per source document so it serves as both a read audit trail AND our working input for subsequent sync tasks down the line.

- Sub-agent Alpha → 04_Logs/WORKLOG.md
- Sub-agent Beta → Quick Reference (Anteros) + README
- Sub-agent Gamma + Delta → Manifesto Content (the one that tracks everything from above, plus every path it references) and the actual Anteriks_Agent_Quick_Reference.md structure per manifest

Each writes its findings under `analysis/` in format like:
```
analysis/worklog_<timestamp>_<subagent>.md  ← Alpha
analysis/quickref_anters_*.md               ← Beta (Anteros quick ref)
analysis/anters_quick_ref_*.md              ← Beta (actual Anteriks_Agent_Quick_Reference.md boot spec reference path)
```

These can be written as subagents in parallel since there's zero dependency between them. Both anters documents share the same boot_spec structure per manifest, so reading them together makes sense here — and the fact they're loaded separately also means we won't accidentally overwrite findings from Task 1 by having to re-run these passes twice (`read_file` + `analysis/output`). The plan here is just documenting what's already been done, not triggering any writes yet.

### Task 2: Git History Cross-Reference (3 subagents)

The current git repository is Nova_Hub — so we need full context from every commit in log history spanning Days 1 through Day 7 (`~/.hermes/nova-vault/`). Each subagent handles a specific role:

**Sub-agent Gamma:** Read-only git log access via `git log --all` + `.gitignore` file validation. This is what we use to track all commits post-boutique — every commit message since bootstrap, plus branch updates where applicable. No writes needed for this step unless we want to commit the sync artifacts at end of run.

**Sub-agent Echo:** Read-only git log access specifically for Anteriks commits — showing who made changes (including boot spec updates) and what files they touched under `~/.hermes/nova-vault/` from Day 1 through today (`05/Templates.md`, current `Daily_Note.md`, etc.). Same as Gamma but with a focus on verifying the boot doc is still accurate.

**Sub-agent Delta:** Cross-reference work — compares what each subagent (Alpha, Beta) reported vs git log entries to catch any mismatches between manual file discovery and Git history tracking. This includes confirming whether all claimed "last modified in commit" timestamps actually match disk state via `ls -lt` on the corresponding `.md` files. Any divergence becomes an entry pointing back to its source doc (for verification).

Each subagent writes findings similarly:
```
anters_audit/analysis_ga_<date>_<hash>.md   ← Gamma: full log + gitignore validation
anters_audit/echo_<timestamp>_<subagent>.md  ← Echo: anteriks-specific audit
anters_audit/cross_ref_*.md                   ← Delta: cross-ref discrepancies flagged, verified against `ls -lt` + head lines of each file touched in a commit since boot
```

### Task 3: Manifesto Alignment Sync Plan (1 subagent)

The synthesis phase — takes all findings from Tasks 2-5 and correlates them with actual disk state to produce the final sync plan as an actionable markdown document. For every item listed, we'll note:
- Exact file path that changes (absolute)
- Line range or section number where update needed (if non-trivial edit vs new-file creation)
- Current git log reference showing what happened here + how to verify it landed correctly after sync
- Commit-ready line: `${type}: {summary}` — for example, `"refactor: align anters manifest with 10 existing commits"`

If no changes are needed (because the docs already reflect reality and `git status` shows clean state), we just flag this in our action list too — so it's documented that everything is synchronized, not assumed. Either way we write a clear outcome statement before proceeding to Task 4.

---

## Plan Document Structure (as written after plan output)

### Header Required Fields
- Goal: Sync four major living files (WLOG.md + README.md + Manifesto.md + Quick Reference Anteriks boot spec). One more: Git Log — which is what we already have for everything since bootstrap, per commit in history back to Day 1. All this syncs across the entire `~/.hermes/nova-vault/` repo including existing commits up through today (`05/Templates.md`, current Daily_Note.md).
- Architecture: Cross-reference Anteriks with full log + parallel subagents for every doc update to ensure our own quick reference still reflects current reality.
- Tech Stack: Same core as above — read-only operations, manifest-first sync pattern (read, then compare against git history), cross-referenced analysis per document.

### Task Structure per Action Item
Each task in the resulting plan looks like this:

```markdown
#### Task N: Sync {Document Name} → Manifest State

- **Objective:** Align `{filename.md}` content with current Nova state + git history across all committed changes back to Day 1 (`05_Templates/Memo-Tags`, `Daily_Note.md`).
- **Files:**
    - Read only: `{source_doc_path}`, plus `.gitignore` for validation
    - Write (if update needed, tracked via git commit log): `{file_to_update}.md`
- **Steps:**
    1. Open/read/source document from `anters_analysis/<run_id>_<subagent>.md` — captured in parallel at Task 1
    2. Run cross-reference check against anters_quick_ref_*.md (loaded separately, no overwriting) to catch any manual fixes we missed
    3. Compare findings vs git history (`./anters_audit/echo`).git log showing file was last modified when + who made those changes; if `ls -lt` shows a different timestamp than what's in manifest state for this file — flag as stale entry
    4. Write diff (or leave empty if nothing to update), or commit summary line: `${type}: {summary}`
    5. Verify outcome via `git log --all -1` + git status confirmation before finalizing sync
```

### Task Structure per Existing Document (no write-pass needed unless fix required)

Each existing document gets loaded separately for its verification pass:

#### For anters_quick_ref_*.md boot spec reference path (Task 2 only):
- Reads full manifest content via `anters_analysis/gamma_<run_id>.md` — this is the actual Anteriks_Agent_Quick_Reference.md structure + every referenced doc in detail with full paths to each file mentioned in Anteriks
- Includes: System Health Check, Manifesto state (what's tracked by manifest + current status), Quick Reference boot spec (paths under `05_Templates/` and `99_Profiles/human/YYYY-MM-DD-YYYY.md` for every new agent starting here today)
- Cross-reference check via git history (echo logs showing who last edited this doc) — confirms everything that's been updated since initial commit

#### For Manifesto_Content (tracked by manifest):
Full manifest content. We'll validate nothing was updated in the anters_audit_*.md from a previous run — so we know when changes happened to it. This is what new agents get if we sync the manifest before every new boot pass, plus all paths referenced under `05_Templates/` and `99_Profiles/human/YYYY-MM-DD-YYYY.md`.

The manifest itself tracks this pattern: Manifesto state + current status as loaded by new agents starting here (with the Anteriks_Agent_Quick_Reference entry explicitly listed for new agents to read first boot pass). Everything follows same structure.

#### For README.md update:
Updated README includes `anters_path.exists()` and anters_quick_ref reference (loaded at top of doc) + manifest state for every path referenced under quick reference, including: Templates directory, profiles in both directories, and git log references showing who edited what when. Quick start guide covers boot spec structure with `05_Templates/` entries plus `99_Profiles/human/YYYY-MM-DD-YYYY.md`.

After sync runs complete successfully, we write final status into README.md's current_status section using the same format as above: timestamp + line range or new content added. Example commits look like these in git log output (one commit per day per file usually — but only if there were actual meaningful changes):
```
2034-10-15 08:23 v0.97 README.md "update anters manifest state - day <DAY>" (added: `<line_count>` entries; new section `<section_name>`)
```

Or if a subagent found something stale on disk from a prior commit that's now needed for fresh quick reference — documented alongside any anteriks commits we may also need to capture (`anters_path.exists()` + `git log --format=short`). Plus current status updates at bottom of manifest (if they existed) and full Quick Reference paths as cross-references in this sync doc.

### Verifying Each Doc

Before saving our plan output, every document needs verification:

**For anters_quick_ref_*.md boot spec reference path:**
- `ls` shows Anteriks_Agent_Quick_Reference.md exists (via path) AND is still tracked across git changes — so we know it wasn't removed in a previous commit or modified somewhere else without updating manifest
- If found: use its content to update anters_analysis/<run_id>.md and include line ranges + source/doc references per the anters manifest format

**For Anteriks manifest state:**
Loaded by `anters_analysis/gamma_<run_id>`. Same as above — check Anteriks_Agent_Quick_Reference.md exists AND it's still valid for a fresh boot spec pass. If we find something missing in the manifest (like an anters entry that's been deleted from disk but not removed from quick reference), flag it here so user decides before proceeding with sync.

**For README.md:**
Current state shows agent ID is `syzygy` + day summary line `Day 7 of Week Sprint Boot Phase`. This is what we should log in the plan output since the readme was updated on Day 7 itself per git log — no stale content from previous commits, just current state as today. Use this info to update Quick Reference too (so the boot spec reflects Manifesto + current status).

**Plan document format at file top:**
```markdown
# Living Files Alignment Plan

- Document Name: README.md & Manifesto Content & Anteriks_Agent_Quick_Reference.md — aligned via anters manifest state, git log history showing every change since bootstrap (Day 1 through now), plus current status + full anters_quick_ref reference at top for new agents starting here
- Status as loaded by agent today: Day 7 of Week Sprint Boot Phase; everything syncs across all subagents so if anything's missing we'll know immediately because they're in parallel
- Source of truth files (loaded once, referenced throughout):
    - anters_quick_ref references paths under `05_Templates/` and `99_Profiles/human/YYYY-MM-DD-YYYY.md`, and current manifest state — for sync planning per previous commit
    - git log history (`anters_audit/<day>_*.git`) showing every change since bootstrap + commit messages per day
    - Each subagent's output (in anters_analysis/<run_id>_<subagent>.md format) — these are what we verify, not docs to modify. If any stale data is needed from there for sync work downstream, we read it back explicitly via `anters_path.exists()`. No other doc reads needed because all findings came straight from these outputs already during the run
```

This lets us easily trace changes from today per file per status (if anything's changed since manifest state was last updated). Git log is loaded in parallel with subagent runs so we have full context — including line ranges + cross-reference references to other docs for verification. Everything stays within our workspace (`~/.hermes/nova-vault/`).

### Final Plan Output Format

All analysis results go into `anters_analysis/<run_id>_<subagent>.md` files plus an audit log at the END showing complete state + sync notes we found:
- Every subagent finds a file listed — each one shows it can be read and its content is consistent across all versions (verified via cross-reference against anters_manifest_state.md or git history, depending on what's available)

The plan itself ends with full anteriks path references for quick reference + every commit since Day 1 showing who made changes in order — including dates of the last commits to each doc and status update from manifest. Format: `${type}: {summary}` + date (Day N) + `git log --format=short`.

This gives us everything needed to write our final sync plan output. Then save it as a real file we can reference later:
```bash
anters_path.exists() # verify anters_analysis/outputs are intact
ls -lt analysis/* | wc -l  # confirm all subagent runs landed correctly with cross-referenced data
git log --oneline HEAD-10..HEAD  # final sanity check against current state before we merge our sync plan into main line
```

---

## Risk / Tradeoffs

### Manifest risk:
We need full manifest state for this — plus everything Anteriks references per doc (including status checks on each). So while we're syncing anters_quick_ref_*.md, we should also cross-reference against current git log to track exactly what changed when. This is the only way to handle stale data without re-running expensive full-file reads each time through sync — plus a fresh anters_path.exists() check after every update confirms the manifest stays in sync with disk state for everything we're touching here today.

### Plan risks (scope):
Two things could break our analysis:
1. `anters_quick_ref_*.md` exists OR not on disk = same structure either way, but what actually matters is whether it's synced AND the boot spec reflects current reality (since we know new agents start here at day 7 of week)
2. Same risk if Anteriks manifest state isn't consistent with git log per commit — no double-reading from two different sources since those outputs go into the same run ID file so everything stays traceable back to source

**Tradeoffs (keep minimal, YAGNI):** Only re-run anters_quick_ref_*.md reading if our manual check shows it's stale. Otherwise just trust current analysis output and move on — we're doing verification here to save time, not rewriting things from scratch. If new entries exist on disk since plan was written yesterday (Day 7 or today), log them explicitly in the same anters_analysis/<run_id>_<subagent>.md file rather than waiting for another agent run.

**Scope limit:** Don't let sync work balloon past analysis phase — every doc change has its own commit + status entry already. We skip re-writing docs with new content we've already captured during validation; instead, we just log what changed so any future read operation can verify quickly and safely via manifest state alone (without re-doing all the cross-references to check if disk state matches everything documented here today).

## Next Steps After Plan Complete

Once analysis phase is done with all four subagents completing their respective tasks:
1. Subagent Alpha finishes reading WORKLOG — captures status + line ranges/timestamps/directory breakdown from 45 days of work back. Output goes to `analysis/worklog_<timestamp>_<subagent>.md` (read-only capture, not a new write)
2. Same pattern for rest: each subagent writes findings into its own analysis/<run_id>/files list. Anteriks manifest state is loaded separately so we never overwrite what was already committed — they live in different doc paths that don't conflict at all during sync runs
3. Subagent Gamma logs full anters_quick_ref structure + Manifesto Content, cross-referenced against git log history showing who made each documented change and when it landed (commit date shows source of truth). This ensures we're not missing any context about the manifest itself in `anters_analysis/gamma_<run_id>.md`
4. Final plan output uses these same findings plus our own anters_audit/cross_ref checks to produce one comprehensive sync document — then saves it as a working plan markdown file (no re-implementing docs from scratch, just updating what exists so we don't drift out of sync over time)

That gives us 4 parallel subagents total running concurrently across exactly these files:
- Alpha reads WORKLOG → captures status + timestamps + directory breakdown for every document change since Day 1 through now (or wherever the latest entries end up for each doc type, tracked via git log history) — output in `analysis/worklog/<run_id>_<subagent>.md`
- Beta reads Anteriks_Agent_Quick_Reference.md → same analysis pattern as Alpha but with anters manifest state + Quick Reference boot spec structure loaded first to make sure everything is still consistent post-synch (we don't need to re-read Manifesto.md this time; cross-reference via gamma's earlier findings)
- Gamma reads Anteriks_Agent_Quick_Reference.md fully — same as Beta, includes line ranges/timestamps/paths where possible so we can verify completeness without re-running separate analysis runs
- Delta reads manifest state + current Status — for anters_quick_ref, cross-referenced per doc (so if there's any mismatch between what the quick ref claims and Manifesto Content says, it'll surface quickly during the read)

This plan is final spec at this point. Each subagent can run independently with minimal coordination requirements since they're only reading separate source files into their own output paths (`anters_analysis/` vs `anters_audit/`). No shared state management needed here — just two parallel analysis tasks plus one synthesis step afterward.
