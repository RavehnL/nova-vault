type: audit
report: NR-001
date: 2026-07-01
timestamp: 2026-07-01T17:21:00-04:00
status: active
auditor: Big Pickle

# Nova Project — Systems Audit & Roadmap Report

## 1. Hardware Summary

| Component | Detail |
|---|---|
| CPU | AMD Ryzen 5 5600G (12 threads) |
| RAM | 30 GiB |
| GPU | AMD Radeon RX 9060 XT (Navi 44, 16 GB VRAM) |
| Disk | 915 GB total, 845 GB free (92% free) |
| OS | Ubuntu 26.04 LTS (Resolute Raccoon), kernel 7.0.0-27-generic |

**ROCm Status:** Operational. ROCm 7.1 installed (HIP 7.1.52801). Ollama detects GPU as `gfx1201` via ROCm 7.2 backend, "AMD Radeon RX 9060 XT" with 15.8 GiB VRAM. SMI reports device healthy (38°C, 9% VRAM usage).

---

## 2. Software Inventory

### ✅ Installed & Verified

| Tool | Version | Location |
|---|---|---|
| Node.js | 22.22.1 | `/usr/bin/node` |
| npm | 9.2.0 | `/usr/bin/npm` |
| pnpm | 11.9.0 | `/usr/local/bin/pnpm` |
| uv | 0.11.26 | `~/.local/bin/uv` |
| Python 3 | 3.14.4 | `/usr/bin/python3` |
| ROCm | 7.1 | System-wide (dpkg) |
| Obsidian | 1.12.7 | `~/Downloads/Obsidian-1.12.7.AppImage` |
| OpenCode | latest | `~/.opencode/bin/opencode` |
| Ponytail | 4.8.4 | OpenCode plugin at `~/.local/share/ponytail/` |
| NovaHub Dashboard | Next.js 16 + Prisma 6 | Dev server at localhost:3000 |
| Ollama | 0.31.1 | `/usr/local/bin/ollama` — systemd service, ROCm 7.2 GPU backend |
| UFW | — | Active — ports 11434/tcp + 3000/tcp open |
| tinyllama | latest (Q4_0, 637 MB) | `~/.ollama/models/` — GPU inference verified |
| qwen3:8b | latest (Q4_K_M, 5.2 GB) | `~/.ollama/models/` — GPU inference verified (~49 tok/s) |
| nomic-embed-text | latest (274 MB) | `~/.ollama/models/` — embedding model, GPU verified |
| nova-tools | custom | `~/nova-tools/` — `vault_operations.py` + `index_memory.py` (LanceDB) |

### ❌ Missing / Broken

| Tool | Status | Issue |
|---|---|---|
| **Hermes Agent** | Cut — dead end | v0.17.0 doesn't support `provider: ollama`. Cloud-only provider model. Replaced with direct Ollama API. |
| **python3-pip** | Not installed | Only `uv` available for package management |

### ⚠️ Partial / Needs Attention

| Component | Note |
|---|---|
| Obsidian vault `.gitignore` | `.obsidian/` is untracked — good practice, but ensure sync config is intentional |
| Old `~/.local/bin/ollama` (v0.12.3) | Shadows `/usr/local/bin/ollama` (v0.31.1) in PATH. Cosmetic warning only — server runs the new version |

---

## 3. Vault Health

### Structure: ✅ Complete

```
nova-vault/
├── 00_System/         ✅ Manifesto, Timeline, Syzygy charter, profiles, moods, tunnels, templates, design
├── 01_Daily/          ✅ 2026-07-01.md (NR-000 through NR-019)
├── 02_Projects/       📁 empty
├── 03_Knowledge/      ✅ ponytail.md — YAGNI skill reference
├── 04_Logs/           ✅ WORKLOG.md, Reflections/ — persistent session log (NR-000 through NR-019)
├── 05_Templates/      ✅ Daily_Note.md
├── 99_Meta/           ✅ Vault_Index.md, Systems_Audit_Report.md, nova.db, _audits/ponytail/
├── .obsidian/         ✅ Connected (Syzygy theme active, appearance configured)
└── .git/              ✅ 11 commits + uncommitted NR-018→NR-019 (no remote)
```

### Git: ⚠️ No Remote (11 commits)

```git log --oneline
0bebf99 NR-017: living log refresh — nova-tools stack, LanceDB memory, timeline update
99871c6 NR-008: daily log updated — NovaHub dashboard review, Ora→Syzygy analysis
ab8e4fa NR-007: living doc refresh
3396f95 NR-006: Syzygy design palette + Obsidian CSS theme
16310a3 NR-005: Ben Goertzel profile
8c2de3d NR-004: Syzygy — guardian identity, mood tiers, tunnels, profiles, templates
b6aaf92 NR-003: README for human
9a20357 NR-002: Agent Quick Reference
a6e6497 Day 1 PM sync: timestamp/file conventions, systems audit
203d19f Day 1 end: systems audit report
5dcd31b Day 1: vault foundation
```

No remote repository configured. Consider adding a private GitHub/GitLab remote for backup.

---

## 4. Services

| Service | Status |
|---|---|---|
| Ollama | ✅ Running — v0.31.1, ROCm 7.2 GPU, systemd service at localhost:11434 |
| UFW / Firewall | ✅ Active — ports 11434/tcp + 3000/tcp open |
| NovaHub Dashboard | ✅ Live — Next.js 16 + Prisma/SQLite at localhost:3000, wired to vault DB, systemd auto-start on boot |
| nova-tools | ✅ Built — vault_operations.py + index_memory.py (LanceDB) at ~/nova-tools/ |
| Ponytail (plugin) | ✅ Active in OpenCode config |
| Open Notebook | Not installed (Week 4) |

---

## 5. Roadmap: Current vs Planned

Based on [Nova_Timeline.md](../00_System/Nova_Timeline.md).

### Week 1: The Foundation (Day 1–7)

| Day | Task | Status | Notes |
|---|---|---|---|
| **1** | Foundation + Syzygy Establishment | ✅ Done | Vault seeded, 10 NR reports, profiles, moods, tunnels, design, theme |
| **2** | Python, Node.js, Firewall hardening (UFW) | ✅ Done | UFW active — ports 11434 + 3000 open |
| **3** | Install Ollama v0.31.1 | ✅ Done | ROCm 7.2 GPU, systemd service |
| **4** | Single Ollama Service (port consolidation to :11434) | ✅ Done | Decision: single Ollama instead of dual services |
| **5** | Pull + verify models | ✅ Done | tinyllama (637MB) + qwen3:8b (5.2GB) — both inferring on GPU |
| **6** | Buffer: Debug GPU & Inference issues | ✅ Done | ROCm 7.2 ABI mismatch (v0.12.3→v0.31.1), tmpfs overflow (TMPDIR override) |
| **7** | Milestone Check: M1 + M2 | ✅ Done | Core infrastructure + inference operational |

### Week 2: The Custom Agentic Core (Day 8–14)

| Day | Task | Status | Notes |
|---|---|---|---|
| **8** | Build `vault_operations.py` (The Hands) | ✅ Done | Read/write/append/search via Ollama `/api/embed`, `/api/chat` |
| **9** | Build `index_memory.py` (The Hippocampus) | ✅ Done | LanceDB embedding storage via Ollama nomic-embed-text |
| **10** | Interactive Mode Verification | ✅ Done | Semantic search `/search` retrieves context via vector similarity (NR-017) |
| **11** | Create systemd services for nova-tools | ❌ Not started | |
| **12** | Initialize Obsidian Vault + Git | ✅ Done | |
| **13** | Seed Vault Architecture | ✅ Done | 00_System through 05_Templates |
| **14** | Milestone Check: M3 + M5 | ❌ Not started | Custom agent pipeline ready, systemd services pending |

Note: Hermes v0.17.0 evaluated and **cut** — doesn't support `provider: ollama`. Replaced with direct Ollama API. The `nova-tools` stack is the sovereign replacement (NR-017).

### Week 3: Semantic Memory & Control Surface (Day 15–21)

| Day | Task | Status | Notes |
|---|---|---|---|
| **15** | Install LanceDB, build `index_memory.py` | ✅ Done | LanceDB in uv venv, embedding via Ollama nomic-embed-text |
| **16** | Build `vault_operations.py` | ✅ Done | Read/write/append with path-traversal protection |
| **17** | Git auto-commit verification | ✅ Done | Python script triggers git add + commit on vault writes |
| **18** | Semantic search verification | ✅ Done | `/search` retrieves context via vector similarity |
| **19** | NovaHub Dashboard — Initialize | ✅ Done | Cloud architect delivered 6-tab reference at ~/nova-tools/novahub/ |
| **20** | API Routes & UI Components | ✅ Done | 8 REST endpoints, agent cards, system monitor |
| **21** | Milestone Check | 🔄 In progress | Memory pipeline + Dashboard live ✅; Install Kokoro TTS (deferred) |

Day 19-20 completed pre-schedule. NovaHub fully wired to vault DB (NR-018), timeline reconciled (NR-019). Prisma enum mismatch fixed — all API endpoints 200.

### Week 4: The Loop & Deep Synthesis (Day 22–30)

nova-tools stack operational. Dashboard live. Hermes dependency resolved (cut). Remaining tasks:

- Register vault_operations as MCP tool / CLI alias
- Test agent write-access: "Syzygy, save this to..."
- Install Open Notebook (native build, NO Docker)
- Wire Open Notebook to local Ollama :11434
- Wire Kokoro TTS for audio briefings
- End-to-end RAG: PDF → Query → Summary → Vault
- Sovereignty Audit: Zero cloud API calls

---

## 6. Immediate Action Items (Priority Order)

1. **systemd services for nova-tools** — Day 11: auto-start vault_operations + index_memory on boot.
2. **Push vault to remote** — Set up GitHub/GitLab remote for backup.
3. **Week 4 tasks** — MCP tool registration, Open Notebook, RAG pipeline, Kokoro TTS, sovereignty audit.
4. **Over-engineering cuts** — Remove unused shadcn components (~3,200 lines), mini-services scripts (266 lines), stale example code (333 lines).

---

## 7. Risks & Blockers

| Risk | Impact | Mitigation |
|---|---|---|
| No git remote | No backup | Set up remote after vault seed |
| No systemd for nova-tools | Agent stack not auto-starting | Day 11 task — create service files |
| No VSCodium | Blocks Continue.dev integration (Day 3) | Install when needed |
| Prisma enums vs raw TEXT mismatch | Schema drift if DB is edited outside Prisma | Keep dev-only; enums are advisory in SQLite |
