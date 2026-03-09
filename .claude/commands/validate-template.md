# Validate Template

Check a Claude Space template against the workspace model schema and report compliance.

## Steps

1. **Identify the template.** Accept a local path, GitHub URL, or repo name.

2. **Run structural checks.** Verify against `reference/schema.json`:
   - [ ] `CLAUDE.md` exists at root
   - [ ] `context/` directory exists
   - [ ] `context/for-agent/` directory exists
   - [ ] `work-log/` directory exists
   - [ ] `planning/` directory exists
   - [ ] `user-docs/` directory exists
   - [ ] `.claude/commands/onboard.md` exists

3. **Run quality checks:**
   - [ ] CLAUDE.md is lightweight (<60 lines, no detailed instructions)
   - [ ] CLAUDE.md has context stub references pointing to `context/for-agent/`
   - [ ] CLAUDE.md lists available slash commands
   - [ ] CLAUDE.md includes memory policy note
   - [ ] `/onboard` command follows the standard pattern (gathers project, role, constraints, environment)
   - [ ] `/onboard` creates required context files (project.md, role.md, constraints.md, environment.md)
   - [ ] Command list in CLAUDE.md matches actual files in `.claude/commands/`
   - [ ] No detailed instructions live in CLAUDE.md (they belong in context/for-agent/)

4. **Report results.** Present a compliance summary:
   ```
   Template: {name}
   Schema Version: 1.1

   Structure:  {PASS/FAIL}  ({n}/7 required items present)
   CLAUDE.md:  {PASS/WARN}  (lightweight: yes/no, stubs: yes/no)
   Onboard:    {PASS/FAIL}  (exists: yes/no, standard: yes/no)
   Commands:   {PASS/WARN}  (listed: n, actual: n, match: yes/no)

   Issues:
   - {list of specific issues}

   Recommendations:
   - {list of suggested improvements}
   ```

5. **Offer to fix.** If issues are found, offer to run `/update-template` to resolve them.
