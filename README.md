# Nova

Local-first AI workstation. No cloud. All yours.

Guardian: **Syzygy** — the alignment engine.

## What Is This?

A vault that Bo and the AI share. Bo writes objectives, reads summaries, reviews artifacts. **Syzygy** reads the mood, routes through tunnels, and executes tasks. Everything stays synced through daily notes.

The guardian's name means the alignment of celestial bodies. It's the bridge between intent and execution.

## Vault Layout

| Folder | What It's For |
|---|---|
| `00_System/` | The rules — Manifesto, Timeline, profiles, moods, tunnels, design |
| `01_Daily/` | Daily notes. One per day. Start here. |
| `02_Projects/` | Active projects. |
| `03_Knowledge/` | Research, references, compounding knowledge. |
| `04_Logs/` | Historical logs. |
| `05_Templates/` | Note templates. Don't edit — copy. |
| `99_Meta/` | Index, audits, vault meta. |

### 00_System Deep Dive

| Path | What It Is |
|---|---|
| `_profiles/human/` | Human identities (Bo, allies like Ben Goertzel) |
| `_profiles/agent/` | Guardian charter (Syzygy 1.0) |
| `_moods/` | 5 operational states: Build · Explore · Survival · Daily · Rest |
| `_tunnels/` | 6 focus channels: Survival · Vault · Infra · Research · Build · Index |
| `_templates/` | Re-usable templates for profiles, moods, tunnels |
| `_design/` | Syzygy palette, Obsidian theme, design system |

## Mood Tiers

Syzygy shifts its behavior based on where Bo's head is at:

| Tier | When | Tone |
|---|---|---|
| **Build** | Deep systems work | Minimal, direct |
| **Explore** | Creative / tinkering | Expansive, curious |
| **Survival** | Stressed / overwhelmed | Sparse, grounding |
| **Daily** | Morning check-in | Normal, syncing |
| **Rest** | Off hours | Silent, log-only |

## Where Things Are Installed

| Tool | Location | Status |
|---|---|---|
| **Obsidian** | `~/Downloads/Obsidian-1.12.7.AppImage` | ✅ Working, Syzygy theme active |
| **ROCm (GPU)** | System-wide | ✅ RX 9060 XT, 16GB VRAM |
| **Hermes** | `~/hermes-agent/` | ⏸️ Cloned, needs venv |
| **Ollama** | Broken binary | ❌ Needs re-download |
| See `00_System/Agent_Quick_Reference.md` for full details |

## Current Status

End of Day 1. Vault is seeded with 8 commits. Syzygy identity is established. Mood tiers and tunnels are documented. Obsidian is themed. 845 GB free disk. Next up: Ollama + Hermes.

## The Look

Syzygy's palette: Void Dark (`#0D1117`) background, Solar Gold (`#F5C542`) accents, Aurora Teal (`#3DD6C8`) links. The Obsidian theme snippet is already loaded — just enable it in Settings → Appearance → CSS snippets.

## Quick Start (for Bo)

1. Open Obsidian (click the desktop icon or run `~/Downloads/Obsidian-1.12.7.AppImage`)
2. Read today's note in `01_Daily/`
3. Check the Timeline in `00_System/`
4. Write what you need under **Human Objectives**
5. Tell Syzygy what mood you're in

## Git

```bash
git log --oneline          # see history
git add . && git commit -m "message"  # save
```

No remote yet. Everything stays local.

---

*Built on Ubuntu 26.04 with an AMD RX 9060 XT and zero cloud calls. Guarded by Syzygy.*
