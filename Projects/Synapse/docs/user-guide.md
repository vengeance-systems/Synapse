---
tags:
  - type/guide
  - project/synapse
  - domain/vault
  - audience/all
---

# Synapse — User Guide

## Reading the Vault

1. **Start at the index** — Open any `_index.md` to see what's available in that section
2. **Use the graph view** — Notes are color-coded by `type/*` tags (blue = index, green = architecture, etc.)
3. **Follow WikiLinks** — `[[Bracket links]]` connect related concepts across the entire vault

## Organizing Content

### When adding a new note:
1. Place it in the right folder (`Projects/<Name>/`, `Memory/`, etc.)
2. Add `type/*` frontmatter tag for graph coloring (see protocol §5)
3. Add a `domain/*` tag to indicate scope (vault, project, cross-cutting)
4. Add relevant `project/*` tags if it relates to specific projects
5. Link it from the nearest `_index.md`

### When creating a new project:
1. Create `Projects/<Name>/_index.md` as the hub
2. Create `Projects/<Name>/Architecture.md` for system design
3. Create `Projects/<Name>/Workspace.md` for active goals
4. Create `Projects/<Name>/Tech Stack/` for technology documentation
5. Add a `docs/` subdirectory for user-facing docs
6. Link `_index → docs/` for graph view connectivity

## AI Sessions

When AI sessions work with this vault:
- They follow the protocol in `System/OpenCode Workspace & Memory Protocol.md`
- They use MCP tools (never direct filesystem access)
- They document everything they find in the appropriate vault location
- They write preferences and patterns to `Memory/`
- They update workspace status and progress as they go

## Maintenance

- **Consolidate Memory** periodically — merge related notes, archive stale ones
- **Check graph colors** — if they break, restore from a saved `graph.json`
- **Keep docs in sync** — vault copies and codebase `docs/` folders should match
