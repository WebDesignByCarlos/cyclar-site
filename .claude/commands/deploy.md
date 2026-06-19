# Deploy

Stage, commit, and push the current work. Behavior depends on the current branch.

## Steps

1. Run `git status` and `git diff` to see what has changed.

2. Run `git branch --show-current` to check the current branch.

3. **If on `main`:**
   - Stage all modified tracked files (do not use `git add -A` blindly — check for sensitive files first)
   - Commit with a clear, descriptive message summarizing the changes (look at the diff to write it)
   - Push to origin main
   - Confirm success and remind the user that Vercel will auto-deploy
   - Then go to step 5 (wrap-up prompt)

4. **If on a feature branch:**
   - Use the `AskUserQuestion` tool to ask: "Where do you want to deploy?" with these options in this exact order:
     - Option 1: "Deploy to production" — merge this branch into main and push
     - Option 2: "Push as preview" — push the branch and get a Vercel preview URL
   - **Option 1 — Deploy to production:**
     - Stage and commit any uncommitted changes on the branch first
     - Switch to main: `git checkout main`
     - Merge the branch: `git merge <branch-name>`
     - Push main: `git push`
     - Confirm success and remind the user that Vercel will auto-deploy to production
     - Use the `AskUserQuestion` tool to ask: "Delete the feature branch now that it's merged?" with options:
       - Option 1: "Yes, delete it" — run `git branch -d <branch-name>` and `git push origin --delete <branch-name>`
       - Option 2: "No, keep it"
     - Then go to step 5 (wrap-up prompt)
   - **Option 2 — Push as preview:**
     - Stage and commit any uncommitted changes
     - Push the branch to origin
     - Remind the user that Vercel will generate a preview URL for this branch
     - Then go to step 5 (wrap-up prompt)

5. **Wrap-up prompt** — after any successful deploy, use the `AskUserQuestion` tool to ask: "Want to run /wrap-up to close out the session?" with options:
   - Option 1: "Yes, run /wrap-up now"
   - Option 2: "No, I'm done"
   - If the user selects Option 1, invoke the `wrap-up` skill using the Skill tool.

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
