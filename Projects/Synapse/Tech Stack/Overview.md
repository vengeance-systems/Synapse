---
tags:
  - type/reference
  - domain/tech-stack
  - audience/both
  - project/synapse
---

# Synapse — Tech Stack Overview

## Stack Summary

| Layer | Technology | Detail |
|-------|-----------|--------|
| **Vault App** | Obsidian | Electron-based markdown note-taking app with graph view |
| **MCP Server** | mcpvault | MCP server exposing vault content to AI sessions |
| **AI Client** | OpenCode | AI coding assistant that consumes MCP tools |
| **Runtime** | Node.js | Runtime for the MCP server |
| **OS** | Linux | Any Linux distribution (Arch, Debian, etc.) |
| **Config** | JSON / JSONC | AI client configuration for MCP tool registration |
| **URI Scheme** | obsidian:// | Opens notes in Obsidian via Electron IPC |

## Key Characteristics
- **No build step** — Notes are plain markdown files with YAML frontmatter
- **MCP-accessible** — All vault content exposed via standardized MCP tools
- **Graph-colored** — 11 `type/*` tag groups color-code the Obsidian graph view
- **Cross-linked** — WikiLinks connect all notes into a navigable network
- **AI-native** — Designed for AI-assisted read/write via protocol-governed sessions

## Architecture Diagram
```
User (Obsidian App)          AI (OpenCode)
       │                           │
       │ graph view, WikiLinks     │ MCP protocol (vault_* tools)
       │                           │
       └───────── vault ───────────┘
                 │
           vault root
                 │
         ┌───────┴────────┐
         │                │
    System/          Projects/
    Memory/           Synapse/
                      <projects...>
```

## Related
- [[Projects/Synapse/Architecture|Architecture]]
- [[Projects/Synapse/Tech Stack/Obsidian|Obsidian]]
- [[Projects/Synapse/Tech Stack/MCP Vault|MCP Vault]]
- [[Projects/Synapse/Tech Stack/OpenCode Integration|OpenCode Integration]]
- [[Projects/Synapse/Tech Stack/Environment|Environment & Tools]]
- [[System/OpenCode Workspace & Memory Protocol]]

## Sub-pages
- [[Projects/Synapse/Tech Stack/Obsidian|Obsidian]]
- [[Projects/Synapse/Tech Stack/MCP Vault|MCP Vault]]
- [[Projects/Synapse/Tech Stack/OpenCode Integration|OpenCode Integration]]
- [[Projects/Synapse/Tech Stack/Environment|Environment & Tools]]
