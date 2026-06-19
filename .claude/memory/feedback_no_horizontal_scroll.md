---
name: feedback_no_horizontal_scroll
description: User strongly dislikes horizontal scrolling on mobile — never cause it
metadata:
  type: feedback
---

Never introduce horizontal scrolling on mobile. The user finds it very annoying.

**Why:** Explicitly called out when it appeared on style-guide.html — was a top-of-mind pain point.

**How to apply:** On every layout decision, check that no element can overflow the viewport horizontally on narrow screens (320px–390px). Common causes to watch for:
- `flex-shrink: 0` on wide elements inside flex rows
- Fixed or large `min-width` values in flex/grid children
- `white-space: nowrap` on text that might be wide
- `width: calc(...)` expressions that can exceed viewport width
- Long unbreakable strings (URLs, code) without `overflow-wrap: break-word`

Always test or reason through the layout at 320px (minimum), 375px (iPhone SE), and 390px (iPhone 14) widths before considering a layout done.
