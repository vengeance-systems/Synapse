---
tags:
  - type/reference
  - domain/tech-stack
  - audience/both
  - project/synapse
---

# Tech Stack — Environment & Tools

## Host OS
- Any Linux distribution with Obsidian support

## Filesystem
- **Vault root**: Configurable location (e.g., `~/vault`, `/var/lib/vault`, etc.)
- The vault can be symlinked for system-wide access

## AI Client Config
- MCP server configuration in the AI client's config file
- Registers vault tools for AI session use

## Supporting Tools

### obsidian:// URI Scheme
- **Purpose**: Opens notes in Obsidian from outside the app
- **Mechanism**: Electron IPC via Obsidian's registered URI handler

## Path Map (Example)
| Logical Path | Example Physical Path |
|-------------|---------------------|
| Vault root | `/var/lib/vault` → `/home/user/vault` |
| MCP binary | `mcpvault` (e.g., installed via npm or from releases) |
| MCP config | AI client config file (e.g., `opencode.json`) |
| Obsidian data | `vault/.obsidian/` |

## Related
- [[Projects/Synapse/Tech Stack/Overview|Stack Overview]]
