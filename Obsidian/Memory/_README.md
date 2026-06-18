---
tags:
  - type/index
  - memory/root
  - audience/ai
---
# /Memory — Long-Term Knowledge

> **Purpose**: Cross-cutting persistent knowledge that spans multiple projects and sessions. This is the most dynamic part of the vault — capture everything here.

## Structure

```
Memory/
├── _README.md                 ← This file (nav)
├── Preferences/               ← How I work, communicate, code
├── Tools/                     ← Installed tools I can use
├── PC/                        ← Hardware and environment
├── Patterns/                  ← Reusable patterns
└── Projects/                  ← Project-specific memory
    └── <Project Name>/        ← Cross-session memory per project
```

## Usage
- **Read**: Search Memory at session start for relevant context
- **Write**: Add immediately when you learn something new — even tiny things
- **Maintain**: Consolidate related notes, remove stale entries
- **Search**: Use `search_notes` rather than reading everything

## Knowledge Base

The vault also maintains a **Knowledge Base** at `Knowledge/` for comprehensive external reference material (tool docs, specs, protocols). This is separate from Memory:
- **Memory** = personal preferences, tool locations, cross-session patterns (here)
- **Knowledge** = full-depth external documentation for tools, languages, protocols

When you need to look up how a tool works, check `Knowledge/` first before searching external sources. Browse all registered domains at [[Knowledge/_index|Knowledge Base Hub]].

## Notes
- (Populate as Memory grows)

## Related
- [[Knowledge/_index|Knowledge Base Hub]]
- [[System/OpenCode Workspace & Memory Protocol|Vault Protocol]]
