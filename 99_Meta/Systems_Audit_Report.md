type: audit
date: 2026-07-01
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

**ROCm Status:** Operational. ROCm 7.1 installed. GPU detected at `gfx1200` (32 CUs, 16GB VRAM). SMI reports device healthy (35°C, 8% VRAM usage).

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

### ❌ Missing / Broken

| Tool | Status | Issue |
|---|---|---|
| **Ollama** | Broken | Binary at `~/.local/bin/ollama` is only 9 bytes ("Not Found") — download URL was wrong |
| **Hermes Agent** | Unconfigured | Repo cloned to `~/hermes-agent`, no venv created, no `~/.hermes/` config |
| **python3-pip** | Not installed | Only `uv` available for package management |
| **LanceDB** | Not installed | Needed for semantic memory (Week 3) |
| **UFW Firewall** | Not configured | Timeline Day 2 task — not started |
| **vault_operations** | Not built | Planned MCP tool for Hermes (Week 3) |

### ⚠️ Partial / Needs Attention

| Component | Note |
|---|---|
| Obsidian vault `.gitignore` | `.obsidian/` is untracked — good practice, but ensure sync config is intentional |
| Hermes venv | Cannot use `python3 -m venv` (no `ensurepip`). Can use `uv venv` instead |
| Hermes config | Need to create `~/.hermes/config.yaml` pointing at Ollama |

---

## 3. Vault Health

### Structure: ✅ Complete

```
nova-vault/
├── 00_System/         ✅ Nova_Manifesto.md, Nova_Timeline.md
├── 01_Daily/          ✅ 2026-07-01.md
├── 02_Projects/       📁 empty
├── 03_Knowledge/      📁 empty
├── 04_Logs/           📁 empty
├── 05_Templates/      ✅ Daily_Note.md
├── 99_Meta/           ✅ Vault_Index.md (now + Systems_Audit_Report.md)
├── .obsidian/         ✅ Connected (appearance, app, core-plugins, graph, workspace)
└── .git/              ✅ 1 commit (no remote configured)
```

### Git: ⚠️ No Remote

```git log
5dcd31b Day 1: vault foundation — system setup, ROCm, Node.js, uv, Living File anchor
```

No remote repository configured. Consider adding a private GitHub/GitLab remote for backup.

---

## 4. Services

| Service | Status |
|---|---|
| ollama | Not running — not installed |
| hermes | Not running — not installed |
| ufw/firewall | Not configured |
| Open Notebook | Not installed (Week 4) |
| NovaHub Dashboard | Not started (Week 3) |

---

## 5. Roadmap: Current vs Planned

Based on [Nova_Timeline.md](../00_System/Nova_Timeline.md).

### Week 1: The Foundation (Day 1–7)

| Day | Task | Status | Notes |
|---|---|---|---|
| **1** | OS Update, GPU Drivers, ROCm | ✅ Done | All packages installed |
| **1** | Node.js, npm, uv | ✅ Done | |
| **1** | Obsidian + vault structure | ✅ Done | AppImage restored, vault connected |
| **2** | Firewall hardening (UFW) | ❌ Not started | |
| **2** | Install Ollama | ❌ Broken binary | Need correct download URL |
| **3** | VSCodium + Continue.dev | ❌ Not started | Wire to Ollama |
| **4** | Pull models (Gemma2/GLM4 + Nomic) | ❌ Not started | Requires Ollama first |
| **5** | Buffer / Debug | ❌ Not started | |
| **6–7** | Milestone check | ❌ Not started | |

### Week 2: The Agentic Core (Day 8–14)

| Day | Task | Status | Notes |
|---|---|---|---|
| **8** | Clone Hermes, create venv, install deps | ⏸️ Partial | Cloned, no venv — blocked on python3-venv |
| **9** | Configure `~/.hermes/config.yaml` | ❌ Blocked | Needs Ollama first |
| **10** | Interactive Mode Verification | ❌ Blocked | |
| **11** | Hermes systemd service | ❌ Blocked | |
| **12** | Obsidian vault operational | ✅ Done | |
| **13** | Seed Vault Architecture | ✅ Done | 00_System through 05_Templates |
| **14** | Milestone check | ❌ | |

### Week 3: Semantic Memory & Control Surface (Day 15–21)

All tasks blocked (require Hermes + Ollama foundation).

### Week 4: The Loop & Deep Synthesis (Day 22–30)

All tasks blocked.

---

## 6. Immediate Action Items (Priority Order)

1. **Fix Ollama download** — Get the correct binary URL for `ollama-linux-amd64` (v0.6.1+). This unblocks everything.
2. **Set up Hermes venv** — Use `uv venv` instead of `python3 -m venv` (no sudo needed).
3. **Install pip** — `uv pip install pip` or use `uv` as the primary package manager.
4. **Configure UFW** — Open ports 11434 (Ollama) and 11435/11436 (dual services per timeline).
5. **Pull models** — At minimum: Hermes 3 (8B) + Nomic embed text.
6. **Configure Hermes** — Create `~/.hermes/config.yaml` pointing at local Ollama.
7. **Push vault to remote** — Set up GitHub/GitLab remote for backup.

---

## 7. Risks & Blockers

| Risk | Impact | Mitigation |
|---|---|---|
| Broken Ollama binary | Blocks Days 2–30 | Fix download or build from source |
| No python3-venv / pip | Blocks Hermes setup | Use `uv` as drop-in replacement |
| No firewall | Security risk | Configure UFW on Day 2 |
| No git remote | No backup | Setup remote after vault seed |
