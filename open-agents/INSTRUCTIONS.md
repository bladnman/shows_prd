# Documentation Editing System Instructions

## Purpose

This system provides editing capabilities for PRD documentation.

## How This System Works

1. Entry points (CLAUDE.md) direct AI assistants to read this file
2. This file routes requests to the appropriate agent
3. Agents work on documents in `docs/` and commit all changes to git

## Project Structure

```
docs/
├── shows_prd/  # Official PRD documents - the source of truth
└── drafts/     # Optional scratch space for ideation
```

- **shows_prd/** - The official PRD. All authoritative documents live here.
- **drafts/** - Optional workspace for experiments, rough ideas, or work-in-progress that isn't ready to be part of the official PRD yet.

## Critical Rule: Auto-Commit

**Every change MUST be committed to git immediately.**

After any document modification:
1. Stage the changed file(s)
2. Commit with a descriptive message
3. Format: `docs: <action> <filename>` (e.g., `docs: edit showbiz_prd.md`)

This ensures the full history of document evolution is preserved.

## Available Agents

| Agent | Purpose | Works On |
|-------|---------|----------|
| [Document Editor](agents/document-editor.md) | Edit and improve documentation | `docs/shows_prd/` (primary), `docs/drafts/` (optional) |

## Routing Logic

| User Says | Route To |
|-----------|----------|
| "edit this doc" | Document Editor |
| "improve the writing" | Document Editor |
| "polish this" | Document Editor |
| "flow-edit" | Document Editor |

## Workflow

1. Work primarily in `docs/shows_prd/` - this is the official PRD
2. Use `docs/drafts/` for experimentation or early-stage ideas
3. Use `/docs:edit` to improve documents
4. Each edit is committed automatically

## Adding New Agents

1. Create a new file in `open-agents/agents/` following the template structure
2. Add the agent to the Available Agents table above
3. Update the Routing Logic table
4. Create a corresponding command in `.claude/commands/docs/`
5. Commit the new agent definition

## Conventions

- All documents live in `docs/` - never in `open-agents/`
- Every change gets a git commit
