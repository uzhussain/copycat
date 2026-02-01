---
title: Build a clean boilerplate, not a full migration
impact: HIGH
impactDescription: Keep the new platform minimal and intentional
tags: scaffold, boilerplate, scope, migration
---

## Build a clean boilerplate, not a full migration

The goal is a clean, minimal base with core navigation and routes. Do not carry over every legacy view.

### Rules

- Only scaffold views that are confirmed as required.
- Favor a small, well-structured route set over feature parity.
- Keep layouts, navigation, and auth gates minimal and composable.
- Leave deprecated or low-value views behind.

### Why this matters

- Avoids rebuilding debt and legacy complexity.
- Gives teams a clean base to add new fidelity.

### Gotchas

- Do not conflate "inventory" with "rebuild." Confirm scope.
