# Claude Space Canonical Structure

Every Claude Space MUST contain this layout:

```
my-space/
├── CLAUDE.md                    # Lightweight: role, stubs, commands
├── context/
│   ├── project.md               # Created by /onboard
│   ├── role.md                  # Created by /onboard
│   ├── constraints.md           # Created by /onboard
│   └── for-agent/
│       ├── environment.md       # Created by /onboard
│       ├── workflows.md         # Template-specific
│       └── ...                  # Additional detailed instructions
├── work-log/
│   └── YYYY-MM-DD.md            # Daily operation logs (agent-written)
├── planning/
│   ├── plan.md                  # Current active plan
│   └── pivots/
│       └── YYYY-MM-DD-reason.md # Plan change records
├── user-docs/
│   └── *.md                     # Deliverables for the user
├── .claude/
│   └── commands/
│       ├── onboard.md           # REQUIRED — personalization command
│       └── *.md                 # Domain-specific commands
└── .mcp.json                    # Optional MCP tool integrations
```

## Key Principles

1. **CLAUDE.md is lightweight** — loaded every prompt, so only essentials and stubs
2. **context/for-agent/** holds detailed instructions — read on demand
3. **Repository is memory** — no reliance on built-in memory features
4. **Templates are blank on context** — structure and mechanics only, personalized via /onboard

## Directory Ownership

| Directory | Owner | Purpose |
|-----------|-------|---------|
| context/ | user | Project context and reference material |
| context/for-agent/ | template/agent | Detailed agent instructions |
| work-log/ | agent | Daily operational tracking |
| planning/ | agent | Plans and pivot history |
| user-docs/ | agent | Polished deliverables |
| .claude/commands/ | template | Slash commands for workflows |
