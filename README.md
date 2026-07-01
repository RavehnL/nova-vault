# Nova

Local-first AI workstation. No cloud. All yours.

## What Is This?

A giant folder (`nova-vault/`) that me and the AI share. I write objectives and read summaries. The AI reads timelines, does tasks, and logs everything back. We stay synced through the daily notes.

## Vault Layout (What Goes Where)

| Folder | What It's For |
|---|---|
| `00_System/` | The rules. Manifesto, timeline, quick-refs. Read these if you're lost. |
| `01_Daily/` | Daily notes. One file per day. Start here every morning. |
| `02_Projects/` | Active stuff I'm working on. |
| `03_Knowledge/` | Research, notes, things I want to keep. |
| `04_Logs/` | Old logs, history. |
| `05_Templates/` | Note templates. Don't edit these — copy them. |
| `99_Meta/` | Indexes, audit reports, vault meta. |

## How to Use This

1. **Open Obsidian** → it opens to `nova-vault` automatically
2. **Read today's note** in `01_Daily/`
3. **Check the Timeline** (`00_System/`) to see where we're at
4. If you want the AI to do something, put it in today's note under **Human Objectives**
5. The AI logs what it did under **Agent Activity Log**

## Where Are Things Installed?

- **Obsidian** — AppImage at `~/Downloads/Obsidian-1.12.7.AppImage` (click to run)
- **Ollama** — not yet working (broken download, needs fixing)
- **Hermes agent** — cloned to `~/hermes-agent/`, not set up yet
- **ROCm (GPU drivers)** — installed and working
- See `00_System/Agent_Quick_Reference.md` for the full list

## Current Status

Day 1 of a 30-day sprint. Vault structure is seeded. GPU is working. Obsidian is connected. Next up: getting Ollama running so we can start pulling AI models.

## File Rules (for the humans)

- Every file has frontmatter at the top (`type:`, `date:`, `status:`)
- Don't delete or rename folders without updating the Index
- Commit to git when things feel important

## Git

```
git log --oneline  # see what changed
git add . && git commit -m "message"  # save your work
```

No remote yet — everything lives on this machine only.

---

*Built on Ubuntu 26.04 with an AMD RX 9060 XT and zero cloud calls.*
