# List Templates

List the user's existing Claude Space workspace templates.

## Steps

1. **Search for templates.** Use `gh repo list` to find repositories that match Claude Space patterns:
   ```
   gh repo list --json name,description,visibility,url,updatedAt --limit 100
   ```
   Filter for repos matching common template naming patterns:
   - `Claude-*-Space`
   - `Claude-*-Manager`
   - `Claude-*-Workspace`

2. **Verify each candidate.** For each matching repo, check if it actually follows the workspace model by looking for key indicators:
   - Has a `CLAUDE.md` at root
   - Has a `.claude/commands/` directory
   - Has a `context/` directory

3. **Present results.** Show a formatted list:
   ```
   Claude Space Templates
   ═══════════════════════

   1. Claude-Research-Space (public)
      Purpose: Competitive research workspace
      Commands: /onboard, /report, /compare
      Updated: 2025-01-15

   2. Claude-Linux-Desktop-Manager (public)
      Purpose: Desktop environment management
      Commands: /onboard, /audit, /cleanup
      Updated: 2025-01-10

   Found: {n} templates ({public} public, {private} private)
   ```

4. **Offer actions.** Ask if the user wants to:
   - Validate any template (`/validate-template`)
   - Edit a template (`/edit-template`)
   - Update a template to latest spec (`/update-template`)
   - Create a new template (`/new-template`)
