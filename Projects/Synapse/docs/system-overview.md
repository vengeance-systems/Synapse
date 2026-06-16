---
tags:
  - type/reference
  - project/synapse
  - domain/vault
  - audience/all
---

# Synapse — System Overview

Synapse is an Obsidian vault system designed as a persistent knowledge base that AI sessions and humans share — the vault holds the context, the AI reads and writes to it, and users navigate it visually through Obsidian's graph view.

## What It Does

- **Stores project documentation** — architecture, API specs, data structures
- **Remembers AI preferences** — communication style, coding conventions, tool knowledge
- **Connects everything** — via WikiLinks and graph view color groups
- **Governs AI conduct** — through the protocol in `System/`

## How It's Organized

```
System/         ← Rules for AI (read this first)
Memory/         ← What the AI knows about preferences, tools, patterns
Projects/       ← Actual work (each project gets a folder)
```

## Key Features

- **Type-tagged graph coloring**: Every note has a `type/*` tag so the graph view is color-coded
- **MCP-powered AI access**: AI sessions use dedicated tools (not filesystem) to read/write notes
- **Cross-linked hubs**: Every project has an `_index.md` that links to everything within it
- **Self-documenting**: The vault documents its own architecture (you're reading it)

## For More

- [[Projects/Synapse/docs/user-guide|User Guide]] — How to use the vault
- [[Projects/Synapse/docs/principles|Principles]] — Design decisions
- [[Projects/Synapse/Architecture|Architecture]] — Deep technical details
