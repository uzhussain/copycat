---
name: nextjs-auth-view-discovery
description: Inventory a Next.js app's marketing and dashboard views by authenticated vs unauthenticated roles, confirm view names with the user, and plan a shadcn-based clean platform scaffold in a separate App Router folder using user-confirmed naming and route segments. Use when auditing role-based views, planning shadcn UI recreation, or splitting auth vs public routes.
---

# Next.js Auth View Discovery + Clean Platform Scaffold

Locate and classify all marketing and dashboard views for authenticated vs unauthenticated users, map them to userRole types, and confirm which views should be recreated in the new shadcn-based platform. Create a clean, non-conflicting App Router folder for the new platform using user-confirmed naming (platform name, base route segment, folder name) with separate public and authenticated layouts. Add a header dropdown on the original landing page that links to the new platform.

## When to Apply

- The app is Next.js (App Router or Pages Router) and needs a role-based view inventory.
- The UI is being recreated with shadcn and requires a clean route scaffold.
- There are both marketing (public) and dashboard (auth) views with unclear naming.
- The old app has inconsistent or deprecated view names that must be confirmed.

## Version Policy

Use the latest stable versions of:
- `next` (App Router preferred)
- `react`
- `tailwindcss`
- `shadcn/ui` components via CLI or MCP

## Rule Categories by Priority

| Priority | Category                         | Impact   | Prefix        | Rules |
| -------- | -------------------------------- | -------- | ------------- | ----- |
| 1        | Discovery & Confirmation         | CRITICAL | `discovery-`, `confirm-` | 2 |
| 2        | Platform Scaffold & Boilerplate  | HIGH     | `routing-`, `boilerplate-` | 2 |
| 3        | Coexistence & Entry              | MEDIUM   | `coexistence-`, `landing-` | 2 |
| 4        | Naming & Testing                 | LOW      | `naming-`, `test-` | 2 |

## Core Outcomes

- A confirmed list of views by userRole and auth state (public vs authenticated).
- A validated naming plan for new view titles (no legacy naming).
- A new, isolated App Router folder for the new platform with user-confirmed naming.
- A landing-page header dropdown linking to the new platform.
- A lean boilerplate scaffold with core navigation/routes only (not a full migration).

## Platform Naming Inputs (Required)

Confirm these before scaffolding:
- `platformName`: Display label for the new platform (e.g., "Acme Platform").
- `platformRouteSegment`: Base URL segment and route group (kebab-case, e.g., `platform`).
- `platformFolderName`: Folder under `/app` (default: `platformRouteSegment`).
- `landingDropdownLabel`: Header dropdown label (default: `platformName`).
- `landingDropdownItemLabel`: Link label (default: `platformName`).

If not provided, derive from repo name or existing product naming in the header, then confirm before creating folders/routes.

## Discovery Order

1) Identify router type and entry points.
2) Inventory all routes and views.
3) Locate auth boundaries and role checks.
4) Classify each view by auth state and userRole.
5) Confirm the view list and naming with the user.
6) Confirm platform naming inputs (name, route segment, folder).
7) Plan the clean platform folder structure and minimal core routes.
8) Add the landing header dropdown link.

## Scans and Mapping

Run scans to discover routes, guards, and role checks:
```bash
# App Router vs Pages Router
rg --files -g"app/**/page.{ts,tsx,js,jsx}"
rg --files -g"pages/**/*.{ts,tsx,js,jsx}"

# Layouts and route groups
rg --files -g"app/**/layout.{ts,tsx}"

# Auth and role checks
rg "useSession|useAuth|getServerSession|auth\\(|requireAuth|withAuth|middleware" .
rg "role|roles|userRole|permissions|rbac|policy" .

# Navigation and landing header
rg "Header|Navbar|Navigation|Menu|Dropdown" app pages src components
```

Map findings to:
- **Public (marketing) views**: landing, pricing, docs, waitlist, onboarding info.
- **Authenticated (dashboard) views**: home, analytics, management, settings, billing.
- **Role-specific views**: admin-only, manager-only, analyst-only, etc.

## View Inventory Template

Use this format to confirm with the user:
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

## Confirmation Loop (Required)

Do not scaffold new views until the user confirms:
1) The view list for each userRole.
2) Which views are deprecated or no longer used.
3) The new naming for each view to be recreated.

If any view is unclear, pause and ask for clarification. Only proceed with confirmed names.

## Naming Rules for New Views

- Use clean, descriptive names (no "New", "V2", "Temp", or legacy prefixes).
- Prefer domain nouns and outcomes (e.g., "AccountOverview", "BillingSettings").
- Keep route segments in kebab-case, component names in PascalCase.
- If a view is deprecated, do not recreate it.

## New Platform App Router Structure

Create a new, isolated folder under `/app` to avoid conflicts:
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

Guidelines:
- Keep existing routes intact. Do not move or rename old files.
- Use `app/<platform-segment>` as the base for all new platform routes.
- If a role needs a distinct URL segment, use explicit routes like `app/<platform-segment>/(app)/admin/...`.
- If roles share a page, keep a single route and gate access inside the page/layout.

## Boilerplate-First (Required)

Do not migrate everything. Create a clean boilerplate with only the core navigation and routes needed to start building new fidelity. Only add views that are confirmed as required.

## Landing Header Dropdown (Original Frontend)

Add a dropdown to the existing landing page header:
- Label: `landingDropdownLabel`
- Item: `landingDropdownItemLabel` -> `/<platform-segment>`

Use shadcn `DropdownMenu` when possible, but match the existing header style and structure.

## Shadcn Usage Rules

- Recreate confirmed views using shadcn components and Tailwind utilities.
- Use shadcn CLI or MCP for new components, do not hand-roll replacements.
- Keep new components under the new platform folder unless shared across platforms.

## Post-Scaffold Verification

- The new `/<platform-segment>` routes load without affecting legacy routes.
- Public vs authenticated layouts are clearly separated.
- The landing header dropdown links to the new platform base route.
- No deprecated views were scaffolded.
- All new view names match the user-confirmed list.

## Rule Index

- Priority 1:
  - Discovery: `rules/discovery-auth-views`
  - Confirmation: `rules/confirm-view-names`
- Priority 2:
  - Routing: `rules/routing-platform-scaffold`
  - Boilerplate: `rules/boilerplate-first`
- Priority 3:
  - Coexistence: `rules/coexistence-legacy`
  - Landing: `rules/landing-header-dropdown`
- Priority 4:
  - Naming: `rules/naming-clean`
  - Testing: `rules/test-auth-flows`
