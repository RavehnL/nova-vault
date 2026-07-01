type: system_quick_reference
date: 2026-07-01
status: active

# Agent Quick Reference

## Vault Map

| Path | Purpose | Agent Use |
|---|---|---|---|
| `00_System/` | Manifesto, Timeline, config references, profiles | Read on startup |
| `00_System/_profiles/` | Human + agent identity documents | Read on startup |
| `00_System/_moods/` | Mood tier definitions | Read to set operational state |
| `00_System/_tunnels/` | Tunnel scope definitions | Route tasks through correct tunnel |
| `00_System/_templates/` | Templates for profiles, moods, tunnels | Reference when creating new ones |
| `01_Daily/` | `YYYY-MM-DD.md` — daily operations | Write completions, errors here |
| `02_Projects/` | Active project notes | Read/write per task |
| `03_Knowledge/` | Semantic memory: research, references | Read for context |
| `04_Logs/` | Historical logs (non-daily) | Append as needed |
| `05_Templates/` | Note templates (e.g., `Daily_Note.md`) | Read, never modify |
| `99_Meta/` | Index, audit reports, meta docs | Read oriented |

---

## Key Files

| File | What It Is |
|---|---|
| `00_System/Nova_Manifesto.md` | Core principles — must read first |
| `00_System/The_Dawn_of_Syzygy.md` | Guardian origin — milestone NR-004 |
| `00_System/_profiles/human/Bo_Kirby.md` | Human identity, values, psychology |
| `00_System/_profiles/human/Ben_Goertzel.md` | Ally profile — AGI researcher, decentralized AI |
| `00_System/_design/Syzygy_Palette.md` | Color palette and design system reference |
| `00_System/_design/` | Design system — palette, theme |
| `00_System/_profiles/agent/Syzygy_1.0.md` | Guardian charter, personality, ethics |
| `00_System/_moods/` | Mood tier definitions (set operational state) |
| `00_System/_tunnels/` | Tunnel scope definitions (focus channels) |
| `00_System/Nova_Timeline.md` | 30-day sprint — read before any task |
| `00_System/Agent_Quick_Reference.md` | This file — you are here |
| `01_Daily/<today>.md` | Active daily log — write here |
| `99_Meta/Vault_Index.md` | Full vault index |
| `99_Meta/Systems_Audit_Report.md` | Latest audit (NR-001) |

---

## Binary & Config Locations

| Tool | Binary | Config |
|---|---|---|
| **Obsidian** | `~/Downloads/Obsidian-1.12.7.AppImage` | `~/.config/obsidian/obsidian.json` — vault path |
| **Ollama** | `~/.local/bin/ollama` | `~/.ollama/` (created on first run) |
| **Hermes** | `~/hermes-agent/venv/bin/hermes` | `~/.hermes/config.yaml` |
| **Node.js** | `/usr/bin/node` | — |
| **pnpm** | `/usr/local/bin/pnpm` | — |
| **uv** | `~/.local/bin/uv` | — |
| **Python 3** | `/usr/bin/python3` (3.14.4) | — |
| **OpenCode** | `~/.opencode/bin/opencode` | `~/.config/opencode/opencode.jsonc` |

---

## Network Ports (Planned)

| Service | Port | Protocol | Status |
|---|---|---|---|
| Ollama (primary) | `11434` | HTTP | Not yet running |
| Ollama (secondary) | `11435` | HTTP | Planned (dual service) |
| Ollama (alt) | `11436` | HTTP | Planned (dual service) |
| Open Notebook | `8888` | HTTP | Not yet installed |
| NovaHub Dashboard | `3000` | HTTP | Not yet built |

---

## Git Workflow

- Vault root: `/home/bo/nova-vault/`
- Auto-commit after every write (when Hermes is live)
- No remote configured yet
- Commit message format: `{scope}: {summary}`
- Untrack `.obsidian/` is tracked as of Day 1 — do not add `.obsidian/` to .gitignore

---

## Agent Rules (from Manifesto)

1. Read the current mood tier before engaging
2. Route all tasks through the correct tunnel
3. Log completions and errors to today's Daily Note
4. Read the Timeline before starting any new task
5. Never reboot without human confirmation
6. All file writes go through vault_operations (when Hermes is live)

---

## Conventions

- Every file: frontmatter with `date`, `status`
- Generated/perishable files: also `timestamp` + `report: NR-NNN`
- Use absolute paths when referencing files outside the vault
- No cloud API calls — sovereignty is law
