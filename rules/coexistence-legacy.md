---
title: Keep legacy UI isolated during migration
impact: HIGH
impactDescription: Prevent style bleed and runtime conflicts
tags: coexistence, legacy, css, migration
---

## Keep legacy UI isolated during migration

During a phased rebuild, keep legacy UI and its CSS isolated from the new platform routes.

### Practices

- Do not import legacy global CSS into `app/<platform-segment>`.
- Scope legacy styles to legacy layouts only.
- Avoid mixing legacy components into the new shadcn layouts.
- If legacy UI kits exist (Ant, Chakra, Material, etc.), do not use them in new routes.
- Only use components from the new shadcn `components` directory or generated registry JSON.
- Ensure overlay z-index values do not conflict across shells.

### Why this matters

- Prevents visual regressions and hydration issues.
- Keeps migration safe while both UIs coexist.

### Gotchas

- Legacy CSS resets can override shadcn focus styles.
- Shared portal roots can cause modal collisions; verify.
