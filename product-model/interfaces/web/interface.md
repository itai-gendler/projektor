---
type: web
actors:
- user
- link-visitor
entryPoints:
- web: /
references:
- kind: code
  role: implementation
  target: apps/web/src/layouts/Base.astro
  title: Primary navigation
- kind: code
  role: implementation
  target: apps/api/src/middleware/auth.ts#authMiddleware
  title: Sign-in strategies
---

# Projektor web app

The browser app people use to run their workspace: projects, issues on a list, board or backlog, sprints, epics, the wiki, metrics, groups and agent connection settings. Signed-in people reach it through the deployment's Cloudflare Access sign-in; a shared issue link opens one issue to anyone holding it.
