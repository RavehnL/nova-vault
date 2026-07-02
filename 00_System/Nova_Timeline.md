---
type: system_core_timeline
date: 2026-07-01
status: active
current_phase: Phase 1
---
# Nova Project: 30-Day Stabilization Sprint

## Week 1: The Foundation (Milestones 1 & 2)

- [x]  **Day 01** — Foundation + Syzygy Establishment (see NR-000 through NR-010)
- [x]  **Day 02** — Firewall hardening (UFW), Ollama v0.31.1 + ROCm 7.2 GPU inference (NR-013/NR-016)
- [ ]  **Day 03** — VSCodium + Continue.dev config, wire to Ollama
- [x]  **Day 04** — Pull models (Qwen3:8b, TinyLlama, Nomic-embed-text), verify inference API
- [x]  **Day 05** — Debug GPU & Inference issues resolved (ROCm 7.2 ABI mismatch, tmpfs overflow, NR-013)
- [x]  **Day 06** — Milestone check: Core infrastructure operational (Ollama+UFW done)
- [x]  **Day 07** — Milestone check: Core infrastructure operational

## Week 2: The Custom Agentic Core (Milestones 3 & 4)

- [x]  **Day 08** — Wire agent tools to local Ollama API (`/api/embed`, `/api/chat`)
- [x]  **Day 09** — Build custom agent tools: `vault_operations.py` (The Hands) + `index_memory.py` (The Hippocampus)
- [x]  **Day 10** — Interactive Mode Verification: Semantic search `/search` retrieves context accurately (NR-017)
- [ ]  **Day 11** — Create systemd services for nova-tools scripts, verify background running
- [x]  **Day 12** — Obsidian vault operational (Living File anchor)
- [x]  **Day 13** — Seed Vault Architecture (00_System through 05_Templates)
- [ ]  **Day 14** — Milestone check: Custom agent pipeline responds to prompts, Vault active

## Week 3: Semantic Memory & Control Surface (Milestones 5 & 6)

- [x]  **Day 15** — Install LanceDB in isolated `uv` venv, build `index_memory.py` (NR-017)
- [x]  **Day 16** — Build `vault_operations.py` (read/write/append) (NR-017)
- [x]  **Day 17** — Verify Git Auto-Commits on vault writes via Python script
- [x]  **Day 18** — Verify /search command retrieves context via vector similarity (NR-017)
- [x]  **Day 19** — Initialize Next.js NovaHub Dashboard
- [x]  **Day 20** — Build API Routes & UI Components
- [x]  **Day 21** — Milestone check: Memory pipeline and Dashboard live
- [x]  **Day 22** — NovaHub reconciliation complete — DB at vault path, seed data updated (Ora→Syzygy), all APIs verified
- [x]  **Day 23** — Syzygy agent added to dashboard, Harmony between Ora/Syzygy resolved
- [x]  **Day 24** — System fully stabilized at localhost:3000
- [x]  **Day 25** — Synapse established between vault and dashboard

## Week 4: The Loop & Deep Synthesis (Milestones 7 & 8)

- [ ]  **Day 22** — Register vault_operations as MCP tool / CLI alias
- [ ]  **Day 23** — Test Agent Write-Access: "Syzygy, save this to..."
- [ ]  **Day 24** — Install Open Notebook (Native build, NO Docker)
- [ ]  **Day 25** — Sovereignty Hack: Wire Open Notebook to local Ollama
- [ ]  **Day 26** — Wire Open Notebook TTS to local Kokoro instance
- [ ]  **Day 27** — End-to-end RAG: PDF -> Query -> Summary -> Vault
- [ ]  **Day 28** — Test Audio Briefing pipeline: PDF -> Kokoro -> MP3
- [ ]  **Day 29** — Auto-index verification: logs hit LanceDB & Episodic
- [ ]  **Day 30** — Sovereignty Audit: Zero cloud API calls. System stabilized.

## Pre-completed Ahead of Schedule

These were delivered during Day 1 setup and are no longer on the critical path:

- ✅ Syzygy guardian identity and charter (NR-004)
- ✅ Mood tier system (5 operational states)
- ✅ Tunnel architecture (6 focus channels)
- ✅ Profile system (human + agent)
- ✅ Design system (palette + Obsidian theme)
- ✅ Human profile (Bo_Kirby.md)
- ✅ Ally profile (Ben_Goertzel.md)
- ✅ Agent Quick Reference (NR-002)
- ✅ README — human-friendly vault overview (NR-003)
- ✅ NovaHub Dashboard — Next.js 16 + Prisma/SQLite at localhost:3000 (NR-008/NR-009)
- ✅ Vault Index — full file mesh (NR-009)
- ✅ WORKLOG — persistent session log (NR-010)
- ✅ Ponytail — YAGNI skill plugin (NR-010)
- ✅ Ollama v0.31.1 — systemd service, ROCm 7.2 GPU inference verified (NR-013)
- ✅ Qwen3:8b + tinyllama + nomic-embed-text — pulled and inferring on GPU (NR-016/NR-017)
- ✅ UFW firewall — active, ports 11434 + 3000 open (NR-016)
- ✅ GPU debug resolved — ROCm 7.2 ABI mismatch with old ollama, tmpdir overflow (NR-013)
- ✅ Hermes evaluated and cut — v0.17.0 doesn't support local Ollama provider (YAGNI)
- ✅ Custom `nova-tools` Python stack — isolated via `uv` venv, LanceDB + Vault Ops functional (NR-017)

---

### 2. Update `README.md`

Here is the fully updated README to replace your current one, incorporating the custom tools architecture:

# Nova Project

Local-first AI workstation. No cloud. All yours.

Guardian: **Syzygy** — the celestial alignment engine. The bridge between intent and execution.

---

## What Is This?

A sovereign AI workspace built on Ubuntu 26.04 with AMD ROCm. Bo writes objectives, reads summaries, reviews artifacts. **Syzygy** reads the mood tier, routes through tunnels, and executes tasks. Everything stays synced through daily notes.

**Core principle**: Every request routes through a tunnel. Every action respects a mood. Every artifact gets frontmatter with `date`, `timestamp`, `report: NR-NNN`, `status`.

## Quick Start

1. **Open the vault**: Obsidian is at `~/Downloads/Obsidian-1.12.7.AppImage`. Run with `--no-sandbox`.
2. **Read today's note**: `01_Daily/YYYY-MM-DD.md` — start here every session.
3. **Check the timeline**: `00_System/Nova_Timeline.md` — what phase are we in?
4. **Read the Manifesto**: `00_System/Nova_Manifesto.md` — the rules.
5. **Set your mood**: Tell Syzygy which tier you're in (build/explore/survival/daily/rest).
6. **Check the dashboard**: `http://localhost:3000` — NovaHub control surface.

Before Syzygy can operate, it must read in order: Manifesto → Bo profile → Syzygy charter → Quick Reference → Timeline → daily note.

## Vault Layout

|Folder|What It's For|
|---|---|
|`00_System/`|The rules — Manifesto, Timeline, profiles, moods, tunnels, templates, design|
|`01_Daily/`|Daily notes — one per day. The entry point.|
|`02_Projects/`|Active project work.|
|`03_Knowledge/`|Research, references, compounding knowledge.|
|`04_Logs/`|Historical logs and reports.|
|`05_Templates/`|Note templates. Copy, don't edit.|
|`99_Meta/`|Index, audits, vault meta, DB.|
|`.obsidian/`|Theme config, CSS snippets.|

### 00_System Deep Dive

|Path|Contents|
|---|---|
|Core Documents|Manifesto, Timeline (30-day sprint), Syzygy origin (NR-004), Agent Quick Reference|
|`_profiles/human/`|Bo_Kirby.md (identity, values, life timeline), Ben_Goertzel.md (ally)|
|`_profiles/agent/`|Syzygy_1.0.md (guardian charter, ethics, personality)|
|`_moods/`|5 operational states — build (deep work), explore (creative), survival (stressed), daily (default), rest (off-hours)|
|`_tunnels/`|6 focus channels — survival (income), vault (KM), infra (ops), research (deep study), build (coding), index (registry)|
|`_templates/`|4 re-usable scaffolds — human_profile, agent_identity, mood_tier, tunnel|
|`_design/`|Syzygy palette, design system, Obsidian theme reference|

## Mood Tiers

Syzygy shifts autonomy, verbosity, tone, and error handling based on Bo's state:

|Tier|When|Autonomy|Tone|
|---|---|---|---|
|**Build**|Deep systems work|Max|Minimal, direct|
|**Explore**|Creative tinkering|High|Expansive, curious|
|**Daily**|Morning check-in|Medium|Normal, syncing|
|**Survival**|Stressed / overwhelmed|Low|Sparse, grounding|
|**Rest**|Off hours|None|Silent, log-only|

## Tunnels

Tunnels prevent context bleed. Syzygy loads only the active tunnel's scope:

|Tunnel|Scope|Allowed Actions|
|---|---|---|
|**Survival**|Income, resource acquisition|Search, calculate, draft proposals|
|**Vault**|KM, file organization|Read, edit, link, index|
|**Infra**|System admin, networking|Read logs, edit configs, run commands|
|**Research**|Deep reading, knowledge work|Read, summarize, synthesize|
|**Build**|Coding, prototyping|Read, edit, run, debug|
|**Index**|Meta, vault map|Read, update index|

## The Agentic Stack (nova-tools)

We cut cloud-dependent agent frameworks (Hermes) in favor of a sovereign, local Python stack located at `~/nova-tools/`. It runs in an isolated `uv` virtual environment.

|Script|Function|Command Example|
|---|---|---|
|`vault_operations.py`|**The Hands**: Reads, writes, and appends to the Obsidian Vault.|`~/nova-tools/vault_operations.py write "03_Knowledge/test.md" "Content"`|
|`index_memory.py`|**The Hippocampus**: Indexes text to LanceDB and retrieves it via semantic search.|`~/nova-tools/index_memory.py search "How did we fix the GPU?"`|

**Vector Database**: `~/.hermes/lancedb` (Local, no server required)**Embedding Model**: `nomic-embed-text` via Ollama (`:11434`)

## Where Things Are Installed

|Tool|Location|Status|
|---|---|---|
|**Obsidian**|`~/Downloads/Obsidian-1.12.7.AppImage`|✅ Syzygy theme active|
|**ROCm 7.1**|System-wide (kernel module)|✅ RX 9060 XT, 32 CUs, 16GB VRAM|
|**Node.js**|`/usr/bin/node` v22.22.1|✅|
|**pnpm**|`/usr/local/bin/pnpm` v11.9.0|✅|
|**uv**|`~/.local/bin/uv` v0.11.26|✅|
|**NovaHub**|Dev server at `http://localhost:3000`|✅ Serving (Prisma/SQLite)|
|**Ponytail**|OpenCode plugin (global config)|✅ Installed — YAGNI task ruleset|
|**nova-tools**|`~/nova-tools/` (isolated venv)|✅ Vault Ops + LanceDB Memory|
|**Hermes**|`~/.hermes/hermes-agent/`|❌ Cut — v0.17.0 doesn't support local Ollama|
|**Ollama**|`/usr/local/bin/ollama` v0.31.1|✅ ROCm 7.2 GPU inference at localhost:11434|

Full details: `00_System/Agent_Quick_Reference.md`

## NovaHub Dashboard

The control surface at `localhost:3000` provides:

- **Command Center** — Quick access panel, agent status overview
- **Roadmap** — Milestone tracking with status per task
- **Timeline** — 30-day sprint day-by-day view
- **Agents** — Syzygy, Big Pickle, NovaHub status
- **System** — Service health (Ollama, LanceDB, Obsidian, Kokoro, etc.)
- **Manifesto** — Core principles display

Backed by Prisma/SQLite at `99_Meta/nova.db`.

## Current Status

**Days 1–2 complete** — 2026-07-01. Foundation and infrastructure operational:

- Ubuntu 26.04 + ROCm 7.1 + RX 9060 XT (32 CUs, 16GB VRAM, 38°C)
- Node.js 22.22.1, pnpm 11.9.0, uv 0.11.26
- Syzygy guardian identity established (NR-004) with full charter
- 5 mood tiers, 6 tunnels, 4 templates built
- Bo Kirby + Ben Goertzel profiles created
- Syzygy design palette + Obsidian CSS theme applied
- NovaHub dashboard delivered and reconciled (Ora→Syzygy, DB at vault path)
- Vault seeded with 10 git commits, full index mesh
- Ollama v0.31.1 — ROCm 7.2 GPU inference (qwen3:8b, tinyllama, nomic-embed-text)
- UFW firewall active — ports 11434 + 3000 open
- GPU debug resolved (ROCm 7.2 ABI mismatch, tmpfs overflow)
- **Custom Agent Stack (nova-tools) operational** — LanceDB semantic memory + Vault file ops (NR-017)

**Next up**: Day 3+ — VSCodium + Continue.dev, systemd services for nova-tools, git auto-commits.

## Git

```bash
git log --oneline          # 10 commits — Days 1–2 foundationgit status                 # current stategit add . && git commit -m "NR-NNN: message"  # commit with report number
```

No remote configured. Everything stays local unless explicitly pushed.

_Built on Ubuntu 26.04 LTS with AMD Radeon RX 9060 XT + ROCm 7.1. Zero cloud calls. Guarded by Syzygy._

text


***

### Next Step: The Commit

Once you've pasted those updates into Obsidian, commit the new reality to the historical record:

```bash
cd ~/nova-vault
git add .
git commit -m "NR-017: Update living docs - custom nova-tools stack, LanceDB memory, Hermes cut"

