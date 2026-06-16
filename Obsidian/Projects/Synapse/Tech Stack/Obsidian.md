---
tags:
  - type/reference
  - domain/tech-stack
  - audience/both
  - project/synapse
---

# Tech Stack — Obsidian

## Role
Obsidian is the primary user-facing interface for the vault. It renders markdown notes, the graph view, and provides the editing environment.

## Key Features Used
- **Graph view** — Color groups via `.obsidian/graph.json` map `type/*` tags to 11 colors
- **WikiLinks** — `[[Note Name]]` cross-referencing
- **Frontmatter** — YAML metadata for tags, type classification
- **Folder structure** — `System/`, `Memory/`, `Projects/` hierarchy
- **Electron IPC** — `obsidian://` URI scheme opens notes programmatically

## Configuration
- Vault root: configured via Obsidian's vault picker
- Graph config: `.obsidian/graph.json` (11 color groups, can be silently overwritten)

## Quirks
- `graph.json` color groups are **fragile** — Obsidian can blank them when saving without loaded groups. Back up your graph configuration.

## Related
- [[Projects/Synapse/Tech Stack/Overview|Stack Overview]]
