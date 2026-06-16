# Synapse — The Vault System

**Synapse** is an Obsidian vault that serves as a personal knowledge management system documenting architecture, protocols, tools, and conventions — the connective tissue between projects and memory.

## Structure

```
.
├── Obsidian/              ← The Obsidian vault (open this folder in Obsidian)
│   ├── System/            ← Meta-instructions & vault protocols
│   ├── Memory/            ← Long-term cross-session knowledge
│   └── Projects/          ← Project-specific documentation
│       ├── Synapse/       ← Vault system itself
│       ├── Sentinel Flow/ ← Project A
│       └── VGOS/          ← Project B
├── .gitignore
└── README.md
```

## Getting Started

1. Clone the repo
2. Open `Obsidian/` as a vault in Obsidian (open folder → select `Obsidian/`)
3. Enable the graph view to explore linked notes

## Stack

- **Obsidian** — Note-taking app with graph view
- **MCP Vault** — Server exposing the vault via MCP tools
- **OpenCode** — AI assistant consuming the vault

## License

MIT
