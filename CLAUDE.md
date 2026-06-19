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

## Design System

The design system is established. Do not reinvent it — use what's there.

- **`style-guide.html`** — visual reference for all design decisions; open in browser to review before building any UI
- **CSS load order** — every HTML page must link these in order:
  ```html
  <link rel="stylesheet" href="./assets/css/tokens.css">
  <link rel="stylesheet" href="./assets/css/base.css">
  <link rel="stylesheet" href="./assets/css/[page].css">
  ```
- **`assets/css/tokens.css`** — CSS custom properties for colors, typography, spacing, radius, shadows, transitions
- **`assets/css/base.css`** — global reset (box-sizing, margin/padding zero, body font, overflow-x hidden)
- **`assets/css/nav.css`** — sticky nav component; `.is-scrolled` class toggled by inline JS on scroll
- **Typography:** Manrope (Google Fonts, weights 400–800) for H1–H4; system font stack for body text. Load via:
  ```html
  <link href="https://fonts.googleapis.com/css2?family=Manrope:wght@400;500;600;700;800&display=swap" rel="stylesheet">
  ```
- **Brand green:** `#059669` (`--clr-brand`); hover state `#047857` (`--clr-brand-dark`). Used only for interactive elements and key accents — not decorative fills.
- **Spacing:** rem throughout — always use `--sp-*` tokens, never hardcode px values
- **Light mode only** — no dark mode on the marketing site
- **Screenshots** at `assets/images/screenshots/` — 26 JPGs covering all major app screens in light and dark mode; use for feature sections and visual reference
- **Brand assets** at `assets/images/`:
  - `logos/logo-light-mode.svg` — full logo (mark + wordmark), portrait-stacked (383×449). Not suitable for horizontal navs — the wordmark renders unreadably small at nav heights.
  - `logos/logomark.svg` — icon only (257×279). Use anywhere space is tight (e.g. favicons, small badges).
  - `logos/wordmark-light-mode.svg` — text only (383×123).
  - `logos/light-mode-horizontal.svg` — combined mark + wordmark, horizontal layout (690×279). This is what the live nav uses.
  - **Nav logo pattern:** single `<img>` of `light-mode-horizontal.svg` at `height: 36px; width: auto;`
  - `icons/favicon.svg` — browser tab icon (already wired in `index.html`)
  - `icons/opengraph.png` — social sharing preview (already wired in `index.html`)
  - Dark mode variants exist but are not used on this site (light mode only)

---

## Design Requirements

- Mobile-first — the majority of visitors will be on phones
- Fast and lightweight — no unnecessary JS, no heavy frameworks
- Clear hierarchy: headline → value prop → features → pricing → CTA
- Match the visual identity of the app (neutral palette, green accent only)
- **No horizontal scrolling on mobile** — never allow overflow-x on any viewport. Reason through layouts at 320px, 375px, and 390px before considering a layout done. Common causes: `flex-shrink: 0` on wide elements, large `min-width` on flex children, `white-space: nowrap`, oversized `calc()` widths.

## Site Structure

- **`tasks/site-structure.md`** — source of truth for which pages exist, what sections they contain, build order, and SEO strategy. Read this at the start of any session that adds pages or sections.
- **Clean URLs** — `vercel.json` sets `cleanUrls: true`. Never use `.html` extensions in internal links; write `/privacy`, `/terms`, `/style-guide`, etc.
- **Existing pages:**
  - `index.html` — main landing page; nav built, hero and remaining sections pending
  - `privacy.html` — Privacy Policy → `/privacy`
  - `terms.html` — Terms of Service → `/terms`
  - `style-guide.html` — design reference → `/style-guide`
- **Homepage copy** — full approved copy for all 7 sections is in `tasks/homepage-copy.md`. Read this before building any section.

---

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
- `frontend-design.md` — design-lead mode for building UI; use with `/frontend-design` before any new section

## Core Principles

- **Simplicity First**: Make every change as simple as possible. Minimal code impact.
- **No Laziness**: Find root causes. No temporary fixes. Senior developer standards.
- **Minimal Impact**: Changes should only touch what's necessary.
