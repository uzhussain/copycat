---
title: Discover auth vs public views and roles
impact: HIGH
impactDescription: Preserve public/auth flows and role access while rebuilding
tags: discovery, routing, auth, roles, views
---

## Discover auth vs public views and roles

Inventory how users enter the app, which routes are public vs authenticated, and how roles/guards are enforced. Preserve behavior while rebuilding shadcn layouts; do not change auth.

### Steps

1) Identify router type:
- App Router: `app/**/page.*` and `app/**/layout.*`
- Pages Router: `pages/**/*.*` plus custom `_app`, `_document`

2) Map routes and entry points:
- Locate router config, route groups, and menu definitions.
- Identify marketing pages vs dashboard/app shell.
- Record public routes, protected routes, and role-gated paths.

3) Identify auth/guard mechanisms:
- Auth hooks/HOCs (`useSession`, `useAuth`, `RequireAuth`, `withAuth`), middleware, cookie checks.
- Note where redirects happen; keep logic intact.

4) Capture role metadata:
- Collect roles/permissions objects, menu-role mappings, guard functions.
- Track where role data is derived (JWT, session, DB, feature flags).

### Why this matters

- Prevents breaking login/role flows during a UI rebuild.
- Ensures nav/breadcrumbs reflect role-based access.

### Gotchas

- `useEffect` redirects can hide missing server guards; document and preserve.
- Magic-link or invite flows often rely on query params; do not break them.
