# Deploy

Stage, commit, and push the current work. Behavior depends on the current branch:

## Steps

1. Run `git status` and `git diff` to see what has changed.

2. Run `git branch --show-current` to check the current branch.

3. **If on `main`:**
   - Stage all modified tracked files (do not use `git add -A` blindly — check for sensitive files first)
   - Commit with a clear, descriptive message summarizing the changes (look at the diff to write it)
   - Push to origin main
   - Confirm success and remind the user that Vercel will auto-deploy

4. **If on a feature branch:**
   - Ask the user: "Do you want to (1) push this branch as a preview, or (2) merge it into main and deploy to production?"
   - **Option 1 — Push branch for preview:**
     - Stage and commit any uncommitted changes
     - Push the branch to origin
     - Remind the user that Vercel will generate a preview URL for this branch
   - **Option 2 — Merge to main and deploy:**
     - Stage and commit any uncommitted changes on the branch first
     - Switch to main: `git checkout main`
     - Merge the branch: `git merge <branch-name>`
     - Push main: `git push`
     - Confirm success and remind the user that Vercel will auto-deploy to production
     - Ask if they want to delete the branch now that it's merged: `git branch -d <branch-name>` and `git push origin --delete <branch-name>`

## Commit message guidelines
- Look at the actual diff — don't guess
- One short summary line (under 72 chars)
- If there are many changes, add a bullet list of the key ones below the summary
- Always append: `Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>`
- Pass the message via heredoc to avoid shell escaping issues

## Notes
- Never force push to main
- Never commit .env files or secrets
- If there are no changes to commit, say so and skip the commit step
- After merging to main, suggest running `/wrap-up` to update CLAUDE.md before ending the session
