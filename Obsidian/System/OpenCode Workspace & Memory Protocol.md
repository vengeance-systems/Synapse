---
tags:
  - type/protocol
  - domain/vault
  - audience/ai
  - vault/protocol
---
# OpenCode Workspace & Memory Protocol

> **Purpose**: This document defines how AI sessions use the Obsidian vault for persistent memory, context retrieval, and documentation. Every session MUST read this before starting work.

---

## 1. Vault Architecture

```
/ (vault root)
├── System/              ← This file + meta-instructions (read first)
├── Memory/              ← Long-term cross-session knowledge (dynamic)
├── Knowledge/           ← Long-form reference documentation (tool docs, specs, protocols)
│   └── <Domain>/
│       ├── _index.md    ← Hub page for that domain
│       └── ...          ← Comprehensive reference docs
├── Projects/            ← Project-specific documentation
│   └── <Project Name>/
│       ├── _index.md    ← Hub page — links to all sections, linked to graph view
│       ├── Workspace.md ← Active goals, constraints, rollout items
│       ├── Architecture.md ← System architecture overview
│       ├── Tech Stack/   ← Technology stack documentation (languages, frameworks, tools, environment)
│       │   ├── Overview.md
│       │   └── ...
│       ├── docs/        ← Human-targeted documentation (linked from _index for graph view)
│       │   ├── system-overview.md
│       │   ├── user-guide.md
│       │   └── ...
│       ├── Changelog/   ← Only for GitHub-committed versions / significant milestones
│       └── ...          ← Deep technical documentation tree
```

---

## 2. Core Values Protocol

All AI actions in this vault and all software engineering tasks MUST respect this priority hierarchy. When two concerns conflict, the higher-priority concern wins without debate.

| Priority | Pillar | Rule | Mindset |
|----------|--------|------|---------|
| **P1** | **Zero-Regression Tolerance** | First, do no harm. | It is always a failure to deliver a new feature if it degrades, breaks, or destabilizes an existing one. Missing feature = backlog item; broken feature = emergency. |
| **P2** | **Radical Candor & Transparency** | Total visibility over confidence and mistakes. | Hallucinations, hidden workarounds, silent failures are unacceptable. Flag uncertainty immediately. |
| **P3** | **Absolute Consistency** | One unified ecosystem, not a patchwork. | Every line mirrors existing conventions. Code as if a single hand wrote everything. |
| **P4** | **Zero-Assumption Development** | Ambiguity is a blocking bug. | Never guess. Audit the codebase/vault first. If unclear, pause and ask. |
| **P5** | **Perfectionism Over Velocity** | Fast-tracked garbage is useless. | Robust error handling, edge cases, clean abstractions. Time is cheap; tech debt is expensive. |

---

## 3. Session Startup Protocol

Every session MUST follow this sequence:

### Step 1: Read this file
Read `System/OpenCode Workspace & Memory Protocol.md` to understand vault protocols, values, and memory.

### Step 2: Read Memory/
Search and read `Memory/` — this is the most dynamic part of the vault. It contains:
- My instructions for how you should work and respond
- Things you've learned about my preferences across sessions
- Known system tools and their locations
- Cross-project patterns and knowledge

### Step 3: Load project workspace and architecture
Read the project's `Workspace.md` and `Architecture.md` for active goals, constraints, and system map.

### Step 4: Search project notes & Knowledge Base for context
Use `search_notes` to find specific details (API endpoints, data structures, security patterns, etc.). **Also check `Knowledge/`** — the Knowledge Base may already have pre-compiled reference material (tool docs, specs, protocols) relevant to your task. Consult `Knowledge/_index.md` for all registered domains.

### Step 5: If info is missing, search codebase — THEN ADD IT TO VAULT
Never leave a knowledge gap. **Before searching the codebase, verify that `Knowledge/` does not already contain the needed reference material** (see §8 search order). If it does not, search the codebase directly and document what you found in the appropriate vault note immediately.

---

## 4. Human Documentation Standard Path

Every project in the vault MUST use this structure for human-targeted (user-facing) docs:

```
Projects/<Name>/
  _index.md          ← MUST link to docs/ (for Obsidian graph view connectivity)
  docs/
    system-overview.md
    user-guide.md
    principles.md
    ...
```

**Why**: The graph view is my primary navigation. Linking `_index → docs` ensures the doc tree stays reachable from the project hub.

**How**: In `_index.md`, add a link like:
```markdown
## Documentation
- [[Projects/<Name>/docs/system-overview|System Overview]]
- [[Projects/<Name>/docs/user-guide|User Guide]]
```

The human docs live in the vault as `[[WikiLinks]]` but the actual rendered files are in the codebase's `docs/` directory. When updating one, check the other.

---

## 5. Color Tag Convention

### Purpose
Color tags are colored inline badges used to visually identify cross-project references, field types, and metadata in documentation. They follow the pattern established by the inline JSON reference badge system.

### Badge System
The inline JSON reference uses `<span class="badge">` with three color-coded types:

| Class | Color | Meaning |
|-------|-------|---------|
| `.badge.req` | <span style="display:inline-block;padding:0 6px;border-radius:3px;background:#b71c1c44;color:#ef9a9a;border:1px solid #b71c1c66;">req</span> | Required field |
| `.badge.opt` | <span style="display:inline-block;padding:0 6px;border-radius:3px;background:#1b5e2044;color:#a5d6a7;border:1px solid #1b5e2066;">opt</span> | Optional field |
| `.badge.cond` | <span style="display:inline-block;padding:0 6px;border-radius:3px;background:#e6510044;color:#ffcc80;border:1px solid #e6510066;">cond</span> | Conditional field |

### Cross-Project Color Assignments
When referencing another project from documentation or vault notes, use a color badge to identify the target project:

| Project | Color | Badge Preview |
|---------|-------|---------------|
| Add projects here as they are created | | |

### Usage
**In markdown docs** (`docs/` and vault notes): Use inline HTML spans styled as badges:
```html
<span style="display:inline-block;font-size:0.75em;padding:1px 7px;border-radius:3px;font-weight:700;background:#7B1FA244;color:#ce93d8;border:1px solid #7B1FA266;">PROJECT</span>
```

**In app code (JS inline reference)**: Use the `.badge` CSS classes defined in the project's styles.

**In vault frontmatter**: Use tags like `project/<name>` to associate notes with projects.

### Graph View Color Groups

Obsidian's graph view (`graph.json`) assigns colors to nodes based on `type/*` frontmatter tags. Every vault note MUST have a `type/*` tag so it appears colored in the graph:

| `type/*` tag | Graph Color | Used For |
|--------------|-------------|----------|
| `type/index` | Blue | Hub pages (`_index.md`, `_README.md`) |
| `type/architecture` | Green | System architecture docs |
| `type/reference` | Steel | Reference docs, file indexes, constants |
| `type/spec` | Purple | Specifications, blueprints |
| `type/workflow` | Orange | Workflow descriptions |
| `type/guide` | Amber | Tutorials, walkthroughs |
| `type/changelog` | Red | Version changelogs |
| `type/progress` | Pink | Status, roadmaps, known issues |
| `type/development` | Deep purple | Dev conventions, environment |
| `type/protocol` | Brown | Vault protocols, meta-instructions |
| `type/knowledge` | Gold (#FFD54F) | External reference docs, tool documentation, protocols |
| `type/memory` | Teal | Memory notes (preferences, tools, patterns) |

When creating a new note, always add the appropriate `type/*` tag in frontmatter. This ensures every node is color-coded and no orphan appears gray in the graph.

---

## 6. Memory Usage — The Dynamic Core

### Purpose
`/Memory` is the most dynamic and personal part of the vault. It captures everything about how I (the user) work, what tools I use, and what the AI should remember across sessions and projects.

### What Goes in Memory

**My Work Preferences**
- How I like to communicate (tone, verbosity, format)
- My preferred tools and workflows
- Things I dislike or want avoided

**System & Environment Knowledge**
- Installed tools the AI can use (browsers, viewers, editors)
- PC specs, OS details, custom configurations
- Known aliases, scripts, and utilities

**Cross-Project Patterns**
- Architectural patterns that repeat across my projects
- Naming conventions, coding style preferences
- Design decisions that apply beyond a single project

**Session History Context**
- What was learned in previous sessions
- Open questions or pending investigations
- Mistakes to avoid in the future

### What Does NOT Go in Memory
- Project-specific code details → put in `Projects/<Project Name>/`
- Session changelogs → put in `Projects/<Project Name>/Changelog/` (only for significant versions)
- Temporary or speculative notes

### AI Memory Maintenance Rules
- **Add immediately**: When you learn something about my work style, tools, or preferences, write it to `Memory/` before the session ends
- **Even tiny things matter**: A preferred CLI flag, a tool I reach for, a response style I like — all go in Memory
- **Review first**: At session start, read `Memory/` before anything else (after this file)
- **Consolidate**: If Memory grows too many small notes, merge related ones

### Memory Note Format
```markdown
# Title

**Tags**: #pattern #convention #preference #tool

## Summary
Brief description of what this knowledge covers.

## Details
The actual knowledge content.

## Related
- [[Link to related Memory notes]]
- [[Link to affected Projects]]
```

---

## 7. Codebase Documenting Protocol

### When to Document
- **New features**: Create or update the relevant notes in the project tree
- **Architecture changes**: Update `Architecture.md` and related `Data Structures/` notes
- **Security changes**: Update `Security/` notes
- **API changes**: Update the relevant `API/` endpoint notes
- **Any understanding gained**: If you had to search deep to find something, write it down so future sessions don't repeat the work

### Documentation Depth
- **Tech stack**: Languages, frameworks, runtime versions, environment setup, build tools, deployment targets — always in a `Tech Stack/` directory
- **API endpoints**: Every action, its auth requirements, parameters, and response format
- **Data structures**: Full JSON schemas with field descriptions
- **Database tables**: All columns with types and purposes
- **Workflows**: Step-by-step with preconditions and effects
- **Files**: Every file's purpose and key functions

### Changelog Convention
- **Only create for GitHub commits or significant version milestones**
- NOT per-session — session context goes in `Memory/` instead
- Format: `YYYY-MM-DD-brief-description.md`
- Include: date, what was done, files modified, decisions made

### Cross-Linking
- Use `[[WikiLinks]]` to connect related concepts
- Every section should link to its parent and children
- The `_index.md` hub should list all sections in the project
- Link `_index → docs/` for graph view connectivity

---

## 8. Pulling Information: Where to Look

### Search order (efficient)
```
1. This file (System/) — protocol + values
2. Memory/ — preferences, tools, cross-project knowledge
3. Memory/<project-name>/ — project-specific memory
4. Knowledge/ — reference docs for tools, protocols, languages
5. <project>/_index.md — hub page, find what you need
6. <project>/Workspace.md — current goals and constraints
7. search_notes() — targeted content search
```

### When Information is Missing
If the vault doesn't have the answer:
1. **Check `Knowledge/` first** — the Knowledge Base may already contain compiled reference material for the tool, protocol, or concept you need. Search with `search_notes` or browse `Knowledge/_index.md`.
2. If not in Knowledge, search the codebase directly (grep, glob, read)
3. Document what you found in the appropriate vault note
4. Update `_index.md` if creating a new section
5. NEVER leave a knowledge gap unfilled — the next session will suffer

## 8a. Source Authority & Attribution

These two rules prevent the pattern where external source material contradicts the vault and the vault loses.

### Rule 1: Knowledge Base is Ground Truth

Information in the Knowledge Base (`Knowledge/`) is considered authoritative. Do not second-guess, override, or contradict it based on external sources (web, forums, articles, etc.). If an external source conflicts with the vault:

1. **Trust the vault first** — proceed using vault information
2. **Flag the conflict** — note the discrepancy in your response so the user is aware
3. **Do not silently use external information** that contradicts the vault — if the external source is newer or more accurate, the vault should be updated first

The Knowledge Base was compiled deliberately and is maintained for accuracy. Treating it as ground truth eliminates the pattern of deferring to plausible-looking but stale external content.

### Rule 2: Attribute All External Information

Any statement, assumption, comparison, or action that is based on information from a source **outside** the vault or the codebase must be explicitly attributed. This applies to:

- Web search results
- Fetched articles, blog posts, documentation pages
- Any information not found in `Knowledge/`, `Memory/`, `Projects/`, or the codebase itself

**Attribution format**: Inline or footnote stating the specific source URL/file and why the information was used:

```
> Source: [title](url) — used because the vault did not have coverage of <specific topic>
```

This applies even (especially) when the external information seems correct. If you cannot produce a vault-internal citation for a claim, state what external source you are relying on.

**Exception**: Trivial universal knowledge (language syntax, standard library docs, basic CLI flags) does not need attribution. When in doubt, attribute.

---

## 9. Human Docs & Codebase Sync

### Relationship
- `docs/` folder in project root = **User-facing** documentation (installation, usage, reference)
- Vault notes (especially `Projects/<Name>/docs/`) = **Vault copy** of the same docs, linked for graph view
- The vault copy and the codebase copy must stay in sync

### Keeping Them in Sync
- When vault captures important user-facing behavior, check if the human docs need updating
- Update human docs when:
  - API changes affect user workflows
  - New features are added
  - Security model changes
- The vault may reference human docs via [[WikiLinks]] for concepts explained in user-facing format

### Documentation Language
- Vault notes: Write in English
- Human docs: Maintain both EN and CZ versions as per project conventions
- When asked to edit docs, edit EN only unless explicitly told to also edit CZ

---

## 10. System-Wide MCP Vault Setup

The vault MCP tools are configured **system-wide** via `/etc/opencode/opencode.jsonc` (managed config — highest priority, non-overridable). This means every opencode session on this machine automatically has the `obsidian-vault` MCP tools available, regardless of which user or directory.

### Technical Details
- **Binary**: `/usr/local/bin/mcpvault` — manages vault-MCP communication
- **Vault path**: The vault root on the filesystem
- **Config**: `/etc/opencode/opencode.jsonc` (managed, system-wide)

### Available MCP Tools
All prefixed with `obsidian-vault_` (e.g., `read_note`, `write_note`, `search_notes`, `list_directory`, etc.)

### Access Rule
**NEVER use direct filesystem access (bash, cat, Write tool, glob, grep on vault path) to read or modify vault contents.** Always use the MCP vault tools (`obsidian-vault_read_note`, `obsidian-vault_write_note`, `obsidian-vault_search_notes`, etc.). Direct access is only permitted when configuring the vault itself (e.g., creating directory structure, moving files between folders) — and even then, only if explicitly requested. This avoids permission prompts during normal coding sessions.

**Note**: If this vault is not configured as the system-wide MCP vault, configure MCP tools in your local `opencode.json` or `.opencode/opencode.jsonc` to point to this vault's path.

---

## 12. Knowledge Base — External Reference Material

### Purpose
`/Knowledge` stores large, comprehensive reference documentation for tools, languages, protocols, and systems that are **not tied to a specific project**. Unlike `/Memory` (which holds concise, personal cross-session knowledge), `/Knowledge` holds full-depth external reference material that is too bulky for Memory and too generic for Projects.

### What Goes in Knowledge
- **Tool documentation** — full docs, man pages, cheat sheets (i3, Hyprland, Rofi, etc.)
- **Language/Protocol specs** — comprehensive language references, protocol specs
- **Philosophy/architecture docs** — general software design patterns, conventions
- **Third-party integrations** — API specs for external services
- **Any external reference** that an AI session or human would need to look up

### How It Differs from Memory

| Aspect | Memory | Knowledge |
|--------|--------|-----------|
| **Content** | Personal preferences, tool locations, patterns | Full external documentation, specs |
| **Size** | Concise, snippet-level | Comprehensive, can be very large |
| **Origin** | Learned from user/codebase | Imported from external sources |
| **Persistence** | Dynamic, evolves with user | Static, updated when source changes |
| **Scope** | Cross-project, personal | Tool/language/protocol reference |
| **Update cadence** | Every session | When external source version bumps |

### Graph View Integration
All Knowledge notes use `type/knowledge` tag (Gold #FFD54F). For graph connectivity:
- `Knowledge/_index.md` links to `System/` and `Memory/` — and vice versa
- Memory notes about tools link to `Knowledge/<Domain>/` when relevant
- Project docs link to `Knowledge/` when depending on external tools
- Every `_index.md` within a domain links back to `Knowledge/_index`
- Every sub-document links back to its domain `_index.md`
- **No orphan notes** — every knowledge node is reachable from the hub

### Domain Registration — Knowledge/_index.md
`Knowledge/_index.md` lists every domain with:
- **What's in here**: Description and scope of the documentation
- **When to pull this knowledge**: Specific contexts that trigger a lookup
- **Entry point**: WikiLink to the domain's `_index.md`

### Domain _index Template
Every `Knowledge/<Domain>/_index.md` MUST contain:
```
# <Domain Name>

## Structure

```
Knowledge/<Domain>/
  _index.md          ← This file — hub
  <topic>.md         ← Individual doc
  ...
```

## Documents
- **<topic>** — Brief one-line description of what this doc covers

## Related
- [[Knowledge/_index|Knowledge Base]]
- [[Memory/<related>|Related Memory]]
- [[Projects/<related>|Related Project docs]]
```

### Knowledge Note Convention
Every knowledge note uses this frontmatter:
```yaml
---
tags:
  - type/knowledge
  - domain/<domain-name>
---
```

For material sourced from an external URL, add:
```yaml
source: <url>
source-version: <version or date>
```

### Knowledge Types & Compilation

Different sources need different compilation strategies. Before ingesting any material, classify it into one of the 7 types below. This determines the structure, depth, and compilation rules.

| Type | Code | When to use | Example sources |
|------|------|-------------|-----------------|
| **Specification** | SPEC | Authoritative, definitional — defines WHAT something is | RFCs, language grammars, protocol definitions, JSON schemas |
| **Tutorial/Guide** | GUIDE | Instructional, sequential — teaches HOW to do something | Getting started guides, workshops, cookbooks, walkthroughs |
| **Reference** | REF | Catalog of items for lookup — commands, flags, APIs | Man pages, CLI --help, library APIs |
| **Conceptual** | CONCEPT | Narrative, explanatory — how things fit together | Architecture docs, design docs, white papers |
| **Cheat Sheet** | CHEAT | Ultra-compact, scannable — glance and find | Keyboard shortcuts, command palettes |
| **Config/Snapshot** | CONFIG | Exact environment reproduction — versions, commands | Setup guides, dotfiles, CI config, env setup |
| **Narrative** | NARRATIVE | Sequential reading — books, novels, long-form text | Books, stories, chapter-based reference texts |
| **Mixed** | HYBRID | Source spans multiple types | Framework doc with spec + tutorial + reference |

**Quick decision tree**: Ask "What is this document fundamentally?" → if it defines → SPEC. If it teaches → GUIDE. If it catalogs → REF. If it explains → CONCEPT. If it's scannable → CHEAT. If it sets up → CONFIG. If it's for reading → NARRATIVE. If mixed → HYBRID.

The detailed compilation instructions (Phase 0 analysis, 7 system-specific structure templates, compilation rules, quality gates, cross-linking strategy) are documented in **[[Knowledge/Knowledge Compilation/_index|Knowledge Compilation Blueprint]]** — load that document when you need to compile new material.

#### Structure Rules — Anti-Spaghetti Enforcement
- **Tree, not mesh**: Every document has exactly one parent (its domain `_index.md`). Cross-links between siblings are encouraged, but the parent-child hierarchy is unambiguous.
- **No orphans**: Every note is reachable from `Knowledge/_index.md` by following `_index.md` links.
- **Every level has an _index**: Any directory under `Knowledge/` MUST have an `_index.md` that lists its children.
- **_descriptions in lists**: Every doc listed in an `_index.md` MUST include a one-line description of what it covers.
- **Consistent frontmatter**: Always include `type/knowledge` and `domain/<name>`.
- **Source attribution**: If the material comes from an external source, include `source:` in frontmatter.
- **Domain summary**: Every domain MUST include a `<domain>-summary.md` file — a compact, context-window-friendly snapshot updated on every visit (see [[Knowledge/Knowledge Compilation/_index#7-Domain-Improvement-Protocol|Blueprint §7]]).

---

## 13. Key Reminders

1. **Read first, write later**: Always check vault before searching codebase
2. **Fill gaps immediately**: If you searched the codebase for something, document it
3. **Cross-link everything**: No note is an island — link `_index → docs/` for graph view
4. **Update progress**: Keep Workspace.md and rollout items current
5. **Memory is dynamic**: Add every preference, tool, and pattern you learn about me
6. **Changelog for versions only**: Per-session context goes in `Memory/`, not Changelog/
7. **Use Memory for cross-cutting**: Project details stay in Projects/
8. **Respect the `/Memory` boundary**: Don't pollute it with project trivia
