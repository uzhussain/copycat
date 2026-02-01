---
title: Derive platform name and route segment from existing copy
impact: HIGH
impactDescription: Avoid naming prompts and keep the new platform discoverable
tags: naming, routes, platform, discovery
---

## Derive platform name and route segment from existing copy

Do not ask the user to name the new platform folder. Derive a stable platform name and route segment from existing copy, then use it consistently.

### Steps
1) Scan stable sources:
- Terms, privacy, or legal pages
- Footer product name and copyright
- Marketing hero headline and primary nav
- App shell title or logo text
2) Choose a simple platform name from the strongest signal.
3) Generate the route segment:
- kebab-case
- short, brand-based, no spaces
4) If the base segment already exists in legacy routes, append `-v2`.
5) Default `platformFolderName` to `platformRouteSegment`.
6) Default landing dropdown labels to the platform name.

### Gotchas
- Do not use `New*` or `*V2` for view names; `-v2` is only for the platform root if needed to avoid collisions.
- If no clear signal exists, use a neutral base like `platform`.
