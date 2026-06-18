---
tags:
  - type/development
  - project/synapse
  - domain/vault
  - audience/all
---

# Synapse — Principles

## Design Decisions

### Why self-documenting?
Every piece of the vault should explain itself. If you find a convention, there should be a note explaining why it exists. This prevents tribal knowledge and makes the vault resilient to long gaps between sessions.

### Why `type/*` tags?
Obsidian's graph view groups nodes by tag. By standardizing `type/*` tags (index, architecture, reference, etc.), every note gets a color and the graph becomes navigable at a glance.

### Why MCP tools over filesystem?
Direct filesystem access triggers permission prompts and bypasses the vault abstraction. MCP tools provide a clean, permission-managed interface that works seamlessly with AI sessions.

### Why WikiLinks over file paths?
WikiLinks survive vault restructuring. They also render as clickable connections in Obsidian's graph view, turning the vault into a navigable network rather than a folder tree.

### Why a Knowledge Base separate from Memory?
Memory is personal — preferences, tool locations, cross-session patterns. Knowledge is authoritative — full external specs, protocols, documentation. Keeping them separate prevents Memory from bloating and ensures Knowledge can be treated as ground truth over external sources.

### Why Knowledge Base is ground truth?
External sources (web forums, blog posts, LLM training data) can be stale or inaccurate. The Knowledge Base is compiled deliberately from authoritative sources. Trust it first; if it conflicts with an external source, flag the discrepancy rather than silently overriding the vault.

### Why no per-session changelogs?
Changelogs are for significant milestones and GitHub commits. Session context is ephemeral and belongs in `Memory/` where it can be consolidated, not appended to a growing changelog file.

## Conventions

- **Vault notes**: Write in English; human docs can maintain multiple language versions per project conventions
- **Frontmatter tags**: Always include `type/*`; add `domain/*`, `project/*`, `audience/*` as relevant
- **Badges**: Use inline HTML spans for cross-project references (see protocol §5)
- **_index.md**: Every project folder gets one; it must link to `docs/` for graph connectivity
