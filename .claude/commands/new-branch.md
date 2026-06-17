# New Branch

Create a new feature branch off of the latest main, so work is isolated from production.

## Steps

1. Make sure we're on main and it's up to date:
   ```
   git checkout main
   git pull
   ```

2. Ask the user for a short description of what we're building (if they haven't already provided one with the command, e.g. `/new-branch hero section`).

3. Convert their description into a valid branch name: lowercase, hyphens instead of spaces, no special characters. Prefix with `feature/`. Example: "hero section" → `feature/hero-section`.

4. Create and switch to the new branch:
   ```
   git checkout -b feature/branch-name
   ```

5. Confirm to the user:
   - What branch we're on
   - That main and production are fully protected until they choose to merge
   - That they can delete this branch at any time to discard all changes and return to the live build
   - That when they're ready to go live, they can type `/deploy` and choose to merge to main
