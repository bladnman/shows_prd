# Documentation Editing System Instructions

## Purpose

This system provides flow-editing capabilities for documentation. It transforms rough drafts, notes, or existing docs into polished, well-structured documents.

## How This System Works

1. Entry points (CLAUDE.md) direct AI assistants to read this file
2. This file routes requests to the appropriate agent
3. Agents process inputs and produce outputs in designated folders

## Available Agents

| Agent | Purpose | Trigger | Output Location |
|-------|---------|---------|-----------------|
| [Document Editor](agents/document-editor.md) | Flow-edit and improve documentation | "edit", "improve", "polish", "flow-edit" | `output-edited/` |

## Routing Logic

| User Says | Route To |
|-----------|----------|
| "edit this doc" | Document Editor |
| "improve the writing" | Document Editor |
| "polish this" | Document Editor |
| "flow-edit" | Document Editor |
| "clean up this document" | Document Editor |

## Workflow

1. Place source documents in `open-agents/source/`
2. Invoke the appropriate command or ask to edit a specific file
3. Find processed output in `open-agents/output-edited/`

## Adding New Agents

1. Create a new file in `agents/` following the template structure
2. Add the agent to the Available Agents table above
3. Update the Routing Logic table
4. Create a corresponding command in `.claude/commands/docs/`

## Conventions

- Preserve the original file in `source/` (never overwrite)
- Output files use the same name as input, placed in `output-edited/`
- Include a brief changelog comment at the top of edited docs if significant changes were made
