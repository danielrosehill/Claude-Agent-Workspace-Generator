# Edit Template

Modify an existing Claude Space template's files. Use this to change the CLAUDE.md, add/remove slash commands, update context/for-agent/ instructions, or adjust MCP configuration.

## Steps

1. **Identify the template.** Ask the user which template to edit. Options:
   - A local path to a cloned template repo
   - A GitHub repo URL (clone it first)
   - A repo name to look up via `gh repo list`

2. **Read the current state.** Read the template's key files:
   - `CLAUDE.md`
   - `.claude/commands/` (list all commands)
   - `context/for-agent/` (list all instruction files)
   - `.mcp.json` (if present)

3. **Understand the edit.** Ask the user what they want to change. Common edits:
   - **Add a slash command**: Design and create a new `.claude/commands/*.md`
   - **Remove a slash command**: Delete the file and update CLAUDE.md command list
   - **Modify CLAUDE.md**: Update role, stubs, or command list
   - **Update agent instructions**: Edit files in `context/for-agent/`
   - **Add/change MCP servers**: Create or modify `.mcp.json`
   - **Rename the workspace**: Update CLAUDE.md header and README

4. **Apply the changes.** Make the edits while preserving:
   - The lightweight CLAUDE.md pattern (no detailed instructions in CLAUDE.md)
   - The required directory structure (never remove required dirs)
   - Consistency between CLAUDE.md command list and actual `.claude/commands/` files

5. **Validate.** Check the template still conforms to the schema:
   - All required directories present
   - CLAUDE.md exists and is lightweight
   - `/onboard` command still exists
   - Command list in CLAUDE.md matches actual command files

6. **Commit.** Stage and commit the changes with a descriptive message.

7. **Optionally push.** Ask the user if they want to push the changes to the remote.

## Notes

- If the template is a remote repo, clone it to a temporary location or `~/repos/github/` first.
- Never delete required directories or the onboard command.
- When adding commands, follow the pattern of existing commands in the template.
