## Next.js Auth View Discovery + Clean Platform Scaffold Skill

Guidance and rule set to inventory role-based views, confirm naming, and build a clean shadcn-based platform scaffold without fully migrating legacy UI. Focuses on authenticated vs unauthenticated views, role gating, minimal core navigation/routes, coexistence boundaries, and a new platform entry in the landing header.

### What’s inside
- `SKILL.md` — overview, priorities, discovery order, naming inputs, and rule index.
- `rules/` — focused rules for discovery, confirmation, platform scaffold, boilerplate-first scope, coexistence, landing dropdown, naming, and testing.

### When to use
- You have a Next.js app with marketing + dashboard views and unclear role-based routing.
- You need a clean platform scaffold with shadcn components, not a full migration.
- You want a confirmed view list and naming plan before building new routes.

### Quick start (conceptual)
1) **Discover**: map routes, auth boundaries, and role gates.
2) **Confirm**: validate view list and new names per role.
3) **Name platform**: confirm platform label, route segment, and folder name.
4) **Scaffold**: create `app/<platform-segment>` with public/app layouts.
5) **Entry**: add landing header dropdown link to the new platform.
6) **Verify**: smoke-check public/auth routes and role gates.

### Key rule highlights
- **Discovery & confirmation**: inventory public/auth/role views and confirm names.
- **Platform scaffold**: isolated `app/<platform-segment>` with clean layouts.
- **Boilerplate-first**: build minimal core routes, avoid full migration.
- **Coexistence**: keep legacy UI isolated and prevent style bleed.
- **Landing entry**: dropdown link to the new platform.
- **Testing**: basic smoke checks for auth and routing.
