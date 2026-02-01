---
title: Scaffold new platform routes under /app/<platform-segment>
impact: HIGH
impactDescription: Create a clean, non-conflicting App Router tree
tags: routing, scaffold, app-router, layouts
---

## Scaffold new platform routes under /app/<platform-segment>

Create a new App Router subtree at `/app/<platform-segment>` with separate public and authenticated layouts. Keep legacy routes intact and isolated.

### Structure

```
app/
  <platform-segment>/
    layout.tsx
    (public)/
      layout.tsx
      page.tsx
      <public-views>/
    (app)/
      layout.tsx
      <auth-views>/
```

### Rules

- Do not move or rename legacy routes.
- Keep all new views under `app/<platform-segment>`.
- Use explicit role segments only when necessary (e.g., `app/<platform-segment>/(app)/admin/...`).
- If roles share a page, use a single route and guard access within the layout/page.
- Add `loading.tsx`, `error.tsx`, and `not-found.tsx` as needed for UX parity.

### Why this matters

- Avoids route conflicts and keeps migration low risk.
- Provides a clean surface for shadcn-based rebuilds.

### Gotchas

- Ensure legacy CSS does not import into `app/<platform-segment>` layouts.
- Avoid mixing Ant-based components inside new shadcn layouts.
