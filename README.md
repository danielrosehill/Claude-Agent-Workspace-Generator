# Claude Agent Workspace Generator

A Claude Code workspace for creating, editing, and managing Claude Space templates that conform to the [Claude Agent Workspace Model](https://github.com/danielrosehill/Claude-Agent-Workspace-Model) v1.1 specification.

## What This Does

This repository is a **launchpad** — you open it in Claude Code and use slash commands to generate new workspace templates as GitHub repositories. Each template follows a standardized structure with onboarding, context management, work logging, and domain-specific slash commands.

## Commands

| Command | Purpose |
|---------|---------|
| `/new-template` | Create a new workspace template from scratch |
| `/edit-template` | Modify an existing template's files |
| `/update-template` | Bring a template up to spec with the latest model |
| `/combine-template` | Merge capabilities from multiple templates |
| `/validate-template` | Check a template against the schema |
| `/list-templates` | List your existing workspace templates |
| `/publish-template` | Push a local template to GitHub |

## Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI installed
- [GitHub CLI](https://cli.github.com/) (`gh`) authenticated
- Git configured

## Usage

```bash
cd Claude-Agent-Workspace-Generator
claude
```

Then run any slash command, e.g.:
```
/new-template
```

The agent will interview you about the workspace you need and generate a complete template repository.

## Reference

The `reference/` directory contains the workspace model spec:
- `structure.md` — Canonical folder structure
- `schema.json` — Validation schema
- `onboard-template.md` — Standard onboard command template
- `categories.md` — Workspace category reference

## Workspace Model

Templates follow the [Claude Spaces Standard v1.1](https://github.com/danielrosehill/Claude-Agent-Workspace-Model):

```
my-space/
├── CLAUDE.md              # Lightweight role & command stubs
├── context/
│   └── for-agent/         # Detailed agent instructions
├── work-log/              # Daily operation logs
├── planning/              # Active plans & pivots
├── user-docs/             # Agent-generated deliverables
└── .claude/commands/
    └── onboard.md         # Required initialization command
```
