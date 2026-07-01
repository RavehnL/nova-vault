---
type: tunnel
tunnel: infra
date: 2026-07-01
status: active
---

# Tunnel: Infra

## Scope

System administration, service configuration, port management, dependency installation, network setup.

## Boundaries

Do NOT modify vault files, create project notes, or engage in research. Infra only.

## Linked Files

- `00_System/Agent_Quick_Reference.md` — binary paths, port list
- `00_System/Nova_Timeline.md` — infra-related milestones
- `01_Daily/<today>.md` — log changes

## Allowed Actions

| Action | Permission |
|---|---|
| Install/update packages | Yes |
| Configure services (systemd, ports) | Yes |
| Modify config files (~/.hermes/, ~/.ollama/) | Yes |
| Git commit vault changes | Log-only |
| Run diagnostic commands | Yes |

## Key Configs

| Service | Path | Port |
|---|---|---|
| Ollama | `~/.local/bin/ollama` | 11434 / 11435 |
| Hermes | `~/hermes-agent/` | — |
| Obsidian | `~/Downloads/Obsidian-1.12.7.AppImage` | — |
| OpenCode | `~/.opencode/bin/opencode` | — |
| UFW | System | All ports |
