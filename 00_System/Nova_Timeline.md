type: system_core_timeline
date: 2026-07-01
status: active
current_phase: Phase 1

# Nova Project: 30-Day Stabilization Sprint

## Week 1: The Foundation (Milestones 1 & 2)

- [x] **Day 01** — OS Update, Essential Packages, GPU Drivers (ROCm 7.1, RX 9060 XT)
- [ ] **Day 02** — Firewall hardening, Install Ollama (Dual services: :11435 / :11436)
- [ ] **Day 03** — VSCodium + Continue.dev config, wire to Ollama
- [ ] **Day 04** — Pull models (Gemma2/GLM4 + Nomic), verify inference API
- [ ] **Day 05** — Buffer day / Debug GPU & Inference issues
- [ ] **Day 06** — Milestone check: Core infrastructure operational
- [ ] **Day 07** — Milestone check: Core infrastructure operational

## Week 2: The Agentic Core (Milestones 3 & 4)

- [ ] **Day 08** — Clone Hermes, create venv, install dependencies
- [ ] **Day 09** — Configure ~/.hermes/config.yaml, connect to Ollama ports
- [ ] **Day 10** — Interactive Mode Verification, test NL prompts
- [ ] **Day 11** — Create Hermes systemd service, verify background running
- [ ] **Day 12** — Obsidian vault operational (Living File anchor)
- [ ] **Day 13** — Seed Vault Architecture (00_System through 05_Templates)
- [ ] **Day 14** — Milestone check: Hermes responds to prompts, Vault active

## Week 3: Semantic Memory & Control Surface (Milestones 5 & 6)

- [ ] **Day 15** — Install LanceDB, build index_memory.py
- [ ] **Day 16** — Build vault_operations.py (read/write/append/search)
- [ ] **Day 17** — Verify Git Auto-Commits on vault writes
- [ ] **Day 18** — Verify /search command in Hermes retrieves context
- [ ] **Day 19** — Initialize Next.js NovaHub Dashboard
- [ ] **Day 20** — Build API Routes & UI Components
- [ ] **Day 21** — Milestone check: Memory pipeline and Dashboard live

## Week 4: The Loop & Deep Synthesis (Milestones 7 & 8)

- [ ] **Day 22** — Register vault_operations as MCP tool for Hermes
- [ ] **Day 23** — Test Agent Write-Access: "Hermes, save this to..."
- [ ] **Day 24** — Install Open Notebook (Native build, NO Docker)
- [ ] **Day 25** — Sovereignty Hack: Wire Open Notebook to local Ollama
- [ ] **Day 26** — Wire Open Notebook TTS to local Kokoro instance
- [ ] **Day 27** — End-to-end RAG: PDF -> Query -> Summary -> Vault
- [ ] **Day 28** — Test Audio Briefing pipeline: PDF -> Kokoro -> MP3
- [ ] **Day 29** — Auto-index verification: logs hit LanceDB & Episodic
- [ ] **Day 30** — Sovereignty Audit: Zero cloud API calls. System stabilized.
