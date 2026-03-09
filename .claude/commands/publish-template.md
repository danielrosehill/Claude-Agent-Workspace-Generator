# Publish Template

Push a local Claude Space template to GitHub as a new repository.

## Steps

1. **Identify the template.** Ask for the local path to the template directory.

2. **Validate first.** Run the validation checks from `/validate-template` before publishing. If issues are found, offer to fix them first.

3. **Gather publishing details:**
   - **Visibility**: Public or private?
   - **Repository name**: Suggest based on CLAUDE.md header, let user override
   - **Description**: Generate from CLAUDE.md purpose, let user override
   - **Topics/tags**: Suggest relevant GitHub topics (e.g., `claude-space`, `ai-workspace`, `claude-code`)

4. **Create the remote repository:**
   ```
   gh repo create {owner}/{repo-name} --{public|private} --description "{description}" --source . --push
   ```

5. **Add topics:**
   ```
   gh repo edit {owner}/{repo-name} --add-topic claude-space --add-topic ai-workspace
   ```

6. **Verify.** Confirm the repo was created and all files were pushed.

7. **Report.** Provide:
   - The repo URL
   - Clone command for users: `git clone {url} && cd {repo} && claude` then run `/onboard`
   - Visibility status

## Notes

- If the directory is already a git repo with a remote, offer to push to the existing remote instead of creating a new one.
- Always validate before publishing to avoid pushing broken templates.
- Suggest adding the `claude-space` topic for discoverability.
