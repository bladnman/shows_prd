# Documentation Editing System

An Open Agent System for flow-editing documentation.

## Quick Start

Place documents in `open-agents/source/` and use the `/docs:edit` command to process them.

## Structure

```
open-agents/
├── agents/          # Agent definitions
├── source/          # Input documents to edit
└── output-edited/   # Processed documents
```

## Available Commands

- `/docs:edit <filename or instructions>` - Edit a document with the flow editor
