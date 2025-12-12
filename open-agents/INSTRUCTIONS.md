# Documentation Editing System Instructions

## Purpose

This system provides flow-editing and finalization capabilities for PRD documentation.

## How This System Works

1. Entry points (CLAUDE.md) direct AI assistants to read this file
2. This file routes requests to the appropriate agent
3. Agents work on documents in `docs/` and commit all changes to git

## Project Structure

```
docs/
├── drafts/     # Active working documents
└── final/      # Authoritative final versions
```

- **drafts/** - Where all active editing happens. Documents being developed, revised, or reviewed live here.
- **final/** - The authoritative output. When a document is ready for release, it gets finalized here.

## Critical Rule: Auto-Commit

**Every change MUST be committed to git immediately.**

After any document modification:
1. Stage the changed file(s)
2. Commit with a descriptive message
3. Format: `docs: <action> <filename>` (e.g., `docs: edit overview.md`, `docs: finalize prd.md`)

This ensures the full history of document evolution is preserved.

## Available Agents

| Agent | Purpose | Trigger | Works On |
|-------|---------|---------|----------|
| [Document Editor](agents/document-editor.md) | Flow-edit and improve documentation | "edit", "improve", "polish" | `docs/drafts/` |
| [Finalizer](agents/finalizer.md) | Produce final authoritative versions | "finalize", "publish", "release" | `docs/drafts/` → `docs/final/` |

## Routing Logic

| User Says | Route To |
|-----------|----------|
| "edit this doc" | Document Editor |
| "improve the writing" | Document Editor |
| "polish this" | Document Editor |
| "flow-edit" | Document Editor |
| "finalize" | Finalizer |
| "publish to final" | Finalizer |
| "create final version" | Finalizer |
| "release the PRD" | Finalizer |

## Workflow

### Editing Flow
1. Place or create documents in `docs/drafts/`
2. Use `/docs:edit` to improve them iteratively
3. Each edit is committed automatically

### Finalization Flow
1. When drafts are ready, use `/docs:finalize`
2. Finalizer agent produces polished versions in `docs/final/`
3. Final versions are the authoritative source of truth

## Adding New Agents

1. Create a new file in `open-agents/agents/` following the template structure
2. Add the agent to the Available Agents table above
3. Update the Routing Logic table
4. Create a corresponding command in `.claude/commands/docs/`
5. Commit the new agent definition

## Conventions

- All documents live in `docs/` - never in `open-agents/`
- Drafts can be edited freely and repeatedly
- Final versions should only be updated via the Finalizer agent
- Every change gets a git commit
