# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Marketing Reference

**Before writing any copy, updating features, pricing, or positioning, read the marketing reference:**

```
/Users/carloscaballero/Documents/Projects/Cyclar/docs/marketing-reference.md
```

This file is the source of truth for all product positioning, feature descriptions, pricing tiers, taglines, target audience, and differentiators. It lives in the Cyclar app repo and is kept up to date as part of that project's `/wrap-up` workflow.

**To read it in a session:**
Use the Read tool with the absolute path above. Do not guess at copy, pricing, or feature names — always verify against this file first.

---

## Project Overview

**Cyclar Site** is the marketing and landing page for [cyclar.co](https://cyclar.co) — the public face of the Cyclar personal finance web app. The goal is to communicate what Cyclar is, why it matters, and convert visitors into signups.

The app itself lives at `cyclar.app`. This repo is the marketing site only.

## Tech Stack

- **HTML + CSS + JavaScript** — no framework; keep it simple and fast
- **Vercel** — production hosting, auto-deploys on push to `main`

## Common Commands

```bash
# No build step — open index.html directly in the browser or use a local server
npx serve .       # Serve the site locally
```

## Deployment

Hosted on Vercel, connected to GitHub. Every push to `main` auto-deploys.

```bash
git add <files>
git commit -m "description"
git push
```

## Design Requirements

- Mobile-first — the majority of visitors will be on phones
- Fast and lightweight — no unnecessary JS, no heavy frameworks
- Clear hierarchy: headline → value prop → features → pricing → CTA
- Match the visual identity of the app (neutral palette, green accent only)

## Copy Standards

- All copy must be consistent with the marketing reference (`marketing-reference.md` in the Cyclar app repo)
- Use the approved taglines and positioning — do not invent new ones without updating the reference file
- Pricing must match exactly what's in the reference; never hardcode pricing without checking there first
- Feature descriptions must reflect actual app behavior — verify against the reference before writing

## Working Style

- **Always start with `/new-branch`** — feature branch before any code changes
- **Explain what you're doing and why** before implementing
- **Ask before large structural changes**
- **Prefer simple and readable** over clever or abstract
- **Flag anything that needs manual testing**
- **Keep output concise**

## Workflow Orchestration

1. **Plan first** — enter plan mode for any non-trivial task (3+ steps or structural decisions)
2. **Use subagents** — offload research, exploration, and parallel work to keep main context clean
3. **Verify before done** — never mark complete without proving it works
4. **Demand elegance** — for non-trivial changes, ask "is there a more elegant way?"

## Task Management

1. Write plan to `tasks/todo.md` with checkable items
2. Check in before starting implementation
3. Mark items complete as you go
4. Update `tasks/lessons.md` after any correction from the user

## Custom Slash Commands

Project-level commands in `.claude/commands/`:
- `deploy.md` — stages, commits, and pushes
- `new-branch.md` — creates a new feature branch
- `wrap-up.md` — reviews session changes, updates CLAUDE.md, optionally deploys

## Core Principles

- **Simplicity First**: Make every change as simple as possible. Minimal code impact.
- **No Laziness**: Find root causes. No temporary fixes. Senior developer standards.
- **Minimal Impact**: Changes should only touch what's necessary.
