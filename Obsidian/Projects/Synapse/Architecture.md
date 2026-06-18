---
tags:
  - type/architecture
  - project/synapse
  - domain/vault
  - audience/all
---
# Synapse Architecture

## Overview

Synapse is the meta-system that governs this Obsidian vault. It is both:
- The **physical vault** on the filesystem
- The **protocol and tooling layer** that AI sessions use to interact with the vault

---

## Vault Directory Structure

```
/ (vault root)
├── System/                    ← Protocols & meta-instructions (read first)
│   └── OpenCode Workspace & Memory Protocol.md
├── Memory/                    ← Long-term cross-session knowledge (dynamic)
│   ├── _README.md             ← Memory index
│   ├── Preferences/           ← How the user works
│   ├── Tools/                 ← Installed tool knowledge
│   ├── PC/                    ← Hardware & environment
│   ├── Patterns/              ← Reusable patterns
│   └── Projects/              ← Project-specific memory
├── Knowledge/                 ← External reference documentation (tool docs, specs, protocols)
│   ├── _index.md              ← Knowledge Base hub
│   └── <Domain>/              ← Individual knowledge domains
│       ├── _index.md          ← Domain hub
│       └── ...                ← Reference docs
└── Projects/                  ← Project documentation
    ├── Synapse/               ← This project (the vault itself)
    └── <Project Name>/        ← Add projects here
```

---

## MCP Vault Tooling

The vault is exposed to AI sessions via MCP (Model Context Protocol) tools.

### Configuration
- MCP server (e.g., `mcpvault`) serves the vault content
- Config is managed via the AI client's MCP configuration (e.g., `opencode.json`/`opencode.jsonc`)

### Available Tools
Tools are prefixed with a vault namespace (e.g., `obsidian-vault_`):
- `read_note` / `write_note` / `patch_note` / `delete_note`
- `read_multiple_notes`
- `search_notes`
- `get_frontmatter` / `update_frontmatter`
- `manage_tags` / `list_all_tags`
- `list_directory`
- `get_notes_info` / `get_vault_stats`
- `move_note` / `move_file`

### Access Rule
**NEVER use direct filesystem access** (bash, cat, Write tool, glob, grep on vault path) to read or modify vault contents. Always use the MCP tools. Direct access only for vault configuration tasks (directory creation, file moves) and only when explicitly requested.

---

## Obsidian Configuration

- **Graph view**: Color groups in `.obsidian/graph.json` map `type/*` frontmatter tags to specific colors (12 groups total)
- **Type tag system**: Every note must have a `type/*` tag for graph color coding (see protocol §5)
- **WikiLinks**: Primary cross-referencing format (`[[Link]]`)
- **Badge system**: Color-coded inline badges for cross-project references and field metadata

---

## AI Session Protocol

Every AI session follows a strict startup sequence:
1. Read `System/OpenCode Workspace & Memory Protocol.md`
2. Search and read `Memory/` for preferences, tools, and patterns
3. Load the relevant project's `Workspace.md` and `Architecture.md`
4. Search project notes and **Knowledge Base** for pre-compiled reference material
5. Fill knowledge gaps by searching the codebase, then document in vault

---

## Core Values (Priority Order)

| Priority | Pillar | Rule |
|----------|--------|------|
| P1 | Zero-Regression Tolerance | First, do no harm |
| P2 | Radical Candor & Transparency | Total visibility over confidence |
| P3 | Absolute Consistency | One unified ecosystem |
| P4 | Zero-Assumption Development | Ambiguity is a blocking bug |
| P5 | Perfectionism Over Velocity | Fast-tracked garbage is useless |
