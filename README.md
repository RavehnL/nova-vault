---
type: readme
date: 2026-07-02
status: active
---

# Nova Project

Local-first AI workstation. No cloud. All yours.

Guardian: **Syzygy** — the celestial alignment engine. The bridge between intent and execution.
Agent stack: **nova-tools** — MCP server (:8765) + FastAPI API (:8766) + NovaHub dashboard (:3000).

---

## What Is This?

A sovereign AI workspace built on Ubuntu 26.04 with AMD ROCm. Bo writes objectives, reads summaries, reviews artifacts. **Syzygy** reads the mood tier, routes through tunnels, and executes tasks. Everything stays synced through daily notes.

**Core principle**: Every request routes through a tunnel. Every action respects a mood. Every artifact gets frontmatter with `date`, `timestamp`, `report: NR-NNN`, `status`.

## Quick Start

1. **Open the vault**: Obsidian is at `~/Downloads/Obsidian-1.12.7.AppImage`. Run with `--no-sandbox`.
2. **Open OpenCode**: Agent interface at `~/.opencode/bin/opencode` — this is how tasks execute.
3. **Read today's note**: `01_Daily/YYYY-MM-DD.md` — start here every session.
4. **Check the timeline**: `00_System/Nova_Timeline.md` — what phase are we in?
5. **Read the Manifesto**: `00_System/Nova_Manifesto.md` — the rules.
6. **Set your mood**: Tell Syzygy which tier you're in (build/explore/survival/daily/rest).
7. **Check the dashboard**: `http://localhost:3000` — NovaHub with 14 tabs.

Before Syzygy can operate, it must read in order: Manifesto → Bo profile → Syzygy charter → Quick Reference → Timeline → daily note.

## Vault Layout

| Folder | What It's For |
|---|---|
| `00_System/` | The rules — Manifesto, Timeline, profiles, moods, tunnels, templates, design |
| `01_Daily/` | Daily notes — one per day. The entry point. |
| `02_Projects/` | Active project work. |
| `03_Knowledge/` | Research, references, compounding knowledge. |
| `04_Logs/` | Historical logs and reports. |
| `05_Templates/` | Note templates. Copy, don't edit. |
| `99_Meta/` | Index, audits, vault meta, DB. |
| `.obsidian/` | Theme config, CSS snippets. |

### 00_System Deep Dive

| Path | Contents |
|---|---|
| Core Documents | Manifesto, Timeline (30-day sprint), Syzygy origin (NR-004), Agent Quick Reference |
| `_profiles/human/` | Bo_Kirby.md (identity, values, life timeline), Ben_Goertzel.md (ally) |
| `_profiles/agent/` | Syzygy_1.0.md (guardian charter, ethics, personality) |
| `_moods/` | 5 operational states — build (deep work), explore (creative), survival (stressed), daily (default), rest (off-hours) |
| `_tunnels/` | 6 focus channels — survival (income), vault (KM), infra (ops), research (deep study), build (coding), index (registry) |
| `_templates/` | 4 re-usable scaffolds — human_profile, agent_identity, mood_tier, tunnel |
| `_design/` | Syzygy palette, design system, Obsidian theme reference |

## Mood Tiers

Syzygy shifts autonomy, verbosity, tone, and error handling based on Bo's state:

| Tier | When | Autonomy | Tone |
|---|---|---|---|
| **Build** | Deep systems work | Max | Minimal, direct |
| **Explore** | Creative tinkering | High | Expansive, curious |
| **Daily** | Morning check-in | Medium | Normal, syncing |
| **Survival** | Stressed / overwhelmed | Low | Sparse, grounding |
| **Rest** | Off hours | None | Silent, log-only |

## Tunnels

Tunnels prevent context bleed. Syzygy loads only the active tunnel's scope:

| Tunnel | Scope | Allowed Actions |
|---|---|---|
| **Survival** | Income, resource acquisition | Search, calculate, draft proposals |
| **Vault** | KM, file organization | Read, edit, link, index |
| **Infra** | System admin, networking | Read logs, edit configs, run commands |
| **Research** | Deep reading, knowledge work | Read, summarize, synthesize |
| **Build** | Coding, prototyping | Read, edit, run, debug |
| **Index** | Meta, vault map | Read, update index |

## Profile Architecture

- **Human profiles** (`_profiles/human/`) — Life timeline, values, psychology. Each ally gets one.
- **Agent identities** (`_profiles/agent/`) — Charter, personality matrix, mood/tunnel config, ethics.

Every profile uses a reusable template from `_templates/`.

## Where Things Are Installed

| Tool | Location | Status |
|---|---|---|
| **Obsidian** | `~/Downloads/Obsidian-1.12.7.AppImage` | ✅ Syzygy theme active |
| **ROCm 7.2** | System-wide (kernel module) | ✅ RX 9060 XT, 32 CUs, 16GB VRAM |
| **Node.js** | `/usr/bin/node` v22.22.1 | ✅ |
| **pnpm** | `/usr/local/bin/pnpm` v11.9.0 | ✅ |
| **uv** | `~/.local/bin/uv` v0.11.26 | ✅ |
| **MCP Server** | `~/nova-tools/mcp_server.py` port 8765 | ✅ SSE, 4 tools, plugins |
| **Nova API** | `~/nova-tools/nova_api.py` port 8766 | ✅ FastAPI, 15 endpoints |
| **NovaHub** | Dev server at `http://localhost:3000` | ✅ 14 tabs, Prisma/SQLite |
| **Ponytail** | OpenCode plugin (global config) | ✅ Installed — YAGNI task ruleset |
| **nova-tools** | `~/nova-tools/` (isolated venv) | ✅ Config, MCP, API, plugins |
| **Ollama** | `/usr/local/bin/ollama` v0.31.1 | ✅ ROCm 7.2 GPU inference at localhost:11434 |

Full details: `00_System/Agent_Quick_Reference.md`

## Backend Services

Three systemd user services run the agent stack:

| Service | Port | What it does |
|---|---|---|
| `nova-tools.service` | 8765 (SSE) | MCP server — vault ops + semantic search + plugins |
| `nova-api.service` | 8766 (HTTP) | FastAPI sidecar — system stats, ollama proxy, vault, chat, search, NR, RAG, TTS |
| `novahub.service` | 3000 (HTTP) | NovaHub dashboard — Next.js 16 + Prisma/SQLite |

`novahub.service` depends on `nova-api.service` (`After=` + `BindsTo=`). All three auto-start on boot, restart on failure. Managed via `systemctl --user`.

## NovaHub Dashboard

The control surface at `localhost:3000` provides 14 tabs:

| Tab | What it does |
|---|---|
| **Command Center** | Quick access panel, agent/service status, milestone progress |
| **Agents** | Agent cards with icons, status, version |
| **Services** | Grouped by category (core/memory/interface/synthesis) |
| **Roadmap** | 30-day sprint milestones with task progress |
| **Timeline** | 4-week sprint day grid |
| **Daily Log** | Log entries with human/agent/errors sections |
| **System** | Live monitor: GPU temp, CPU load, RAM/Disk bars (polls 5s) |
| **Models** | Ollama model table: pull, load/unload, delete |
| **Chat** | Streaming chat with qwen3:8b via Ollama API |
| **Daily** | Today's daily note viewer + append mode |
| **Search** | Semantic vector search via LanceDB |
| **Vault** | File tree browser with edit/save |
| **NR** | NR report viewer with search + expand |
| **RAG** | Index vault markdown, query with context injection |

Backed by Prisma/SQLite at `99_Meta/nova.db` + Python sidecar at `localhost:8766`.

## Current Status

**Days 1-25 complete** — 2026-07-02. Foundation, Agentic Core, Memory, Dashboard, Big Pickle buildout, and git remote all operational:

- Ubuntu 26.04 + ROCm 7.2 + RX 9060 XT (32 CUs, 16GB VRAM, 40°C)
- Syzygy guardian identity established (NR-004) with full charter
- 5 mood tiers, 6 tunnels, 4 templates built
- Ollama v0.31.1 — ROCm 7.2 GPU inference (6 models)
- NovaHub dashboard: 14 tabs at localhost:3000 (NR-021)
- ✅ systemd services for nova-tools — MCP (:8765) + API (:8766) + NovaHub (:3000)
- ✅ Central config — ~/.nova/config.yaml drives all tools
- ✅ RAG pipeline — vault markdown index + context query
- ✅ TTS — espeak-ng daily briefing
- ✅ Git remote push — `git@github.com:RavehnL/nova-vault.git` (SSH)
- ✅ DB reconciliation — services table clean, Prisma enums aligned
- ✅ Hydration fix — Next.js Turbopack SSR consistency (NR-022)

**Next up**: Git auto-commit daemon, daily backup systemd timer, Open Notebook (native build).

## Git

```bash
git log --oneline          # 13 commits — foundation through Big Pickle
git status                 # current state
git add . && git commit -m "NR-NNN: message"  # commit with report number
git push origin main       # push to remote (SSH key auth)
```

Remote: `git@github.com:RavehnL/nova-vault.git` (private, SSH key). Push manually or wait for auto-commit daemon.

---

*Built on Ubuntu 26.04 LTS with AMD Radeon RX 9060 XT + ROCm 7.1. Zero cloud calls. Guarded by Syzygy.*
