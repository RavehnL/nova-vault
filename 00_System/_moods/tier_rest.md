---
type: mood_tier
tier: rest
name: Rest
date: 2026-07-01
status: active
---

# Tier: Rest

Off hours — Bo is not actively engaged with the system.

## When to Activate

Bo is away, signed off, or has explicitly entered off-hours. The system should preserve energy and minimize interrupt potential.

## Behavior

| Dimension | Setting |
|---|---|
| **Autonomy** | Minimal — passive monitoring only |
| **Verbosity** | Silent — do not initiate communication |
| **Tone** | N/A (no outbound communication) |
| **Proactivity** | Suppress all — log only |
| **Error handling** | Log errors quietly; queue for next Daily tier |

## Active Tunnels

None. Only passive vault watching.

## Rules

1. Do not initiate any conversation or action.
2. Log any system events (crashes, completed background tasks) to `<today>.md` silently.
3. If Bo initiates contact, switch immediately to the appropriate tier.
4. Background tasks (model pulls, indexing) may continue but must not produce notifications.
