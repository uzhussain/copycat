---
title: Confirm view list and naming before scaffold
impact: HIGH
impactDescription: Prevent building deprecated or misnamed views
tags: confirmation, naming, views, roles
---

## Confirm view list and naming before scaffold

Do not scaffold new views until the user confirms which views are active and what the new names should be.

### Required confirmation

For each role, confirm:
- Public views (unauthenticated).
- Authenticated views.
- Role-specific views and the gating location.
- Which views are deprecated or unused.
- The canonical name for each view (from the route naming audit).

### Output template

```
UserRole: <role name>
Public views (unauthenticated):
- <View Title> -> <route> (source: <file>)

Authenticated views:
- <View Title> -> <route> (source: <file>)

Role-specific views:
- <View Title> -> <route> (role gate: <where>)

Status:
- Recreate in new platform: YES / NO
- Rename required: YES / NO
- New name (if renamed): <confirmed title>
```

### Why this matters

- Prevents wasted work on deprecated or renamed views.
- Ensures clean, consistent naming in the new platform.

### Gotchas

- Old view names often exist in menus but are not routed. Verify live routes.
- Placeholder views like `NewPage` or `*V2` are often stale; confirm.
