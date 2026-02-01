---
title: Run a route naming audit (librarian pass)
impact: HIGH
impactDescription: Normalize view names and dedupe role variants
tags: naming, routes, discovery, roles, inventory
---

## Run a route naming audit (librarian pass)

Before naming or scaffolding new views, inventory how the same view is named across routes, menus, headings, and containers. Create a canonical name and route segment for each view.

### How to derive canonical names
1) Collect evidence per view:
- route segment and folder name
- page metadata or document title
- primary page heading (h1, PageHeader)
- navigation or breadcrumb labels
- component or container name
2) Prefer the most stable domain noun or outcome:
- remove role prefixes unless the view is truly role-exclusive
- collapse variants (Reports, NewReports, ReportsV2 -> Reports)
- keep route segment kebab-case and short
3) Record a naming map:
- CanonicalName -> canonical route segment -> role variants -> evidence -> notes
4) Only ask the user when evidence conflicts or is missing.

### Output template
```
CanonicalName: <name>
CanonicalRoute: /<segment>
Variants:
- <role> <label> -> <route> (evidence: <h1/nav/component>)
Notes: <role gate or dedupe decision>
```

### Gotchas
- Menu labels often drift from real routes; trust actual routes and page headings.
- Route groups and nested layouts can hide the real label; inspect page content.
- Duplicated views per role should become one route with role gating.
