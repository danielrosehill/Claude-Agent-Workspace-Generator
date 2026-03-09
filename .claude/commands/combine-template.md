# Combine Template

Merge capabilities from two or more Claude Space templates into a single unified template. This is useful when a user needs a workspace that spans multiple domains (e.g., research + content publishing, or project management + client work).

## Steps

1. **Identify source templates.** Ask the user which templates to combine:
   - Local paths, GitHub URLs, or repo names
   - Clone any remote repos first

2. **Analyze each template.** For each source, extract:
   - The role definition from CLAUDE.md
   - All slash commands from `.claude/commands/`
   - All agent instruction files from `context/for-agent/`
   - MCP server configurations from `.mcp.json`
   - Any template-shipped context files

3. **Design the combined template.** Present a merge plan:
   - **Unified role**: A role definition that encompasses both domains
   - **Combined commands**: All commands from both templates. Flag any naming conflicts and ask the user to resolve them.
   - **Merged agent instructions**: Combine context/for-agent/ files. If both templates have `workflows.md`, merge them or create domain-prefixed files (e.g., `research-workflows.md`, `publishing-workflows.md`).
   - **MCP servers**: Union of all .mcp.json entries
   - **Combined onboard**: Merge the onboard questions from both templates, grouping by domain

4. **Get user approval.** Present the merge plan and let the user adjust before proceeding.

5. **Create the combined template.** Options:
   - **New repo**: Create a fresh repo with `gh repo create` (ask public/private)
   - **Extend existing**: Add capabilities from one template into another

6. **Scaffold and populate.** Create the full directory structure and write all files:
   - Combined CLAUDE.md (still lightweight — stubs only)
   - Merged .claude/commands/ directory
   - Merged context/for-agent/ directory
   - Combined .mcp.json
   - README.md describing the combined template

7. **Validate.** Check against `reference/schema.json`.

8. **Commit and push.**

9. **Report.** Show the user the final template structure and available commands.

## Conflict Resolution

When templates have overlapping concerns:
- **Command name conflicts**: Prefix with domain (e.g., `/research-report` vs `/publish-report`)
- **Workflow conflicts**: Create separate workflow files per domain in context/for-agent/
- **Role conflicts**: Synthesize a unified role that covers both domains
- **MCP conflicts**: Merge server lists; if same server appears in both, keep one copy
