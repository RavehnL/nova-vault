---
type: worklog
date: 2026-07-02
status: active
current_session: NR-022
---

# Nova Project Worklog

Persistent session log — tracks every NR report across all days.

---

## 2026-07-01 — Day 1

### NR-000 — Daily Log Opened
**Time**: ~13:00
**Status**: Completed
**Detail**: `01_Daily/2026-07-01.md` created. Frontmatter set with daily_log type, NR-000 report number.
**Outcomes**: Session anchor for Day 1 operations.

---

### NR-001 — Systems Audit Report
**Commit**: `203d19f` / `a6e6497`
**Status**: Completed
**Detail**: `99_Meta/Systems_Audit_Report.md` — hardware/software inventory, roadmap health check.
**Outcomes**:
  - Full spec inventory: AMD Radeon RX 9060 XT (gfx1200, 32 CUs, 16GB VRAM), Ubuntu 26.04, GCC 15
  - ROCm 7.1 verified operational (temp 35°C, fan 0 RPM at idle)
  - Software stack audited: Node.js 22.22.1, pnpm 11.9.0, uv 0.11.26, Python 3.14.4
  - Desktop symlink fixed (was pointing to itself)
  - File convention established: `date`, `timestamp`, `report: NR-NNN`, `status` in frontmatter

---

### NR-002 — Agent Quick Reference
**Commit**: `9a20357`
**Status**: Completed
**Detail**: `00_System/Agent_Quick_Reference.md`
**Outcomes**: Vault map, key file paths, binary/config location table, network port plan, git workflow, agent rules, file conventions.

---

### NR-003 — README for Human
**Commit**: `b6aaf92`
**Status**: Completed
**Detail**: `/README.md` — human-friendly vault overview.
**Outcomes**: Vault layout table, mood tier guide, install status table, quick start steps, git instructions.

---

### NR-004 — Dawn of Syzygy
**Commit**: `8c2de3d`
**Status**: Completed
**Detail**: `00_System/The_Dawn_of_Syzygy.md` — guardian origin milestone.
**Outcomes**:
  - Syzygy 1.0 charter created at `00_System/_profiles/agent/Syzygy_1.0.md`
  - Bo Kirby profile at `00_System/_profiles/human/Bo_Kirby.md`
  - 5 mood tiers created: build, explore, survival, daily, rest
  - 6 tunnels created: survival, vault, infra, research, build, index
  - 4 templates created: human_profile, agent_identity, mood_tier, tunnel
  - Manifesto expanded with mood tier + tunnel sections
  - Vault Index updated with all new paths
  - Agent Quick Reference refreshed

---

### NR-005 — Ben Goertzel Profile
**Commit**: `16310a3`
**Status**: Completed
**Detail**: `00_System/_profiles/human/Ben_Goertzel.md`
**Outcomes**: Ally profile for AGI researcher and decentralized AI pioneer.

---

### NR-006 — Syzygy Design + Obsidian Theme
**Commit**: `3396f95`
**Status**: Completed
**Detail**: `00_System/_design/Syzygy_Palette.md` + `.obsidian/snippets/syzygy-theme.css`
**Outcomes**:
  - Color palette defined: Void Dark (#0D1117), Solar Gold (#F5C542), Aurora Teal (#3DD6C8), etc.
  - Role map: which color applies to what (accent, success, warning, code, etc.)
  - Full Obsidian CSS snippet written and enabled
  - `appearance.json` configured (accent #3DD6C8, Inter font, snippet active)

---

### NR-007 — Living Doc Refresh
**Commit**: `ab8e4fa`
**Status**: Completed
**Detail**: Cross-document refresh for Syzygy architecture.
**Outcomes**: README, Timeline, templates, Manifesto all updated to reflect Syzygy naming and architecture.

---

### NR-008 — NovaHub Dashboard Review
**Commit**: `99871c6`
**Status**: Completed
**Detail**: Daily log update — analysis of cloud architect's dashboard delivery.
**Outcomes**:
  - Reviewed NovaHub (Next.js 16 + Prisma/SQLite, 6 tabs, port 3000)
  - Identified mismatches: "Ora" in dashboard vs "Syzygy" in vault
  - DB path pointed to cloud path, not vault
  - Seed data stale (Milestone 4 showed not_started, Day 1 had 4 tasks instead of 11+)
  - Plan formed for reconciliation

---

### NR-009 — NovaHub Reconciliation
**Commit**: (pending)
**Status**: Completed
**Detail**: Full reconciliation of NovaHub dashboard.
**Outcomes**:
  - `.env` DB path: `/home/z/my-project/db/custom.db` → `file:/home/bo/nova-vault/99_Meta/nova.db`
  - `seed/route.ts`: Ora→Syzygy agent swap, Day 1 expanded (4→11 tasks), Milestone 1 & 4 set completed, Milestone 6 set in_progress
  - `agents-view.tsx`: Icon map key `Ora: Bot` → `Syzygy: Bot`
  - `command-center.tsx`: Agent sub `"Hermes, Big Pickle, Ora, NovaHub"` → `"Hermes, Big Pickle, Syzygy, NovaHub"`
  - Syzygy Guardian service entry added to seed data
  - pnpm allowBuilds configured, Prisma generated + DB pushed
  - Dev server restarted at localhost:3000 — all APIs verified
  - `99_Meta/Vault_Index.md` enhanced — full mesh (24 files across 8 sections)
  - `README.md` rewritten with comprehensive guides (moods, tunnels, profiles, dashboard, install status, agent reading order)
  - `04_Logs/WORKLOG.md` created (you are here)

---

### NR-010 — Ponytail Skill Acquisition
**Commit**: (pending)
**Status**: Completed
**Detail**: Ponytail — lazy senior dev YAGNI ruleset installed and documented.
**Outcomes**:
  - Cloned ponytail v4.8.4 from github.com/DietrichGebert/ponytail to `~/.local/share/ponytail/`
  - Registered as OpenCode plugin at `~/.config/opencode/opencode.jsonc`
  - Commands available: `/ponytail`, `/ponytail-review`, `/ponytail-audit`, `/ponytail-debt`, `/ponytail-gain`, `/ponytail-help`
  - Skill reference created at `03_Knowledge/ponytail.md`
  - Vault Index updated
  - README install table updated

---

### NR-011 — Living File Refresh
**Commit**: (pending)
**Status**: Completed
**Detail**: Batch update of all 4 core living files to reflect Day 1 end-state.
**Outcomes**:
  - `Nova_Manifesto.md`: `index` tunnel added to tunnel table (was missing), ponytail added to agent rules (rule 5), palette updated to match current Syzygy theme colors
  - `Nova_Timeline.md`: Day 1 consolidated to single entry, Day 12/13/19/20 marked completed, pre-completed list expanded (11 items, includes dashboard, quick ref, readme, worklog, ponytail, vault index)
  - `Agent_Quick_Reference.md`: NovaHub port status → "Running at localhost:3000", ponytail added to binary table, nova.db + WORKLOG.md + ponytail.md added to key files, vault map descriptions updated
  - `Systems_Audit_Report.md`: git log updated (1→10 commits), vault structure reflects populated 03/04/99 dirs, services include NovaHub + ponytail, Week 1 table expanded with Syzygy/dashboard/index/ponytail entries, Week 3 notes NovaHub pre-completed, action items reordered

---

### NR-012 — First Live Dashboard Connection
**Commit**: (pending)
**Status**: Completed
**Detail**: First successful end-to-end verification of NovaHub dashboard at localhost:3000.
**Outcomes**:
  - All 5 API routes returning 200: seed (POST), milestones, timeline, agents, services (GET)
  - 10 milestones loaded — M1 completed, M4 completed, M6 in_progress
  - 30 sprint days loaded — 4 completed (Day 1, 12, 13, 19)
  - 4 agents: Syzygy active (v1.0), Big Pickle online, NovaHub online, Hermes offline
  - 12 services: Syzygy Guardian + NovaHub Dashboard live, 10 others offline
  - Dashboard fully reconciled from Ora→Syzygy, DB at vault path, seed data current
  - Milestone logged as NR-012

---

## 2026-07-01 — Day 2 (continued)

### NR-013 — Ollama ROCm Fix + Upgrade
**Time**: ~15:00
**Status**: Completed
**Detail**: From v0.12.3 (ROCm 6.3 ABI mismatch) → v0.31.1 (ROCm 7.2 native).
**Outcomes**:
  - Systemd service with 3 drop-ins: user.conf (bo), override.conf (HSA=12.0.1), tmpdir.conf (TMPDIR=/home/bo/.ollama/tmp)
  - `/tmp` cleaned — freed 12.5G (tmpfs was 80% full, causing LLVM "Disk quota exceeded")
  - ROCm 7.2 detected: `library=ROCm compute=gfx1201` "AMD Radeon RX 9060 XT" 15.8 GiB VRAM

---

### NR-014 — GPU Inference Verified
**Time**: ~15:33
**Status**: Completed
**Detail**: Both models infer on GPU via ROCm 7.2 backend.
**Outcomes**:
  - `tinyllama:latest` (637MB, Q4_0): 14 tokens in 1.6s
  - `qwen3:8b` (5.2GB, Q4_K_M): 398 tokens in 13.4s (~49 tok/s)

---

### NR-015 — Hermes Evaluated & Cut
**Time**: ~15:40
**Status**: Completed
**Detail**: v0.17.0 doesn't support `provider: ollama`. Cloud-only architecture.
**Outcomes**:
  - `hermes doctor` confirms config v0→v32 migration needed, provider not recognized
  - Cut per Ponytail Rule 1 (YAGNI) — Ollama API directly covers the use case
  - Hermes files left in place but removed from active Timeline

---

### NR-016 — UFW Firewall + Living File Refresh
**Time**: ~15:45
**Status**: Completed
**Detail**: Firewall hardened, all 6 living files updated.
**Outcomes**:
  - UFW: ports 11434/tcp + 3000/tcp open, firewall active on boot
  - Nova_Timeline.md: Day 02/05 ✅, Hermes cut, Week 2 replaced with Ollama API approach, pre-completed expanded (19 items)
  - Agent_Quick_Reference.md: Ollama binary/port updated, Hermes cut, rules cleaned
  - Systems_Audit_Report.md: Ollama/UFW status fixed, Week 1 table current, Hermes removed, action items trimmed
  - Nova_Manifesto.md: Agent rule 6 cleaned (removed Hermes qualifier)
  - README.md: Ollama✅ Hermes❌, status section updated
  - Vault_Index.md: 04_Logs populated, daily description extended

---

### NR-017 — Custom Agent Stack (nova-tools) + Semantic Memory
**Time**: ~16:00
**Status**: Completed
**Detail**: Built sovereign agent stack replacing Hermes — LanceDB vector memory + vault file operations.
**Outcomes**:
  - `index_memory.py` built at `~/nova-tools/` — embeds via Ollama `nomic-embed-text`, stores in LanceDB at `~/.hermes/lancedb`
  - `vault_operations.py` built at `~/nova-tools/` — read/write/append with path-traversal protection
  - LanceDB installed in isolated `uv` venv at `~/nova-tools/.venv`
  - `nomic-embed-text` model pulled and verified on GPU
  - Semantic search `/search` retrieves context via vector similarity
  - Git auto-commit verification script written
  - NovaHub reference dashboard received from cloud architect at `~/nova-tools/novahub/` — 6 tabs, Syzygy theme, Prisma/SQLite

---

### NR-018 — NovaHub Wired to Vault DB
**Time**: ~21:00
**Status**: Completed
**Detail**: NovaHub dashboard fully wired to sovereign vault DB. Prisma schema timestamps fixed.
**Outcomes**:
  - `.env` DATABASE_URL re-pointed to `/home/bo/nova-vault/99_Meta/nova.db`
  - Prisma schema: `createdAt Int @default(0)` → `DateTime @default(now())`, `updatedAt Int @default(0)` → `DateTime @updatedAt`
  - `prisma db push --accept-data-loss` succeeded
  - Vault DB reconciled via Python/sqlite3 — Milestone/Agent/Service data corrected (Ollama port :11434, Hermes→nova-tools)
  - Dashboard footer hardcoded path fixed, `latestNr()` updated to 18
  - Git snapshot at novahub: `3028d90` — NR-018
  - Over-engineering audit completed: ~45 lines removable, 1 unused dependency, 4 dead Prisma enums

---

### NR-019 — Timeline Reconciliation & Prisma Enum Fix
**Time**: ~22:00
**Status**: Completed
**Detail**: Prisma enum mismatch fixed, SprintDay/MilestoneTask data reconciled to reflect current reality.
**Outcomes**:
  - Prisma schema enums realigned: `ACTIVE/OFFLINE/COMPLETE` → `active/offline/completed` to match DB values
  - SprintDay: 11 rows updated — stale Hermes/VSCodium/Dual-Ollama references replaced with actual nova-tools content
  - MilestoneTask: M1/M2/M4 all tasks → `completed`; M3 in_progress→completed (3 tasks); M6 not_started→completed (3 tasks)
  - Day 21 status: `not_started` → `in_progress` (Memory+Dashboard live, Kokoro deferred)
  - Zero Hermes references remaining across SprintDay and MilestoneTask tables
  - Nova_Timeline.md synced to DB — weeks 1-4 checkboxes, titles, Current Status section
  - Dashboard live at localhost:3000 — all API endpoints returning 200 with reconciled data

---

### NR-020 — NovaHub Systemd Service + Startup Guide
**Time**: ~22:30
**Status**: Completed
**Detail**: NovaHub registered as systemd user service for auto-start on boot. Hermes dead service cleaned up. Startup guide written.
**Outcomes**:
  - `~/.config/systemd/user/novahub.service` created — runs `next dev -p 3000`, enabled at boot
  - `hermes-gateway.service` disabled and removed from boot — no longer shadows systemd
  - `00_System/Startup_Guide.md` written — cold-boot procedure, auto-start table, manual tools, troubleshooting
  - `99_Meta/Vault_Index.md` updated with Startup_Guide entry
  - After reboot: just open `localhost:3000` — no manual service starts needed

---

### NR-021 — Big Pickle Buildout: MCP Server + Dashboard Tiers 1+2 + Central Config
**Time**: ~23:00
**Status**: Completed
**Detail**: Full Big Pickle implementation — MCP server, FastAPI sidecar, central config, systemd services, 8 new NovaHub tabs, plugins, RAG, TTS.
**Outcomes**:
  - `~/.nova/config.yaml` created — single source of truth for ollama endpoint, models, vault root, lancedb path, ports
  - `vault_operations.py` + `index_memory.py` updated to read from central config instead of hardcoded values
  - `mcp_server.py` created — MCP SSE server on port 8765, 4 tools (vault_read/write/append, semantic_search) + auto-discoverable plugin system
  - `nova_api.py` created — FastAPI sidecar on port 8766 with 15 endpoints (system stats, ollama proxy, vault ops, streaming chat, semantic search, NR parsing, RAG index/query, TTS)
  - `nova-tools.service` + `nova-api.service` — systemd user services, both enabled at boot
  - `plugins/calculator.py` + `plugins/datetime_.py` — 2 starter plugins auto-loaded by MCP server
  - NovaHub expanded from 6 to 14 tabs: System, Models, Chat, Daily, Search, Vault, NR, RAG
  - System Monitor: GPU temp, CPU load, RAM/disk bars, polls every 5s
  - Ollama Panel: model list table with pull/load/unload/delete buttons
  - Quick Chat: streaming SSE chat with qwen3:8b via Ollama /v1/chat/completions
  - Daily Note: auto-detects today's date, reads 01_Daily/YYYY-MM-DD.md, append mode
  - Semantic Search: vector search via LanceDB, shows similarity score + source path
  - Vault Browser: tree view + file editor with path-traversal protection
  - NR Viewer: parses WORKLOG.md, filterable table with expandable detail rows
  - RAG Panel: index all vault .md files, query with context injection, grounded answers
  - TTS Briefing: espeak-ng generates audio of today's daily log
  - `deploy.sh` — one-command redeploy script

---

## 2026-07-02 — Day 25

### NR-022 — DB Reconciliation & Hydration Fix
**Time**: ~00:00
**Status**: Completed
**Detail**: Fix stale Obsidian Vault status, Prisma enum mismatch, and Next.js hydration error on Refresh button.
**Outcomes**:
  - Obsidian Vault status changed from `"available"` → `"active"` in nova.db (Prisma ServiceStatus enum only accepts `active/offline/online`)
  - All 11 services rendering correctly in NovaHub dashboard with correct status colors
  - Hydration mismatch on Refresh button `disabled` attribute fixed — server rendered `null`, client rendered `true`
  - Root cause: Next.js Turbopack static-pre-renders `'use client'` components without running useState initializers for boolean HTML attributes
  - Fix: `mounted` guard (`useState(false)` + `useEffect(() => setMounted(true))`) — both server and client start with `disabled={undefined}`, attribute appears only after hydration

---

## Key Metrics

| Metric | Value |
|---|---|---|
| Sessions | 4 (Day 1 + Day 2 continued + Big Pickle + Day 25) |
| NR Reports | 23 (NR-000 through NR-022) |
| Git Commits | 13 (11 vault + 2 novahub) |
| Files in Vault | 40+ (all sections + nova-tools Python stack) |
| ROCm VRAM | 16GB GDDR6 (15.8 GiB available) |
| Ollama Version | v0.31.1 (ROCm 7.2 GPU backend) |
| Models | tinyllama + qwen3:8b + nomic-embed-text + ornith:9b + ornith:9b-256k — all GPU |
| Services | Ollama (11434) ✅, NovaHub (3000) ✅, nova-tools MCP (8765) ✅, nova-api (8766) ✅, UFW ✅ |
| Free Disk | ~876 GB |
| Dashboard Status | ✅ 14 tabs live at localhost:3000 — all API endpoints verified |
| Agent Stack | ✅ nova-tools (MCP :8765, API :8766, config, plugins) at ~/nova-tools/ |
