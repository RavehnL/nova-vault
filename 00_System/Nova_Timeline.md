---
type: system_core_timeline
date: 2026-07-01
status: active
current_phase: Phase 1
---
# Nova Project: 30-Day Stabilization Sprint

## Week 1: The Foundation (Milestones 1 & 2)

- [x]  **Day 01** — Foundation + Syzygy Establishment (NR-000 through NR-010)
- [x]  **Day 02** — Python, Node.js, Firewall hardening (UFW)
- [x]  **Day 03** — Install Ollama v0.31.1 + ROCm 7.2 GPU inference (NR-013/NR-016)
- [x]  **Day 04** — Single Ollama Service (port consolidation to :11434)
- [x]  **Day 05** — Pull models (Qwen3:8b, TinyLlama, Nomic-embed-text), verify inference API
- [x]  **Day 06** — Buffer Day: Debug GPU & Inference issues (ROCm 7.2 ABI mismatch, tmpfs overflow, NR-013)
- [x]  **Day 07** — Milestone Check: M1 Core Infrastructure + Syzygy, M2 Core Inference

## Week 2: The Custom Agentic Core (Milestones 3 & 4)

- [x]  **Day 08** — Build `vault_operations.py` (The Hands): read/write/append/search for vault
- [x]  **Day 09** — Build `index_memory.py` (The Hippocampus): LanceDB embedding storage via Ollama
- [x]  **Day 10** — Interactive Mode Verification: nova-tools stack responds to NL prompts (NR-017)
- [ ]  **Day 11** — Create systemd services for nova-tools scripts, verify background running
- [x]  **Day 12** — Initialize Obsidian Vault + Git repo, apply Syzygy theme
- [x]  **Day 13** — Seed Vault Architecture (00_System through 05_Templates, profiles/moods/tunnels)
- [ ]  **Day 14** — Milestone Check: M3 Custom Agentic Core pipeline verified, M5 Episodic Memory pipeline verified

## Week 3: Semantic Memory & Control Surface (Milestones 5 & 6)

- [x]  **Day 15** — Install LanceDB in isolated `uv` venv, build `index_memory.py` (NR-017)
- [x]  **Day 16** — Build `vault_operations.py` (read/write/append) (NR-017)
- [x]  **Day 17** — Verify Git Auto-Commits on vault writes via Python script
- [x]  **Day 18** — Verify /search command retrieves context via vector similarity (NR-017)
- [x]  **Day 19** — Initialize Next.js NovaHub Dashboard (6-tab layout)
- [x]  **Day 20** — Build API Routes & UI Components (8 REST endpoints, agent cards, system monitor)
- [~]  **Day 21** — Milestone check: Memory pipeline and Dashboard live ✅; Install Kokoro TTS (deferred)
- [x]  **Day 22** — NovaHub reconciliation — DB at vault path, seed data updated (Ora→Syzygy), all APIs verified
- [x]  **Day 23** — Syzygy agent added to dashboard, Hermes→nova-tools cut resolved
- [x]  **Day 24** — System stabilized, Prisma enum mismatch fixed, all API endpoints 200

## Week 4: The Loop & Deep Synthesis (Milestones 7 & 8)

- [x]  **Day 22** — Central config system (~/.nova/config.yaml), vault_operations.py + index_memory.py migrated
- [x]  **Day 23** — MCP server (SSE :8765, 4 tools + plugin system) + FastAPI sidecar (:8766, 15 endpoints)
- [x]  **Day 24** — NovaHub expanded to 14 tabs: System, Models, Chat, Daily, Search, Vault, NR, RAG, Briefing
- [ ]  **Day 25** — Git auto-commit daemon, daily vault backup, git remote push
- [ ]  **Day 26** — Install Open Notebook (Native build, NO Docker)
- [ ]  **Day 27** — Sovereignty Hack: Wire Open Notebook to local Ollama :11434
- [ ]  **Day 28** — Wire Kokoro TTS to local Ollama :11434
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
- ✅ Central config system — ~/.nova/config.yaml drives all tools (NR-021)
- ✅ MCP server (SSE :8765) — vault_read/write/append, semantic_search + plugin loader
- ✅ FastAPI sidecar (:8766) — 15 endpoints for NovaHub proxy
- ✅ NovaHub 14-tab dashboard — System, Models, Chat, Daily, Search, Vault, NR, RAG, Briefing
- ✅ RAG pipeline — vault markdown index + query with context injection
- ✅ TTS — espeak-ng daily briefing audio

---

