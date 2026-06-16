---
tags:
  - type/progress
  - project/synapse
  - domain/vault
  - audience/ai
---

# Synapse — Workspace

> Active goals, constraints, and priorities for documenting and maintaining the vault system itself.

## Active Goals

- [x] Create Synapse project structure (hub, architecture, tech stack, docs)
- [x] Document vault architecture and MCP tooling
- [ ] Document all project conventions in a central principles note
- [ ] Create a changelog for significant vault-level changes
- [ ] Ensure all existing notes have proper `type/*` tags for graph view

## Principles & Constraints

- **Self-documenting**: The vault documents itself. Everything should be findable from the hub.
- **Protocol-first**: `System/OpenCode Workspace & Memory Protocol.md` is the single source of truth for AI conduct.
- **Memory is dynamic**: Preferences, tools, and patterns go in `Memory/` — not in project docs.
- **No direct filesystem access**: Always use MCP tools for vault content operations.
- **Cross-link everything**: No note is an island. Link `_index → docs/` for graph view connectivity.

## Rollout Items

| Item | Status | Notes |
|------|--------|-------|
| Vault structure docs | ✅ Done | Architecture.md covers full layout |
| MCP tooling docs | ✅ Done | Included in Architecture.md |
| Synapse project docs | ✅ Done | _index.md, Architecture.md, Workspace.md, Tech Stack/ |
| Human docs (docs/) | ✅ Done | system-overview.md, user-guide.md, principles.md |

## Related

- [[Projects/Synapse/Architecture]]
- [[Projects/Synapse/_index]]
- [[System/OpenCode Workspace & Memory Protocol]]
