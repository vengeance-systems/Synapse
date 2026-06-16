b# OpenCode Workspace & Memory Protocol

> **Purpose**: This document defines how AI sessions use the Obsidian vault for persistent memory, context retrieval, and documentation. Every session MUST read this before starting work.

---

## 1. Vault Architecture

```
/ (vault root)
├── System/              ← This file + meta-instructions (read first)
├── Memory/              ← Long-term cross-session knowledge (dynamic)
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
- Instructions for how the AI should work and respond
- Things learned about the user's preferences across sessions
- Known system tools and their locations
- Cross-project patterns and knowledge

### Step 3: Load project workspace and architecture
Read the project's `Workspace.md` and `Architecture.md` for active goals, constraints, and system map.

### Step 4: Search project notes for specific context
Use `search_notes` to find specific details (API endpoints, data structures, security patterns, etc.).

### Step 5: If info is missing, search codebase — THEN ADD IT TO VAULT
Never leave a knowledge gap. Document what you found in the appropriate vault note immediately.

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

**Why**: The graph view is the primary navigation method. Linking `_index → docs` ensures the doc tree stays reachable from the project hub.

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
Color tags are colored inline badges used to visually identify cross-project references, field types, and metadata in documentation.

### Badge Types
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
| `type/memory` | Teal | Memory notes (preferences, tools, patterns) |

When creating a new note, always add the appropriate `type/*` tag in frontmatter. This ensures every node is color-coded and no orphan appears gray in the graph.

---

## 6. Memory Usage — The Dynamic Core

### Purpose
`/Memory` is the most dynamic and personal part of the vault. It captures everything about how the user works, what tools they use, and what the AI should remember across sessions and projects.

### What Goes in Memory

**Work Preferences**
- How the user likes to communicate (tone, verbosity, format)
- Preferred tools and workflows
- Things the user dislikes or wants avoided

**System & Environment Knowledge**
- Installed tools the AI can use (browsers, viewers, editors)
- System specs, OS details, custom configurations
- Known aliases, scripts, and utilities

**Cross-Project Patterns**
- Architectural patterns that repeat across projects
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
- **Add immediately**: When you learn something new about work style, tools, or preferences, write it to `Memory/` before the session ends
- **Even tiny things matter**: A preferred CLI flag, a tool the user reaches for, a response style that works — all go in Memory
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
- **Architecture changes**: Update `Architecture.md` and related data structure notes
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
4. <project>/_index.md — hub page, find what you need
5. <project>/Workspace.md — current goals and constraints
6. search_notes() — targeted content search
```

### When Information is Missing
If the vault doesn't have the answer:
1. Search the codebase directly (grep, glob, read)
2. Document what you found in the appropriate vault note
3. Update `_index.md` if creating a new section
4. NEVER leave a knowledge gap unfilled — the next session will suffer

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
- Human docs: Maintain EN and any other language versions as per project conventions

---

## 10. Key Reminders

1. **Read first, write later**: Always check vault before searching codebase
2. **Fill gaps immediately**: If you searched the codebase for something, document it
3. **Cross-link everything**: No note is an island — link `_index → docs/` for graph view
4. **Update progress**: Keep Workspace.md and rollout items current
5. **Memory is dynamic**: Add every preference, tool, and pattern you learn
6. **Changelog for versions only**: Per-session context goes in `Memory/`, not Changelog/
7. **Use Memory for cross-cutting**: Project details stay in Projects/
8. **Respect the `/Memory` boundary**: Don't pollute it with project trivia
