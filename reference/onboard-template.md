# Onboard

Initialize this Claude Space for its specific application. This command drives the **Personalize** stage — gathering context from the user, saving it to the repository, and configuring the workspace.

## Steps

1. **Identify the template.** Read CLAUDE.md to determine which Claude Space template this repository was created from. Summarize the template's purpose and capabilities back to the user for confirmation.

2. **Gather user context.** Ask the user for the following, one at a time:
   - **Project name**: What is this specific instance of the space for?
   - **User role**: What is your role in this project?
   - **Project description**: Describe the project in 2-3 sentences. What are you trying to accomplish?
   - **Key constraints or preferences**: Any boundaries, deadlines, tools, or preferences the agent should know about?
   - **Environment details**: What OS, key tools, file paths, or infrastructure details should the agent know about?

3. **Save context to the repository.** Write the gathered information into `context/`:
   - `context/project.md` — Project name, description, and goals
   - `context/role.md` — User's role and how it shapes the work
   - `context/constraints.md` — Any constraints, preferences, or boundaries
   - `context/for-agent/environment.md` — OS, tools, paths, infrastructure details

4. **Configure CLAUDE.md.** Ensure CLAUDE.md follows the lightweight pattern:
   - Keep it to high-level essentials only (role, template identity, commands)
   - Add stub references pointing to the context files just created
   - Add a `## Current Project` section with the project name and one-line summary
   - Add a memory policy note: "Use this repository as your primary memory. Do not rely on built-in memory features for project context."
   - Do NOT put detailed instructions or environment specifics in CLAUDE.md — those belong in `context/for-agent/`

5. **Initialize the planning directory.** Create `planning/plan.md` with a skeleton plan based on the project description. Include sections for Objectives, Current Phase, and Next Steps. Ask the user to review and refine it.

6. **Initialize the work log.** Create the first entry in `work-log/` using today's date (`YYYY-MM-DD.md`) documenting:
   - Workspace onboarded
   - Template identified
   - Initial context captured
   - Plan drafted

7. **Confirm readiness.** Summarize what was set up and list the available slash commands. Tell the user the workspace is ready — the **Success** stage is reached.

## Context Architecture

- `CLAUDE.md` = stubs and essentials (loaded every prompt)
- `context/for-agent/` = detailed instructions (read on demand)
- `context/` (root files) = project context from the user

## Notes

- If any required directories don't exist yet, create them.
- Do not overwrite existing context files — if they exist, ask the user whether to update or keep them.
- This command is idempotent: running it again should allow the user to update their context without losing previous data.
