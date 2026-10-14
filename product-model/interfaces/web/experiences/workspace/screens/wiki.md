---
entities:
- entity: wiki-page
  shows: [Title, Slug, Parent page, Project, Type, Status, Tags, Freshness, Verified at]
  collects: [Title, Slug, Parent page, Project, Content]
entryPoints:
- web: /wiki
references:
- kind: code
  role: implementation
  target: apps/web/src/islands/WikiPage.tsx
---

# Wiki

The wiki's page tree, search, page lists and stale-page queue, with a form to create a page.
