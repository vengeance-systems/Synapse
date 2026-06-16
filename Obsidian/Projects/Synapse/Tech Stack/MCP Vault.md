---
tags:
  - type/reference
  - domain/tech-stack
  - audience/both
  - project/synapse
---

# Tech Stack — MCP Vault Server

## Role
The MCP Vault server (e.g., `mcpvault`) exposes the Obsidian vault as MCP tools that AI assistants can use. It's the bridge between the filesystem vault and AI sessions.

## Configuration
- **Config**: Managed via the AI client's MCP configuration file
- **Purpose**: Makes vault tools available to AI sessions
- **Scope**: Can be project-local or system-wide

## Available Tools
All tools are typically prefixed with a vault namespace (e.g., `vault_`):
- `read_note` / `write_note` / `patch_note` / `delete_note`
- `read_multiple_notes`
- `search_notes`
- `get_frontmatter` / `update_frontmatter`
- `manage_tags` / `list_all_tags`
- `list_directory`
- `get_notes_info` / `get_vault_stats`
- `move_note` / `move_file`

## Access Rules
- **NEVER** use direct filesystem access (bash, cat, Write, glob, grep) on vault contents
- Direct access only for vault configuration (directory structure, file moves) and only when explicitly requested
- This avoids permission prompts during normal coding sessions

## Related
- [[Projects/Synapse/Tech Stack/Overview|Stack Overview]]
- [[Projects/Synapse/Tech Stack/OpenCode Integration|OpenCode Integration]]
