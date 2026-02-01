# Reference: Auth View Discovery + Clean Scaffold

## Discovery scans
```bash
# App Router vs Pages Router
rg --files -g"app/**/page.{ts,tsx,js,jsx}"
rg --files -g"pages/**/*.{ts,tsx,js,jsx}"

# Layouts and route groups
rg --files -g"app/**/layout.{ts,tsx,js,jsx}"

# Auth and role checks
rg "useSession|useAuth|getServerSession|auth\\(|requireAuth|withAuth|middleware" .
rg "role|roles|userRole|permissions|rbac|policy" .

# Navigation and landing header
rg "Header|Navbar|Navigation|Menu|Dropdown" app pages src components
```

## Mapping guidance
- Public (marketing) views: landing, pricing, docs, waitlist, onboarding info.
- Authenticated (dashboard) views: home, analytics, management, settings, billing.
- Role-specific views: admin-only, manager-only, analyst-only, etc.
- Record both menu labels and actual routes to avoid stale naming.

## Auth and role notes
- Track where auth gates occur (server layouts, middleware, client effects).
- Preserve existing redirect behavior; do not change auth logic.
- Note role source (session, JWT claims, DB, feature flags).

## Confirmation loop
1) Present the full view inventory per role.
2) Ask which views are active vs deprecated.
3) Confirm the new name for each view to be recreated.
4) Confirm platform naming inputs before creating folders.

## Naming rules
- No `New*`, `*V2`, `Temp*`, or legacy prefixes.
- Prefer domain nouns/outcomes: `AccountOverview`, `BillingSettings`.
- Route segments in kebab-case; component names in PascalCase.

## Scaffold notes
- Keep new routes under `app/<platform-segment>`.
- Separate public and authenticated layouts.
- Add `loading.tsx`, `error.tsx`, `not-found.tsx` only if needed for parity.
- Avoid importing legacy global CSS into new layouts.

## Landing header dropdown
- Label: `landingDropdownLabel`
- Item label: `landingDropdownItemLabel`
- Item href: `/<platform-segment>`
- Match existing header layout and responsive behavior.

## Coexistence precautions
- Do not mix legacy components into new shadcn layouts.
- Avoid shared portal roots and conflicting z-index stacks.

## Post-scaffold verification
- Public routes load unauthenticated.
- Auth routes redirect when unauthenticated.
- Role-gated routes block unauthorized roles.
- Landing dropdown navigates to `/<platform-segment>`.
- No console errors on load.
