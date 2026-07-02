---
type: system_core_reference
date: 2026-07-02
status: active
---

# Nova Project — Startup Guide

Cold-boot procedure after computer restart. Everything is local — no cloud dependencies.

## After restart, these start automatically

| Service          | Port     | Auto                    | Verifies via                    |
| ---------------- | -------- | ----------------------- | ------------------------------- |
| **Ollama**       | `:11434` | systemd (enabled)       | `curl localhost:11434/api/tags` |
| **UFW firewall** | —        | systemd (enabled)       | `ufw status`                    |
| **nova-tools (MCP)** | `:8765` | systemd (user, enabled) | `curl http://localhost:8765/health` |
| **nova-api**     | `:8766`  | systemd (user, enabled) | `curl http://localhost:8766/health` |
| **NovaHub**      | `:3000`  | systemd (user, enabled) | open `http://localhost:3000`    |

Startup order: Ollama → nova-tools → nova-api → NovaHub (nova-api is a `Wants=` soft dependency for NovaHub — if nova-api fails, NovaHub still starts).

**You don't need to start anything.** Just open `http://localhost:3000` in a browser.

## What's still manual

These are on-demand tools, not background services:

```
# Obsidian vault (if you want the visual editor)
~/Downloads/Obsidian-1.12.7.AppImage --no-sandbox &

# nova-tools agent stack (for vault operations / memory queries)
cd ~/nova-tools
.venv/bin/python vault_operations.py read "04_Logs/WORKLOG.md"
.venv/bin/python index_memory.py search "any question"

# OpenCode agent session
opencode

# Git push to remote
cd ~/nova-vault
git add . && git commit -m "NR-NNN: message"
git push origin main
```

## Troubleshooting

### NovaHub doesn't load

```
# Check the service
systemctl --user status novahub.service
journalctl --user -u novahub.service -n 30 --no-pager

# Restart it
systemctl --user restart novahub.service
```

### NovaHub loads but shows stale data (500 errors)

This usually means the Prisma enums don't match the DB. Common cause: a service status was set to a value not in `ServiceStatus` enum (`active`, `offline`, `online` only).

```
# Check if nova-api is healthy
curl http://localhost:8766/health

# Check the DB directly
sqlite3 ~/nova-vault/99_Meta/nova.db "SELECT DISTINCT status FROM Service"

# Fix off-enum values, then restart NovaHub
systemctl --user restart novahub.service
```

### All services check (verbose)

```
systemctl --user status nova-tools.service nova-api.service novahub.service --no-pager -l
```

## Quick reference

| Endpoint | What |
|----------|------|
| `http://localhost:3000` | NovaHub dashboard (14 tabs) |
| `http://localhost:8765` | MCP server (SSE — vault ops + search + plugins) |
| `http://localhost:8766` | Nova API sidecar (REST — stats, ollama proxy, vault, chat, RAG, TTS) |
| `http://localhost:11434` | Ollama API — 6 models on ROCm 7.2 GPU |
| `~/nova-vault/` | Vault root (git repo, remote at `github.com/RavehnL/nova-vault`) |
| `~/nova-vault/99_Meta/nova.db` | Vault database (SQLite — NovaHub backend) |
| `~/nova-tools/novahub/` | Dashboard source (Next.js 16) |
| `~/nova-tools/vault_operations.py` | Vault read/write/append tool |
| `~/nova-tools/index_memory.py` | Semantic memory (LanceDB at `~/.hermes/lancedb`) |
| `~/nova-tools/mcp_server.py` | MCP server (port 8765) |
| `~/nova-tools/nova_api.py` | API sidecar (port 8766) |
| `~/nova-tools/deploy.sh` | One-command redeploy |
| `~/.nova/config.yaml` | Central config — ollama, vault, lancedb, ports |

## Boot log

```bash
journalctl --user -u nova-tools.service --no-pager -n 30
journalctl --user -u nova-api.service --no-pager -n 30
journalctl --user -u novahub.service --no-pager -n 50
journalctl -u ollama.service --no-pager -n 20
```
