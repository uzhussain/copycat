# Examples

## Example: View inventory output
```
UserRole: Admin
Public views (unauthenticated):
- Landing -> / (source: app/(marketing)/page.tsx)
- Pricing -> /pricing (source: app/(marketing)/pricing/page.tsx)

Authenticated views:
- Dashboard Home -> /app (source: app/(app)/page.tsx)
- Analytics -> /app/analytics (source: app/(app)/analytics/page.tsx)

Role-specific views:
- Admin Users -> /app/admin/users (role gate: app/(app)/admin/layout.tsx)

Status:
- Recreate in new platform: YES
- Rename required: YES
- New name (if renamed): UserManagement
```

## Example: Platform naming inputs
```
platformName: Acme Platform
platformRouteSegment: platform
platformFolderName: platform
landingDropdownLabel: Acme Platform
landingDropdownItemLabel: Acme Platform
```

## Example: New platform scaffold
```
app/
  platform/
    layout.tsx
    (public)/
      layout.tsx
      page.tsx
      pricing/
        page.tsx
    (app)/
      layout.tsx
      dashboard/
        page.tsx
      analytics/
        page.tsx
      admin/
        users/
          page.tsx
```
