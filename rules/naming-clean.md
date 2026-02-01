---
title: Use clean, confirmed names for new views
impact: MEDIUM
impactDescription: Enforce clear naming and avoid legacy labels
tags: naming, views, routes
---

## Use clean, confirmed names for new views

All new platform views must use confirmed, clean names. Do not carry forward legacy or placeholder naming.

### Rules

- No `New*`, `*V2`, `Temp*`, or legacy prefixes.
- Use domain nouns and outcomes (e.g., `AccountOverview`, `BillingSettings`).
- Route segments in kebab-case; component names in PascalCase.
- If a view is deprecated, do not recreate it.
 - Prefer canonical names from the route naming audit.

### Why this matters

- Prevents naming drift and duplicate routes.
- Ensures the new UI reflects current product vocabulary.

### Gotchas

- Menus often reference outdated labels; verify against actual routes.
- Multiple folders for the same view indicate sprawl; consolidate.
