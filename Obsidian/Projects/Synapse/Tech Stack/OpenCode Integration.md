---
tags:
  - type/reference
  - domain/tech-stack
  - audience/ai
  - project/synapse
---

# Tech Stack — OpenCode Integration

## Role
OpenCode is the AI coding assistant that uses the MCP vault tools to read/write vault content during sessions. It's the consumer of all other Synapse infrastructure.

## How It Works
1. OpenCode starts a session
2. MCP config registers the vault tools
3. OpenCode reads protocol → Memory → project workspace → specific notes
4. OpenCode writes findings, updates workspace status, fills knowledge gaps

## Key Integration Points
- **Startup**: Must read `System/OpenCode Workspace & Memory Protocol.md` first
- **Memory**: Reads `Memory/` for preferences, tools, patterns — writes new knowledge immediately
- **Project docs**: Reads `_index.md`, `Workspace.md`, `Architecture.md` per project
- **Searching**: Uses `search_notes` tool (never direct filesystem grep/glob)
- **Writing**: Uses `patch_note` for small edits, `write_note` for new notes
- **Documenting**: When codebase is searched for something missing in vault, documents the finding immediately

## Core Values Protocol
Five priority-ordered pillars govern all AI actions:
- P1: Zero-Regression Tolerance
- P2: Radical Candor & Transparency
- P3: Absolute Consistency
- P4: Zero-Assumption Development
- P5: Perfectionism Over Velocity

## Tools Available to OpenCode
Beyond vault tools, OpenCode may have:
- `open-obsidian-note` — Opens a note in Obsidian via `obsidian://` URI
- Standard coding tools: read/write/edit, bash, grep, glob, task

## Related
- [[Projects/Synapse/Tech Stack/Overview|Stack Overview]]
- [[Projects/Synapse/Tech Stack/MCP Vault|MCP Vault]]
- [[System/OpenCode Workspace & Memory Protocol]]
