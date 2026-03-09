# New Template

Create a new Claude Space workspace template from scratch. This generates a GitHub repository with the full workspace structure, a tailored CLAUDE.md, an `/onboard` command, and domain-specific slash commands.

## Steps

1. **Gather requirements.** Ask the user:
   - **Workspace purpose**: What kind of work is this template for? (e.g., "competitive research", "home renovation planning", "podcast production")
   - **Target user role**: Who will use this template? (e.g., "product manager", "freelance researcher", "homeowner")
   - **Key workflows**: What are the 2-5 main things the agent should help with? These become slash commands.
   - **Tool integrations**: Does the workspace need MCP servers? (e.g., web search, file access, APIs)
   - **Visibility**: Should the GitHub repo be **public** or **private**?
   - **Repository name**: Suggest a name following the pattern `Claude-{Purpose}-Space` (e.g., `Claude-Competitive-Research-Space`). Let the user override.

2. **Design the template.** Based on requirements, plan:
   - The CLAUDE.md content (lightweight: role definition, stubs to context/for-agent/, command list)
   - The `/onboard` command (adapted from `reference/onboard-template.md` with domain-specific questions)
   - Domain-specific slash commands (one `.md` file per workflow in `.claude/commands/`)
   - Any `context/for-agent/` files that should ship with the template (e.g., `workflows.md` with domain methodology)
   - Whether a `.mcp.json` is needed

3. **Create the repository.** Use `gh` CLI:
   ```
   gh repo create {owner}/{repo-name} --{public|private} --clone
   ```

4. **Scaffold the structure.** Create all required directories and files:
   - `CLAUDE.md` — Tailored to the workspace purpose
   - `context/` — Empty, with `.gitkeep` files
   - `context/for-agent/` — With any template-shipped instruction files
   - `work-log/` — Empty with `.gitkeep`
   - `planning/` — Empty with `.gitkeep`
   - `user-docs/` — Empty with `.gitkeep`
   - `.claude/commands/onboard.md` — Adapted onboard command
   - `.claude/commands/*.md` — Domain-specific commands
   - `.mcp.json` — If tool integrations were specified
   - `README.md` — Brief description of the template

5. **Commit and push.** Stage all files, commit with a descriptive message, and push to the remote.

6. **Report.** Tell the user:
   - The repo URL
   - The template structure created
   - The available slash commands
   - How to use it: clone the repo and run `/onboard`

## Design Guidelines

- **CLAUDE.md** must stay under ~50 lines. Role definition, context stubs, and command list only.
- **Slash commands** should be actionable workflows, not just documentation. Each command should produce a concrete output.
- **The /onboard command** must ask domain-relevant questions beyond the standard set (project name, role, description, constraints, environment).
- **context/for-agent/workflows.md** should describe the domain methodology the agent should follow.
- Use `.gitkeep` files in empty directories so Git tracks them.

## Validation

Before committing, verify the template against `reference/schema.json`:
- [ ] CLAUDE.md exists at root
- [ ] context/ directory exists
- [ ] context/for-agent/ directory exists
- [ ] work-log/ directory exists
- [ ] planning/ directory exists
- [ ] user-docs/ directory exists
- [ ] .claude/commands/onboard.md exists
