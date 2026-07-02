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
	| `03_Knowledge/` | Semantic memory: research, references, acquired skills | Read for context |
	| `04_Logs/` | Historical logs, WORKLOG, persistent reports | Append as needed |
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
	| `99_Meta/nova.db` | Prisma/SQLite database — NovaHub dashboard backend |
	| `99_Meta/Vault_Index.md` | Full vault file index |
	| `04_Logs/WORKLOG.md` | Persistent session log — all NR reports across days |
	| `03_Knowledge/ponytail.md` | YAGNI skill reference — lazy senior dev ruleset |
	
	---
	
	## Binary & Config Locations
	
	| Tool | Binary | Config |
	|---|---|---|
	| **Obsidian** | `~/Downloads/Obsidian-1.12.7.AppImage` | `~/.config/obsidian/obsidian.json` — vault path |
	| **Ollama** | `/usr/local/bin/ollama` (v0.31.1) | `/etc/systemd/system/ollama.service` + `~/.ollama/` |
	| **Hermes** | `~/.hermes/hermes-agent/venv/bin/hermes` | `~/.hermes/config.yaml` (cut — v0.17.0 doesn't support local Ollama) |
	| **Node.js** | `/usr/bin/node` | — |
	| **pnpm** | `/usr/local/bin/pnpm` | — |
	| **uv** | `~/.local/bin/uv` | — |
	| **Python 3** | `/usr/bin/python3` (3.14.4) | — |
	| **OpenCode** | `~/.opencode/bin/opencode` | `~/.config/opencode/opencode.jsonc` |
	| **Ponytail** | OpenCode plugin | `~/.local/share/ponytail/` (cloned repo) |
	
	---
	
	## Network Ports (Planned)
	
	| Service | Port | Protocol | Status |
	|---|---|---|---|---|
	| Ollama | `11434` | HTTP | ✅ Running — ROCm 7.2 GPU (v0.31.1) |
	| NovaHub Dashboard | `3000` | HTTP | ✅ Running — Prisma/SQLite at 99_Meta/nova.db |
	| Open Notebook | `8888` | HTTP | Not yet installed |
	| UFW Firewall | — | — | ✅ Active — ports 11434 + 3000 open |
	
	---
	
	## Git Workflow
	
	- Vault root: `/home/bo/nova-vault/`
	- Auto-commit after every write
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
	6. Prefer YAGNI: use ponytail ruleset (stdlib → native → dependency → one line → min code)
	
	---
	
	## Conventions
	
	- Every file: frontmatter with `date`, `status`
	- Generated/perishable files: also `timestamp` + `report: NR-NNN`
	- Use absolute paths when referencing files outside the vault
	- No cloud API calls — sovereignty is law
