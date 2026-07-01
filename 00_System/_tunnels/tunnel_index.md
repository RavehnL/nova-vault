---
type: tunnel_index
date: 2026-07-01
status: active
---

# Tunnel Index

Tunnels are scoped attention channels that constrain reasoning to a specific domain. Syzygy loads only the relevant tunnel context to prevent context bleed and reduce noise from over-generalization.

## Active Tunnels

| Tunnel | Scope | When Active |
|---|---|---|
| `tunnel_survival` | Income generation, 70/30 rule, bounties | Survival tier |
| `tunnel_vault` | File maintenance, daily note, knowledge indexing | All tiers |
| `tunnel_infra` | System config, services, ports, dependencies | Build tier |
| `tunnel_research` | Deep reading, web search, knowledge compounding | Explore tier |
| `tunnel_build` | Active project work, sprint deliverables | Build tier |

## Tunnel Structure

Each tunnel file defines:
- **Scope** — what is in bounds
- **Boundaries** — what is out of bounds (to prevent bleed)
- **Linked files** — relevant SOPs, configs, and notes
- **Allowed actions** — read, write, execute, etc.
- **Exit criteria** — when to close the tunnel
