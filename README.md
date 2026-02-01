## Copycat: Start Fresh Without the Hairballs

Copycat doesn't clone your mess. It maps public vs authenticated views, confirms what stays, and scaffolds a clean shadcn platform in Next.js. You copy the good parts, not the chaos.

### Who it’s for
- Designers who want a clean, modern starting point
- Engineers who want clarity on routes, roles, and structure
- Product managers who need a real inventory of what’s still in use
- Business owners who want a new platform without legacy baggage

### What it does (in human terms)
- Separates public pages from authenticated ones
- Identifies role-based views and confirms what to keep
- Runs a naming audit to dedupe role variants into one canonical view
- Renames old, messy view names into clean ones
- Builds a new, isolated platform folder with core routes only
- Adds a simple entry link from the existing landing page

### What it does not do
- It does **not** migrate every legacy screen
- It does **not** change your auth logic
- It does **not** delete old code

### Quick start
1) **Discover** what views exist and who can access them
2) **Audit** naming to dedupe role variants and set canonical names
3) **Confirm** which views are still needed (and rename them cleanly)
4) **Name** your new platform and route segment
5) **Scaffold** a clean boilerplate under `app/<platform-segment>`
6) **Link** it from the existing landing header

### Where to look next
- `SKILL.md` for the workflow overview and checkpoints
- `reference.md` for scans, mapping tips, and gotchas
- `examples.md` for inventory and scaffold examples
- `rules/` for focused rules you can follow step by step
