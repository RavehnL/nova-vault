---
type: system_core_reference
date: 2026-07-01
status: active
---

# Nova Project — Startup Guide

Cold-boot procedure after computer restart. Everything is local — no cloud dependencies.

## After restart, these start automatically

| Service          | Auto                    | Verifies via                    |
| ---------------- | ----------------------- | ------------------------------- |
| **Ollama**       | systemd (enabled)       | `curl localhost:11434/api/tags` |
| **UFW firewall** | systemd (enabled)       | `ufw status`                    |
| **NovaHub**      | systemd (user, enabled) | open `http://localhost:3000`    |
| **nova-tools (MCP)** | systemd (user, enabled) | `curl http://localhost:8766/health` |
| **nova-api**     | systemd (user, enabled) | `curl http://localhost:8766/system/stats` |

**You don't need to start anything.** Just open `http://localhost:3000` in a browser. NovaHub, Ollama, MCP, API sidecar, and the vault DB are all live.

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
```

## If NovaHub doesn't load

```
# Check the service
systemctl --user status novahub.service
journalctl --user -u novahub.service -n 30 --no-pager

# Restart it
systemctl --user restart novahub.service
```

## Quick reference

| Endpoint | What |
|----------|------|
| `http://localhost:3000` | NovaHub dashboard (14 tabs) |
| `http://localhost:8765` | MCP server (SSE — vault ops + search) |
| `http://localhost:8766` | Nova API sidecar (REST — stats, ollama proxy, vault, chat, RAG, TTS) |
| `http://localhost:11434` | Ollama API |
| `~/nova-vault/99_Meta/nova.db` | Vault database (SQLite) |
| `~/nova-tools/novahub/` | Dashboard source |
| `~/nova-tools/vault_operations.py` | Vault read/write tool |
| `~/nova-tools/index_memory.py` | Semantic memory (LanceDB) |
| `~/nova-tools/mcp_server.py` | MCP server (port 8765) |
| `~/nova-tools/nova_api.py` | API sidecar (port 8766) |
| `~/.nova/config.yaml` | Central config |

## Boot log

```bash
journalctl --user -u novahub.service --no-pager -n 50
journalctl -u ollama.service --no-pager -n 20
```
