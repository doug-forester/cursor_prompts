# ben_cursor_prompts

# BEN Platform — Cursor Prompt Pack

> **Purpose**: This prompt pack provides structured prompts for maintaining architectural consistency and governance in the BEN Platform codebase.

---

## 🏛️ PROMPT 1: Master Architect Mode

**When to use**: At the start of any major architectural discussion or feature design.

**Prompt**:

```
You are now operating in BEN Platform Architect Mode.

Review all requests, code, and documentation through the lens of the BEN Platform governance rules, including:

- BEN Hybrid Architecture (Nuxt Layers + Extension Registry)
- Folder Structure Enforcement
- Multi-Tenant Isolation
- API Namespaces
- Plugin Framework & Manifest Schema
- Documentation Structure
- ADR Governance
- Nuxt + NuxtUI Pro Coding Standards
- Required Mermaid Diagrams for Flows

Before writing any code or generating documentation:

1. Perform a full architectural consistency analysis
2. Identify architectural impacts
3. Identify required documentation updates
4. Identify required ADRs
5. Plan extension-based implementation first
6. Then implement, ensuring rule compliance at every step

If the request violates BEN rules, propose a compliant alternative.
Your output must always reflect BEN governance, structure, and best practices.
```

---

## 🧠 PROMPT 2: Architectural Consistency Check

**When to use**: Before writing any code.

**Prompt**:

```
Perform a comprehensive BEN architecture audit of the requested change.

Evaluate:
- Correct Nuxt layer usage
- Correct extension scoping
- Routing compliance
- Data model alignment
- Tenant isolation in all queries
- Plugin manifest implications
- Required extension lifecycle hooks
- Impact on ADRs
- Impact on existing docs & diagrams

Return:
1. A "PASS / FAIL" compliance score
2. A detailed reasoning summary
3. Required corrections
4. Required ADRs
5. Required documentation updates
6. Risks + future architectural impacts
```

---

## 🧩 PROMPT 3: Extension-First Feature Design

**When to use**: When designing a new feature. Every feature should be built as an extension unless declared core.

**Prompt**:

```
Design this feature as a BEN Extension following:

- manifest.json schema
- extension routing conventions
- extension API namespacing
- extension layout structure
- extension lifecycle (install, load, update)

Output:
1. Complete folder structure
2. Full manifest.json
3. Routes
4. API handlers
5. Components & layouts
6. Pinia store (if needed)
7. Documentation updates
8. Mermaid architecture diagram
```

---

## 🔐 PROMPT 4: Tenant Isolation Enforcement

**When to use**: Before writing any server logic or DB queries.

**Prompt**:

```
Review all database queries and server logic:

1. Add tenant_id filtering to every query
2. Identify global-only tables (allowed exceptions)
3. Block cross-tenant reads/writes
4. Enforce access through tenant context resolver
5. Use BEN database helper utilities

For every query:
(1) Extract the entity
(2) Confirm if it is tenant-scoped or global
(3) Either apply tenant_id or justify an exception

If missing or ambiguous, refuse to generate code until corrected.
```

---

## 🔌 PROMPT 5: Plugin Manifest Validator

**When to use**: Before committing or generating any extension manifest.

**Prompt**:

```
Validate manifest.json against: /docs/05_Plugin-System/plugin-json-schema.json

Perform:
- Schema validation
- Route prefix enforcement
- Namespacing validation
- Layout references validation
- API handler references
- Dependency compatibility check
- Required fields check (id, name, version, routes, apiRoutes, layouts)

If invalid:
- Return a corrected manifest
- Explain reasoning
```

---

## 🗂️ PROMPT 6: Documentation Auto-Update

**When to use**: Whenever a change affects the platform.

**Prompt**:

```
For every generated feature or architectural change:

1. Update appropriate /docs section
2. Add or update Mermaid diagrams
3. Ensure crosslinking
4. Update glossary terms
5. Update API reference
6. Update plugin documentation (if relevant)
7. Suggest ADR creation when needed

Return:
- List of modified docs
- New diagrams
- Structured documentation output
```

---

## 🔄 PROMPT 7: ADR Auto-Generator

**When to use**: When a decision impacts architecture.

**Prompt**:

```
Create a new ADR following /docs/09_ADRs format.

Include:
1. Status (Proposed, Accepted, Deprecated, Superseded)
2. Context (the issue motivating this decision)
3. Decision (the change we're proposing or have agreed to)
4. Consequences (what becomes easier or more difficult)
5. References (links to related ADRs, issues, or documentation)

Ensure the ADR follows the BEN Platform ADR template and is properly numbered.
```

---

## 🔍 PROMPT 8: Context Optimization Check

**When to use:** When starting a new chat or when context seems lacking.

**Prompt:**

Check my current context and optimize it:
  1. List all currently loaded files in context
  2. Identify unnecessary files that should be excluded
  3. Identify missing critical files that should be included
  4. Recommend which .setup/ docs to reference
  5. Suggest optimal context for my current task
Then reconfigure context accordingly.

---

## ⚡ PROMPT 9: Smart File Creation

**When to use:** Before creating any new file.

**Prompt:**

I need to create a new file. First, analyze:

  1. What is the correct BEN directory for this file?
  2. Is this core platform or extension code?
  3. What naming conventions apply?
  4. What template should I use from .setup/07_CODE_TEMPLATES.md?
  5. What related files need to be updated?
  6. What documentation needs updating?

Then create the file in the correct location with proper structure.


---

## 🧪 PROMPT 10: Pre-Commit Validation

**When to use:** Before committing code.

**Prompt:**

Perform a pre-commit validation:
  1. Verify all files are in correct directories
  2. Check tenant isolation in all queries
  3. Verify API routes use correct namespaces
  4. Confirm TypeScript strict mode compliance
  5. Check for missing documentation updates
  6. Verify tests exist for new code
  7. Check for ADR requirements

Return a PASS/FAIL report with specific issues to fix.


---

## 📊 PROMPT 11: Architecture Impact Analysis

**When to use:** Before making significant changes.

**Prompt:**

Analyze the architectural impact of this change:
  1. Which layers are affected? (Core platform, extensions, APIs, database)
  2. Does this change affect tenant isolation?
  3. Does this change affect extension lifecycle?
  4. What are the ripple effects?
  5. What documentation must be updated?
  6. Does this require an ADR?
  7. What are the risks?
  8. What are alternative approaches?

Provide a detailed impact analysis before proceeding.


---

## 🎯 PROMPT 12: Extension Scaffolding

**When to use:** Creating a new extension.

**Prompt:**

Scaffold a complete BEN extension:

Extension name: [NAME] Route prefix: [PREFIX] Description: [DESCRIPTION]

Generate:
  1. Complete folder structure
  2. manifest.json with all required fields
  3. Placeholder pages, layouts, components
  4. API route structure
  5. Pinia store template (if needed)
  6. Extension documentation
  7. Installation instructions
  8. Mermaid architecture diagram

Follow .setup/12_EXTENSION_DEVELOPMENT_GUIDE.md exactly.

---

## 📋 Usage Guidelines

1. **Start with PROMPT 1** (Master Architect Mode) for major features or architectural changes
2. **Use PROMPT 2** (Consistency Check) before implementing any code changes
3. **Use PROMPT 3** (Extension-First Design) when designing new features
4. **Use PROMPT 4** (Tenant Isolation) before writing database queries or server logic
5. **Use PROMPT 5** (Manifest Validator) before committing extension manifests
6. **Use PROMPT 6** (Documentation Update) after any platform-affecting change
7. **Use PROMPT 7** (ADR Generator) when making architectural decisions

---

## 🔗 Related Documentation

- `/docs/05_Plugin-System/plugin-json-schema.json` - Plugin manifest schema
- `/docs/09_ADRs` - Architecture Decision Records format
- Platform architecture documentation
- Extension development guidelines