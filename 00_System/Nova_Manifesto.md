type: system_core_principles
status: active

# Nova Manifesto

## Sovereignty

This system makes zero cloud API calls. Every model, every embedding, every search, every synthesis runs on local hardware. No data leaves this machine.

## Architecture

The vault is a shared state machine between human and AI:

- **Human** writes objectives, reads summaries, reviews artifacts
- **AI** reads timelines, executes tasks, appends logs, indexes knowledge
- **Time anchor** — Daily notes synchronize both parties to the same day

## Memory Hierarchy

| Layer | Store | Purpose |
|---|---|---|
| Episodic | LanceDB + 01_Daily | What happened today |
| Semantic | Obsidian vault (03_Knowledge) | What we know |
| Deep Synthesis | Open Notebook | Multi-document analysis |

## File Conventions

Every vault document SHOULD include in its frontmatter:
- `date: YYYY-MM-DD` — the calendar date
- `timestamp: YYYY-MM-DDTHH:MM:SS±HH:MM` — precise wall-clock time
- `report: NR-NNN` — sequential report number (for generated reports)
- `status: active | draft | completed` — lifecycle state

Perishable or auto-generated files (reports, session logs) MUST include `timestamp`. Static reference files (manifestos, templates) need only `date`.

## Getting Started

New agents should read, in order:
1. `00_System/Nova_Manifesto.md` — this file
2. `00_System/Agent_Quick_Reference.md` — paths, ports, configs, conventions
3. `00_System/Nova_Timeline.md` — current phase and daily goals
4. `01_Daily/<today>.md` — active log (append here after tasks)

## Agent Rules

1. Always log completions and errors to today's Daily Note
2. Read the Timeline before starting any new task
3. Never reboot the system without human confirmation
4. All file writes go through vault_operations (when Hermes is live)
