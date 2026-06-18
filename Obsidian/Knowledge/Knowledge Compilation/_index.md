---
tags:
  - type/knowledge
  - type/index
  - domain/knowledge-compilation
  - audience/ai
---
# Knowledge Compilation Blueprint

> **Purpose**: Full-depth reference for compiling external knowledge into the vault. This document defines how to analyze, classify, structure, and cross-link any external source. Load this document when you need to ingest new reference material.

**Status**: Active
**Version**: 1.0
**Domain type**: Meta-domain (governs how all Knowledge/ domains are created)

---

## Table of Contents

1. [The Common Pipeline](#1-the-common-pipeline)
2. [Phase 0: Understanding the Source](#2-phase-0-understanding-the-source)
3. [Knowledge Type Classification](#3-knowledge-type-classification)
4. [The 7 Compilation Systems](#4-the-7-compilation-systems)
5. [Phase 1-4: Compilation Pipeline Details](#5-phase-1-4-compilation-pipeline-details)
6. [Cross-Linking Strategy](#6-cross-linking-strategy)
7. [Domain Improvement Protocol](#7-domain-improvement-protocol)
8. [Special Topics](#8-special-topics)
9. [Quality Gates](#9-quality-gates)

---

## 1. The Common Pipeline

All knowledge compilation follows these phases in sequence — **never skip a phase**:

```
Phase 0 ── Understand the Source
  │
  ▼
Phase 1 ── Structure Design
  │
  ▼
Phase 2 ── Content Compilation
  │
  ▼
Phase 3 ── Graph Wiring
  │
  ▼
Phase 4 ── Quality Review
```

---

## 2. Phase 0: Understanding the Source

Before choosing any structure, deeply understand what you are working with.

### 0.1 — Source Genre

| Genre | Examples | Author's intent |
|-------|----------|-----------------|
| **Specification** | RFC, language spec, protocol definition, API reference | Define precisely what something is |
| **Tutorial** | Getting started guide, workshop, walkthrough | Teach how to accomplish a goal |
| **Reference** | Man page, CLI --help, framework API docs | Be looked up, not read linearly |
| **Conceptual guide** | Architecture overview, design doc, white paper | Explain ideas and how things fit |
| **Cheat sheet** | Keyboard shortcuts, command quick reference | Be scanned rapidly during use |
| **Configuration guide** | Setup instructions, env setup, CI config | Reproduce a specific environment state |
| **Narrative work** | Book, novel, story, long-form essay | Be read sequentially, preserved as-is |

### 0.2 — Reader Intent

| Intent | Needs | Priority |
|--------|-------|----------|
| Implement something | Exact specs, edge cases, error codes | Fidelity, completeness |
| Learn a skill | Steps, prerequisites, verification | Clarity, sequencing |
| Look up a fact | Compact reference, index, search | Scanability, organization |
| Understand a system | Concepts, relationships, mental models | Narrative, cross-links |
| Debug a problem | Error states, common pitfalls, troubleshooting | Traceability, examples |
| Set up an environment | Exact commands, versions, platform specifics | Reproducibility, exactness |
| Read a narrative | Sequential chapters, preserved structure | Faithfulness to original |

### 0.3 — Structural Patterns

Ask:
- **Does it have explicit sections?** (headings, chapters, numbered sections)
- **Is it linear or referential?** (reads front-to-back vs. jump-to-section)
- **What are the atomic units?** (command, function signature, concept, step, term)
- **Are there internal cross-references?** (links, "as described in section X")
- **What's the nesting depth?** (shallow = one note, deep = directory tree)
- **Is there a canonical ordering?** (tutorials are sequential; references are alphabetical)

### 0.4 — Knowledge Density

| Density | Characteristics | Approach |
|---------|----------------|----------|
| **High** | Every sentence defines something; tables, code blocks, formal syntax | Preserve fidelity; minimal rewriting |
| **Medium** | Mix of explanation and reference; prose with examples | Summarize concepts; extract reference material |
| **Low** | Narrative, opinion, anecdote, padding | Condense to essence; extract actionable parts |

### 0.5 — Connection Points

Map the source to the vault:
- **What domains does this touch?** (Hyprland, Rofi, Python, etc.)
- **What projects depend on this?** (Synapse, etc.)
- **What Memory notes reference this tool/concept?**
- **What prerequisites does it assume?**
- **What tools/languages/standards does it reference?**

### 0.6 — Scope Evaluation

| Size | Likely structure | Effort |
|------|-----------------|--------|
| < 1 page, single concept | One note | Low |
| 1-10 pages, several concepts | Domain directory, several notes | Medium |
| 10-100 pages, major domain | Domain with subdirectories | High |
| 100+ pages, complete system | Full domain with deep nesting | Very high |

**Phase 0 quality gates** — do not proceed until:
- [ ] Source genre identified
- [ ] Reader intent identified
- [ ] Structural patterns mapped
- [ ] Density assessed
- [ ] Connection points listed
- [ ] Scope evaluated
- [ ] Compilation system selected (see §3)

---

## 3. Knowledge Type Classification

Every source is classified into one of **7 types**. Each has a dedicated compilation system.

### Type A — Specification (SPEC)

Authoritative, definitional, precise. Defines WHAT something is.
- **Examples**: RFCs, language grammars, protocol definitions, JSON schemas, API contracts
- **Density**: Very high — every clause matters
- **Fidelity**: Maximum — never paraphrase specs
- **System**: **Canonical Transcription** (§4.A)

### Type B — Tutorial / Procedural Guide (GUIDE)

Instructional, sequential, goal-oriented. Teaches HOW to do something.
- **Examples**: Getting started guides, workshops, cookbooks, walkthroughs
- **Density**: Medium — prose with interspersed actions
- **Fidelity**: Medium — actions must be exact; explanations can be summarized
- **System**: **Procedural Extraction** (§4.B)

### Type C — Reference / Lookup (REF)

Catalog of items (commands, functions, flags, APIs). Designed for lookup.
- **Examples**: Man pages, CLI --help output, framework API docs, library references
- **Density**: High — tabular, structured data
- **Fidelity**: High — values must be exact; ordering can be reorganized for scanability
- **System**: **Reference Catalog** (§4.C)

### Type D — Conceptual / Explanatory (CONCEPT)

Narrative, relational, "big picture". Explains how things fit together.
- **Examples**: Architecture docs, design documents, white papers, philosophical essays
- **Density**: Low to medium — prose-heavy
- **Fidelity**: Low — concepts can be restated; analogies can be introduced
- **System**: **Concept Mapping** (§4.D)

### Type E — Cheat Sheet / Compact Reference (CHEAT)

Highly compressed, extremely scannable. Optimized for working memory.
- **Examples**: Keyboard shortcut cards, command palettes, syntax summaries
- **Density**: Extreme — minimal prose, maximum data per line
- **Fidelity**: High — values must be exact; nothing can be dropped
- **System**: **Compression Grid** (§4.E)

### Type F — Environment / Config Snapshot (CONFIG)

Exact, reproducible, platform-specific. Captures a particular state.
- **Examples**: Setup guides, dotfiles, CI configuration, environment setup scripts
- **Density**: Medium to high — exact commands and values
- **Fidelity**: Very high — commands must be copy-pasteable; versions pinned
- **System**: **Environment Snapshot** (§4.F)

### Type G — Narrative / Structured Text (NARRATIVE)

Sequential, chapter-based, author-driven. Preserved as-is with structural splitting.
- **Examples**: Books, novels, stories, long-form essays, reference texts read cover-to-cover
- **Density**: Variable — determined by source
- **Fidelity**: Maximum — preserve the original; split only by chapters/parts
- **System**: **Structural Transcription** (§4.G)

### Hybrid — Mixed Source (HYBRID)

Source that contains multiple types in one document (e.g., a framework doc with spec + tutorial + reference).
- **Approach**: Split by type, apply each system to its portion
- **System**: **Hybrid Split** (§4.H)

### Classification Decision Tree

```
Authoritative, definitional, precise?
  ├─ Defines WHAT something is ──────────────► Type A (SPEC)
  ├─ Catalogs items for lookup ───────────────► Type C (REF)
  └─ No → continue ↓

Instructional, sequential? ────────────────────► Type B (GUIDE)
  └─ No → continue ↓

Extremely compressed, scannable? ──────────────► Type E (CHEAT)
  └─ No → continue ↓

Explanatory, narrative, big-picture? ──────────► Type D (CONCEPT)
  └─ No → continue ↓

Exact environment reproduction? ───────────────► Type F (CONFIG)
  └─ No → continue ↓

Sequential reading, chapter-based narrative? ──► Type G (NARRATIVE)
  └─ No → continue ↓

Mixed multiple types? ─────────────────────────► Type H (HYBRID)
```

---

## 4. The 7 Compilation Systems

### 4.A — Canonical Transcription (Type A: SPEC)

**Philosophy**: Faithfully preserve the source's authoritative structure. The compiler is a curator, not an author.

**Structure**:
```
Knowledge/<Domain>/
  _index.md              ← Hub: scope, version, source
  overview.md            ← Purpose, conformance requirements
  section-01.md          ← Mirror source section numbering
  section-02.md
  ...
  appendix.md            ← Appendices, errata
  glossary.md            ← Defined terms
```

**Rules**:
1. Mirror source section hierarchy exactly. Use same numbering.
2. Every formal definition → code block or formatted table.
3. Preserve normative language (MUST, SHOULD, MAY) — never paraphrase.
4. Add "Summary" at top of each file (2-3 sentences in compiler's words for navigation).
5. External references → `[[WikiLink]]` if target exists in vault, else footnote with URL.
6. Document version, date accessed, source URL in frontmatter.
7. **Do NOT**: Add opinions, interpretations, examples not in source, or simplify.

---

### 4.B — Procedural Extraction (Type B: GUIDE)

**Philosophy**: Extract the essential procedure, strip unnecessary narrative, add structure for reproducibility.

**Structure**:
```
Knowledge/<Domain>/
  _index.md              ← Hub: what this guide covers, skill level
  quickstart.md          ← Minimal path to first success (5-10 steps max)
  <procedure-name>.md    ← Single procedure (one .md per workflow)
  troubleshooting.md     ← Common errors, failure modes, solutions
  reference.md           ← Parameters, options, config values (optional)
```

**Rules**:
1. Each guide file covers exactly one goal (one workflow).
2. Every procedure file starts with:
   - **Prerequisites**: What must be true before starting
   - **Expected outcome**: What success looks like
3. Steps are numbered, each step is one actionable sentence.
4. After each step, include the **expected result** where possible.
5. Commands in code blocks, copy-pasteable.
6. Troubleshooting associates errors with specific steps ("If step 3 fails...").
7. **Do NOT**: Mix multiple workflows in one file, omit prerequisite checks, skip error handling.

---

### 4.C — Reference Catalog (Type C: REF)

**Philosophy**: Organize for maximally fast lookup. The reader knows what they're looking for and wants to find it in seconds.

**Structure**:
```
Knowledge/<Domain>/
  _index.md              ← Hub: categories, index, search tips
  <category>.md          ← One category per file (e.g., "Commands", "Config Options")
                           Each entry: signature, description, params table, example, see-also
  full-index.md          ← Alphabetical master index (if >50 entries)
```

**Rules**:
1. Every entry has a consistent structure. Choose a template and stick to it.
2. Group by meaningful category (not arbitrary first-letter). The `_index.md` explains grouping.
3. Within a category, sort alphabetically or by frequency of use.
4. Each entry includes:
   - **Signature** (syntax, CLI flags, function prototype)
   - **Description** (1-2 sentences max)
   - **Parameters/Options** (table format)
   - **Example** (one practical example)
   - **See also** (links to related entries)
5. If >50 entries, create `full-index.md` with quick links.
6. **Do NOT**: Write long prose, mix categories, omit examples.

---

### 4.D — Concept Mapping (Type D: CONCEPT)

**Philosophy**: Create a navigable concept graph. The reader wants to understand relationships, not memorize facts.

**Structure**:
```
Knowledge/<Domain>/
  _index.md              ← Hub: concept map, key ideas, reading paths
  overview.md            ← High-level narrative (the "elevator pitch")
  <concept>.md           ← One concept per file
    - Definition
    - Why it matters
    - How it relates to other concepts (with links)
    - Examples / analogies
    - Deeper dive (optional)
  glossary.md            ← Key terms with brief definitions and links
```

**Rules**:
1. Start with `overview.md` — 10,000-foot view in your own words.
2. Identify 5-7 key concepts. Each gets its own file.
3. Every concept file follows the same template.
4. `_index.md` includes a concept map (text diagram or relationship list).
5. Cross-link aggressively — every concept file links to every related concept.
6. Glossary defines every term in any concept file.
7. **Do NOT**: Exceed 10-12 concept files (split into subdomains if larger). Avoid flat definition lists — the value is in connections.

---

### 4.E — Compression Grid (Type E: CHEAT)

**Philosophy**: Maximum density in a single scannable artifact.

**Structure**: **Single file preferred.**
```
Knowledge/<Domain>/
  _index.md                          ← Hub: brief description, link to cheat
  <name>-cheat-sheet.md              ← The cheat sheet (single file)
```

**Rules**:
1. **Prefer a single markdown file** — split only if >200 lines.
2. Use tables as primary structure. Each table = a meaningful category.
3. Layout:
   - **Header**: What this covers, version, source
   - **Quick reference**: 5-10 most-used items at top
   - **Category tables**: Each with clear heading
   - **Examples**: 2-3 practical snippets
4. Descriptions: 1-5 words per cell.
5. Monospace for commands, flags, code.
6. **Do NOT**: Write paragraphs, include conceptual explanations, exceed ~200 lines per file without splitting, omit the quick reference.

---

### 4.F — Environment Snapshot (Type F: CONFIG)

**Philosophy**: Reproduce an exact environment state. Every command must work when copy-pasted.

**Structure**:
```
Knowledge/<Domain>/
  _index.md              ← Hub: what environment, version, platform
  prerequisites.md       ← Required tools, versions, platform requirements
  setup.md               ← Step-by-step installation
  configuration.md       ← Config files, environment variables, dotfiles
  validation.md          ← Commands that verify correct setup
  troubleshooting.md     ← Common setup failures
```

**Rules**:
1. Every command block prefixed with the shell: `bash`, `zsh`, `fish`.
2. Pin versions explicitly: `install tool@1.2.3`, not `install tool`.
3. Each step specifies platform: `# Linux (Arch)`, `# macOS`, `# All`.
4. Configuration files as code blocks with exact contents.
5. `validation.md` contains commands whose output confirms correct setup.
6. `troubleshooting.md` links each failure mode to the causing step.
7. **Do NOT**: Use `latest`/unversioned install, omit platform notes, skip validation.

---

### 4.G — Structural Transcription (Type G: NARRATIVE)

**Philosophy**: Preserve the original work faithfully. Split only by the author's own chapter/part boundaries. No reinterpretation.

**Structure**:
```
Knowledge/<Domain>/
  _index.md              ← Hub: title, author, metadata, reading guide
  preface.md             ← Foreword, introduction, author's notes (if any)
  part-01/               ← Part/Chapter grouping (if source uses parts)
    _index.md            ← Part overview
    chapter-01.md        ← One chapter per file
    chapter-02.md
    ...
  part-02/
    ...
  appendix.md            ← Any appendices, endnotes
```

**Rules**:
1. Split only at the source's natural boundaries (chapters, parts, books).
2. Every file starts with the chapter/part title and number as it appears in source.
3. Preserve the original text faithfully — no paraphrasing, no restructuring.
4. Add a brief summary at the top of each chapter file (2-3 sentences) for navigation.
5. Metadata in frontmatter: title, author, original publication date, source URL, ISBN if applicable.
6. If the source has its own internal cross-references, preserve them as footnotes since `[[WikiLinks]]` won't point to an external page number.
7. **Do NOT**: Add commentary, analysis, abridgement, or restructuring. This is pure preservation.
8. For extremely long works (>50 chapters), consider grouping into subdirectories by book/part.

---

### 4.H — Hybrid Split (Type H: HYBRID)

**Philosophy**: Split a complex source by knowledge type and apply the appropriate system to each part.

**Structure**:
```
Knowledge/<Domain>/
  _index.md              ← Hub: explains the split, reading paths
  spec/                  → Apply System A
  guide/                 → Apply System B
  ref/                   → Apply System C
  concept/               → Apply System D
```

**Rules**:
1. Identify which sections of the source correspond to which type.
2. Create subdirectories per type (`spec/`, `guide/`, `ref/`, `concept/`, `cheat/`, `config/`, `narrative/`).
3. Each subdirectory follows its compilation system independently.
4. The `_index.md` explains the split and provides reading paths based on reader intent.
5. Cross-link between subdirectories.
6. **Do NOT**: Force a mixed source into a single system.

---

## 5. Phase 1-4: Compilation Pipeline Details

### Phase 1 — Structure Design

Input: Phase 0 analysis → selected compilation system
Output: Directory tree

1. Create domain directory under `Knowledge/`
2. Create `_index.md` from the domain template with:
   - Frontmatter: `type/knowledge`, `domain/<name>`, `source`, `source-version`
   - Domain description
   - Structure overview (file listing with descriptions)
   - Related domains
3. Create files per the selected compilation system's structure template

### Phase 2 — Content Compilation

Input: Directory structure + source material
Output: Filled knowledge notes

1. Read the source thoroughly
2. For each file:
   a. Extract the relevant portion
   b. Apply compilation rules for the selected system
   c. Add opening summary (1-3 sentences)
   d. Add closing `## Related` section with links
3. Write all files

### Phase 3 — Graph Wiring

Input: Completed notes
Output: Fully cross-linked vault

1. **Register on Knowledge hub**: Add domain to `Knowledge/_index.md`
2. **Link down**: Each note links to its children
3. **Link up**: Each note links to its parent `_index.md`
4. **Link across**: Sibling domains, Memory notes, Projects
5. **Link to Memory**: Update any Memory note that references this tool
6. **Link to Projects**: Add bidirectional links with dependent projects
7. **Verify**: No orphan notes — all reachable from `Knowledge/_index.md`

### Phase 4 — Quality Review

Run the system-specific quality gates (§9). Additionally:

**General gates**:
- [ ] Frontmatter complete
- [ ] Opening summary present in each note
- [ ] Not a direct copy-paste without restructuring (exception: SPEC, NARRATIVE)
- [ ] `## Related` in every note
- [ ] `_index.md` lists all files with descriptions
- [ ] Every note linked from parent `_index.md`
- [ ] Domain registered in `Knowledge/_index.md`
- [ ] No orphan notes

---

## 6. Cross-Linking Strategy

### The 8 Linking Levels

| Level | Links to | Purpose |
|-------|----------|---------|
| **L1 — Parent** | Domain `_index.md` | Location in hierarchy |
| **L2 — Children** | Sub-topics, sub-sections | Navigation depth |
| **L3 — Siblings** | Other notes in same domain | Intra-domain connections |
| **L4 — Cross-domain** | Other `Knowledge/` domains | Cross-topic connections |
| **L5 — Memory** | `Memory/` notes if tool referenced | Personalization |
| **L6 — Project** | `Projects/*/` that depend on this | Practical relevance |
| **L7 — System** | `System/` protocol sections | Governance |
| **L8 — External** | Source URLs, complementary external docs | Original context |

### Placement Rules

1. **Every note** MUST have `## Related` with at least L1.
2. **Domain `_index.md`** MUST have L4, L5, L6, L7.
3. **Individual notes** SHOULD have L3, L4.
4. **Memory notes** about tools MUST link to the `Knowledge/` entry.
5. **Project docs** depending on external tools MUST link to `Knowledge/` entries.

### Bidirectional Linking

For every link A → B, verify B ← A exists:
- If B is a domain `_index.md`, it should list A.
- If B is a concept note, it should mention the relation.
- If B is a Memory note, it should link back.
- If B is a Project doc, it should link to the Knowledge entry.

---

## 7. Domain Improvement Protocol

Every compiled domain includes a dedicated summary file that improves over time.

### Summary File

Every domain MUST include a file at the same level as `_index.md` named `<domain>-summary.md`:

```
Knowledge/<Domain>/
  _index.md              ← Hub (unchanged after creation)
  <domain>-summary.md    ← Self-improving summary (updated on every visit)
  ...
```

**Purpose**: A compact, context-window-friendly snapshot of the domain. Can be loaded into context without stacking.

**Content**:
```markdown
# <Domain> Summary

**Last updated**: YYYY-MM-DD
**Scope**: What this domain covers
**Entry point**: [[Knowledge/<Domain>/_index|<Domain>]]

## Quick Reference
- (5-10 most-used items extracted from the domain: key commands, concepts, config values)
- (Will be one of the first things learned about the domain)

## Key Files
- **<file>** — What it covers (1-line description)
- **<file>** — What it covers

## Common Tasks
- (Any frequent lookups or procedures, extracted from usage patterns)

## Notes
- (Any insights, gotchas, or patterns discovered during use)
```

**Update rules**:
- On every visit to the domain, update the summary with any new insights, frequently accessed items, or patterns observed.
- Keep the summary compact — ideally < 50 lines. Move bulk content to the actual domain files.
- The summary is the "TL;DR" of the domain. It should be loadable into context without stacking the session.

---

## 8. Special Topics

### 8.1 — Sources Spanning Multiple Domains

When a source naturally covers multiple independent domains (e.g., a document about Wayland + Hyprland + Rofi):

**Two workflows** (decided by user):
1. **Independent split**: Parse the source into separate domain directories, each getting only its relevant portion. Create a "bridge" `_index.md` that links to all affected domains.
2. **Meta-domain**: Create a parent domain that contains all three. The `_index.md` explains the meta structure and links to each subdomain.

**Linking rules**:
- Independent split: Each domain `_index.md` links to the others via `## Related` with a note like "This document is part of a broader source: [[Knowledge/<Meta>/_index|Meta Page]]".
- Meta-domain: The meta `_index.md` contains the full source context. Each subdomain `_index.md` links back to the meta page. Cross-links between subdomains are included as L4.

### 8.2 — Evolving Sources (Versioning)

When a source has multiple versions:
1. Check the changelog for each release before updating.
2. When options/features are deprecated:
   - Move deprecated items to a `## DEPRECATED` section at the end of the relevant document.
   - In the main document body, add a brief inline note with a link: `~~--deprecated since v2.0--~~` or similar.
   - In the DEPRECATED section, document each item with: the item name, the last version where it was available, its replacement (if any).
3. When new versions are ingested, create a version-suffixed entry if the changes are substantial. Update the `_index.md` to point to the latest version and note older versions are archived.

### 8.3 — Partial Knowledge

If only part of a large source is compiled:
- Document what was covered and what was not in the `_index.md` header.
- Mark uncovered sections as `<!-- NOT YET COMPILED -->` so future sessions know the gap.
- The summary file (§7) should note any critical missing sections.

### 8.4 — Quick Ingestion (Small Sources)

For small, single-concept sources (scope evaluation = Low effort):
- Create a single note directly under the domain rather than a full directory tree.
- Include the same frontmatter, summary, and cross-links.
- The domain `_index.md` lists it as a single-entry file.
- Upgrade to full structure if the source later proves more complex than initially assessed.

---

## 9. Quality Gates

### System-Specific Gates

**SPEC (System A)**:
- [ ] All sections from source represented
- [ ] Normative language preserved
- [ ] Version/source documented
- [ ] Every formal element present (grammar rules, code blocks, tables, error codes)
- [ ] Cross-links to dependent domains

**GUIDE (System B)**:
- [ ] Each file covers exactly one workflow
- [ ] Prerequisites listed
- [ ] Expected outcome stated
- [ ] Steps numbered and actionable
- [ ] Expected results included where possible
- [ ] Troubleshooting section present
- [ ] Commands copy-pasteable

**REF (System C)**:
- [ ] Consistent entry format throughout
- [ ] Categories meaningful (not arbitrary)
- [ ] Every entry has a description
- [ ] At least one example per entry
- [ ] See-also links for related entries
- [ ] Full index present if >50 entries

**CONCEPT (System D)**:
- [ ] Overview written (coherent narrative)
- [ ] 5-7 key concepts identified
- [ ] Each concept has definition, relations, examples
- [ ] Concept map present
- [ ] Glossary covers all terms
- [ ] Cross-links between concepts bidirectional
- [ ] External links to related domains

**CHEAT (System E)**:
- [ ] Single file (unless >200 lines)
- [ ] Quick reference section at top
- [ ] Tabular format for entries
- [ ] Descriptions 1-5 words maximum
- [ ] At least 2-3 practical examples
- [ ] Source/version documented

**CONFIG (System F)**:
- [ ] Shell prefixes on all command blocks
- [ ] Versions pinned on all dependencies
- [ ] Platform-specific notes where applicable
- [ ] Config files as exact code blocks
- [ ] Validation commands present
- [ ] Troubleshooting linked to specific steps
- [ ] Setup tested (or noted "untested")

**NARRATIVE (System G)**:
- [ ] Split only at natural chapter/part boundaries
- [ ] Original text preserved faithfully
- [ ] Metadata complete (author, date, source)
- [ ] Chapter summaries present for navigation
- [ ] Internal references preserved as footnotes

**HYBRID (System H)**:
- [ ] Source sections correctly classified by type
- [ ] Each subdirectory follows its system's rules
- [ ] `_index.md` explains split and offers reading paths
- [ ] Cross-links between subsystems

### General Gates (All Systems)
- [ ] Frontmatter complete
- [ ] Opening summary present
- [ ] Not raw copy-paste (exceptions: SPEC, NARRATIVE)
- [ ] `## Related` section in every note
- [ ] `_index.md` lists all files with descriptions
- [ ] Every note linked from parent `_index.md`
- [ ] Domain registered in `Knowledge/_index.md`
- [ ] No orphan notes

### Domain Summary Gates
- [ ] `<domain>-summary.md` exists
- [ ] 5-10 most-used items extracted
- [ ] Key files listed with descriptions
- [ ] Compact (< 50 lines preferred)

---

## Related

- [[System/OpenCode Workspace & Memory Protocol#12. Knowledge Base — External Reference Material|Protocol §12 — Knowledge Classification (brief version)]]
- [[Knowledge/_index|Knowledge Base Hub]]
- [[Memory/_README|Memory — cross-session knowledge]]
