# Wrap Up

End-of-session review. Updates CLAUDE.md if project-level guidance changed, then deploys if requested.

## Steps

1. **Review what changed this session** — look at `git diff main` (or `git log` if already merged) to understand what was built, added, or changed.

2. **Check if the marketing reference needs updating.** If any copy, pricing, feature descriptions, or positioning changed on the site, the source of truth must stay in sync:
   - Open `/Users/carloscaballero/Documents/Projects/Cyclar/docs/marketing-reference.md`
   - Update only what changed — keep it accurate to what's live on the site
   - Do not turn it into a changelog; document current state, not history

3. **Update `CLAUDE.md` only if project-level guidance changed** — new conventions, structural decisions, new slash commands, or anything that affects how future work should be approached.

4. **Summarize what was updated** before saving — keep it to a few bullet points. Ask the user to confirm before writing.

5. **If there are uncommitted changes**, ask if they'd like to deploy now via `/deploy`, or leave it for later.

## Notes
- `CLAUDE.md` is gitignored — changes are local only, never committed.
- The marketing reference lives in the Cyclar app repo, not here — but it's the source of truth for all copy on this site. Keep them in sync.
- If nothing meaningful changed that isn't already documented, say so — don't update for the sake of it.
