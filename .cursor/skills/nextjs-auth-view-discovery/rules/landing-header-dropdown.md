---
title: Add new platform link to landing header
impact: MEDIUM
impactDescription: Provide navigation entry to the new platform
tags: landing, header, navigation, dropdown
---

## Add new platform link to landing header

Add a header dropdown on the original landing page to let users navigate to the new platform.

### Requirements

- Dropdown label: `landingDropdownLabel`
- Item label: `landingDropdownItemLabel`
- Item href: `/<platform-segment>`
- Match existing header layout and style
- Prefer shadcn `DropdownMenu` if compatible with the header stack

### Why this matters

- Gives users a clear entry point to the new routes.
- Keeps the migration discoverable without breaking the old site.

### Gotchas

- If the landing header is static, ensure the dropdown does not break layout on mobile.
- Avoid adding global styles or scripts just for the dropdown.
