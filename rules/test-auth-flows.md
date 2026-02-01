---
title: Smoke-test public and auth views
impact: LOW
impactDescription: Catch basic regressions in auth and navigation
tags: testing, auth, routing, navigation
---

## Smoke-test public and auth views

Add lightweight smoke checks to ensure `/<platform-segment>` routes load and auth gating works.

### Checklist

- Public routes load unauthenticated.
- Authenticated routes redirect when unauthenticated.
- Role-gated routes block unauthorized roles.
- Landing dropdown link navigates to `/<platform-segment>`.
- No console errors on load.

### Why this matters

- Prevents basic regressions during phased migration.

### Gotchas

- Use test users/fixtures and avoid external dependencies.
