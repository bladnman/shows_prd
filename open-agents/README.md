# Documentation Editing System

An Open Agent System for PRD documentation editing and finalization.

## Quick Start

1. Place documents in `docs/drafts/`
2. Use `/docs:edit` to improve them
3. Use `/docs:finalize` to create final versions

## Agents

- **Document Editor** - Flow-edit and polish drafts
- **Finalizer** - Produce authoritative final versions

## Project Structure

```
docs/
├── drafts/     # Work here
└── final/      # Final output lives here
```

All changes are automatically committed to git.
