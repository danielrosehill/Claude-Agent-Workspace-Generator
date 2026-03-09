# Update Template

Bring an existing Claude Space template up to compliance with the latest workspace model specification (v1.1).

## Steps

1. **Identify the template.** Ask the user which template to update:
   - A local path to a cloned template repo
   - A GitHub repo URL (clone it first)
   - A repo name to look up via `gh repo list`

2. **Audit the template.** Check it against `reference/schema.json`. Report:
   - **Missing directories**: Any of context/, context/for-agent/, work-log/, planning/, user-docs/, .claude/commands/
   - **Missing files**: CLAUDE.md, .claude/commands/onboard.md
   - **CLAUDE.md weight**: Is it lightweight (stubs + essentials) or bloated with detailed instructions?
   - **Onboard command**: Does it follow the standard pattern? Does it create the required context files?
   - **Context architecture**: Are detailed instructions properly in context/for-agent/ rather than CLAUDE.md?
   - **Memory policy**: Does CLAUDE.md include a note about using the repo as primary memory?

3. **Present findings.** Show the user what's compliant and what needs updating. Let them approve changes before proceeding.

4. **Apply fixes.** For each issue:
   - **Missing directories**: Create them with `.gitkeep` files
   - **Missing onboard.md**: Generate one based on `reference/onboard-template.md`, tailored to the template's purpose
   - **Bloated CLAUDE.md**: Extract detailed instructions to `context/for-agent/`, replace with stubs
   - **Non-standard onboard**: Update to follow the standard interview pattern while preserving domain-specific questions
   - **Missing memory policy**: Add to CLAUDE.md
   - **Missing context stubs**: Add stub references to CLAUDE.md pointing to context/for-agent/ files

5. **Validate.** Re-run the schema check to confirm all issues are resolved.

6. **Commit and optionally push.** Stage changes, commit with message describing what was updated, and ask about pushing.

## Spec Version Tracking

If the template has a version marker, update it to reflect compliance with v1.1. If not, consider adding one to CLAUDE.md:
```
<!-- Conforms to Claude Spaces Standard v1.1 -->
```
