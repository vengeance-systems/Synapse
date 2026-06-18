---
tags:
  - type/knowledge
  - type/index
  - domain/_meta
---
# Knowledge Base

> **Purpose**: Comprehensive reference documentation for tools, languages, protocols, and systems. Unlike `Memory/` (personal, concise), this holds full-depth external material with a linked, nested tree structure.

## Graph View Connectivity

- `System/OpenCode Workspace & Memory Protocol.md` ← links to this note
- [[Memory/_README|Memory/_README]] ← Memory notes link here when referencing tools
- `Projects/*/` ← Project docs link here when depending on external tools

Every knowledge node is `type/knowledge` (Gold #FFD54F in graph). No orphan notes — every note is reachable from this hub.

## Domain Registration

Each knowledge domain follows this template. Register new domains below.

> **Domain**: `<Name>`
> - **What's in here**: What documentation this domain contains, scope, version covered
> - **When to pull this knowledge**: Specific contexts where AI sessions should look here (e.g., "when configuring the tool", "when debugging protocol issues", "when writing scripts using this library")
> - **Entry point**: `[[Knowledge/<Domain>/_index|<Domain> Documentation]]`

---

<!--
  === TEMPLATE FOR NEW DOMAINS ===
  Copy and fill out:

  ### <Domain Name>
  - **What's in here**: ...
  - **When to pull this knowledge**: ...
  - **Entry point**: [[Knowledge/<Domain>/_index|<Domain> Documentation]]

-->

## Registered Domains

(No domains yet — add them as external reference material is compiled.)

---

## Convention

Every knowledge note uses:
```yaml
---
tags:
  - type/knowledge
  - domain/<name>
---
```

For sourced material, add:
```yaml
source: <url>
source-version: <version or date>
```

## Related

- [[System/OpenCode Workspace & Memory Protocol|Protocol — Knowledge Base section]]
- [[Memory/_README|Memory — cross-session knowledge]]
