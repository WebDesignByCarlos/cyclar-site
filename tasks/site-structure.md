# Cyclar Site — Content Structure

Source of truth for the site's page and section plan. Update this as the site evolves.

Last updated: 2026-06-18

---

## SEO Strategy

**Decision:** No blog at this stage. Personal finance content is dominated by NerdWallet, Bankrate, YNAB, and similar — SEO payoff is poor for a solo product. Focus energy on a well-optimized landing page first.

**Future consideration:** Feature sub-pages (`/bill-tracker`, `/debt-tracker`, `/cashflow-tracker`) targeting long-tail searches. One-time effort, no ongoing content requirement. Revisit after the core site is live.

---

## Pages

| File | Purpose |
|---|---|
| `index.html` | Main landing page — does all conversion work |
| `privacy.html` | Privacy Policy — US general, contact via email |
| `terms.html` | Terms of Service — US general |

---

## Navigation

Persistent across all pages. Sticky on scroll.

| Element | Destination | Notes |
|---|---|---|
| Logo (`logo-light-mode.svg`) | `/` | Full logo (mark + wordmark) |
| Features | `/#features` | Anchor link |
| Pricing | `/#pricing` | Anchor link |
| Sign In | `https://cyclar.app` | External, same tab |
| Try Free (CTA button) | `https://cyclar.app/signup` | Brand green; primary action |

Mobile nav: hamburger menu or simplified inline row (logo left, CTA button right).

---

## `index.html` — Home

Clear hierarchy: Hero → Problem → Features → Differentiators → Pricing → CTA → Footer

---

### Section 1 — Hero

The primary first impression. Must answer "what is this and why should I care" in under 5 seconds.

**Content:**
- Headline: `"Know where you stand."` (approved tagline)
- Sub-headline: 1–2 sentences on certainty / replacing financial anxiety with clarity
- Primary CTA button: `"Try free for 30 days"` → cyclar.app/signup
- Trust line below button: `"No credit card required."`
- Visual: phone frame with app screenshot — use `lightmode-manage-screen.jpg` or `lightmode-bill-instance-detail-drawer.jpg`

---

### Section 2 — Problem / Emotional Hook

Bridges the hero to the features. Sets up the emotional resonance before showing product.

**Content:**
- Frame the low-grade financial anxiety most people carry
- Transition: Cyclar turns uncertainty into understanding
- 3–4 short statements framed as questions (from marketing reference): "Am I okay?", "Can I afford this?", "What's coming next?", "Am I making progress?"
- No screenshots here — text-focused, typographic treatment

---

### Section 3 — Features (`id="features"`)

Show what the app does through its key screens. Each feature gets a headline, 2–3 sentences, and a screenshot.

| Feature | Screenshot(s) | Key Copy Angle |
|---|---|---|
| **Bills** — track recurring expenses | `lightmode-collapsed-bills.jpg` | Categories (Loans, Subscriptions, Utilities, Spending); recurrence; active/inactive |
| **Manage** — cashflow by period | `lightmode-manage-screen.jpg` | Paycheck-to-paycheck view; outstanding/upcoming/paid sections; one-time bills |
| **Analytics** — historical charts | `lightmode-analytics-2.jpg` | Net cashflow, spending breakdown, income vs. bills; drill into transactions |
| **Debt Tracker** — loan payoff | `lightmode-debt-overview-screen.jpg` | Progress bars, projected payoffs, payment history, compound interest estimates |

Layout: alternating text-left/image-right on desktop; stacked on mobile.

---

### Section 4 — Differentiators

Short, punchy comparison section. Not a feature list — a positioning statement.

**Three differentiators (each 1 headline + 2–3 sentences):**
1. **vs. automation-first apps** — Cyclar doesn't manage your money for you; it helps you understand it. Intentional data entry builds ownership.
2. **vs. spreadsheets** — Feels like a native mobile app. Large tap targets, no formulas, no rebuilding layouts when life changes.
3. **Intentional by design** — No bank linking, no algorithm. You maintain your data; you understand your finances.

---

### Section 5 — Pricing (`id="pricing"`)

Three-column or card layout. Emphasize trial and free tier to reduce friction.

| Plan | Price | What You Get |
|---|---|---|
| **Free** | $0 forever | Up to 5 recurring bills + 2 income sources |
| **Pro** | $5/month | Unlimited bills and income sources |
| **Free Trial** | 30 days free | Full Pro access — no card required |

**Supporting copy:**
- Trial callout: "Every new account starts with 30 days of full access. No card required."
- Free tier note: One-time bills and income are always unlimited on the free plan.
- Billing note: Cancel anytime. Billed monthly via Stripe.

Primary CTA below the table: `"Start your free trial"`

---

### Section 6 — Final CTA

Simple, high-confidence close. Single focused action.

**Content:**
- Headline: something closing/affirming (e.g., "Start knowing where you stand.")
- 1-sentence sub-line
- Single CTA button: `"Try free for 30 days"` → cyclar.app/signup
- Trust reinforcement: "No card required. Cancel anytime."

---

### Section 7 — Footer

Minimal. Links only.

**Content:**
- Logomark (`logos/logomark.svg`) + "Cyclar"
- Links: Privacy Policy (`/privacy.html`), Terms of Service (`/terms.html`)
- App link: `cyclar.app`
- Copyright: `© 2026 Cyclar`

---

## `privacy.html` — Privacy Policy

**Sections:**
- Simplified nav (logo + "Back to cyclar.co" link)
- Page title: "Privacy Policy"
- Last updated date
- Policy content (to be drafted — covers data collection, Supabase, Stripe, no third-party selling)
- Footer (same as home)

---

## `terms.html` — Terms of Service

**Sections:**
- Simplified nav (logo + "Back to cyclar.co" link)
- Page title: "Terms of Service"
- Last updated date
- Terms content (to be drafted — covers acceptable use, subscription terms, cancellation)
- Footer (same as home)

---

## Screenshots Available

Located at `assets/images/screenshots/`. Light mode only on marketing site.

| File | Best Used In |
|---|---|
| `lightmode-manage-screen.jpg` | Hero visual, Features → Manage section |
| `lightmode-collapsed-bills.jpg` | Features → Bills section |
| `lightmode-analytics-2.jpg` | Features → Analytics section |
| `lightmode-debt-overview-screen.jpg` | Features → Debt Tracker section |
| `lightmode-bill-instance-detail-drawer.jpg` | Hero or Features detail callout |
| `lightmode-debt-overview-drawer.jpg` | Features → Debt detail callout |
| `lightmode-income-screen.jpg` | Features → Bills/Income section |
| `lightmode-settings.jpg` | Settings mention if needed |
| `lightmode-login-screen.jpg` | Auth flow mention if needed |

---

## Build Order (suggested)

1. Shared styles and layout scaffolding (tokens already exist)
2. Nav component
3. Footer component
4. Hero section
5. Problem/Emotional Hook section
6. Features section
7. Differentiators section
8. Pricing section
9. Final CTA section
10. Privacy Policy page
11. Terms of Service page
