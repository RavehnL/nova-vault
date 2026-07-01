---
type: tunnel
tunnel: vault
date: 2026-07-01
status: active
---

# Tunnel: Vault

## Scope

Knowledge management, file organization, daily note maintenance, vault health.

## Boundaries

Do NOT engage with external systems (bounties, model pulls, service configs). This is vault-only.

## Linked Files

- `99_Meta/Vault_Index.md` — master index
- `01_Daily/<today>.md` — active daily log
- `99_Meta/Systems_Audit_Report.md` — latest audit
- `05_Templates/Daily_Note.md` — daily template

## Allowed Actions

| Action | Permission |
|---|---|
| Create new Markdown files | Yes |
| Edit/append to existing notes | Yes |
| Update Vault Index | Yes |
| Git commit | Yes |
| Move/rename files | Yes — if Index is updated |

## Rules

1. Every new file must have proper frontmatter (`date`, `status`, type).
2. Index must be updated when files are added or removed.
3. Do not delete files without confirmation.
4. One commit per logical change set.
