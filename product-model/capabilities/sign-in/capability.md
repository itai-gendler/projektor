---
availability:
- place: web::workspace
domain: workspace
references:
- kind: code
  role: implementation
  target: apps/api/src/services/provisioning.ts#ensureUserProvisioned
- kind: code
  role: implementation
  target: apps/api/src/middleware/auth.ts#authMiddleware
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/architecture/access-control.mdx
  title: Access control
---

# Sign in

A person admitted by the deployment's Cloudflare Access sign-in reaches Projektor, which records them and gives them what the deployment settings say: ownership of every workspace for an admin email, a membership of a domain-mapped workspace, a membership of the default workspace while auto-join is on, or nothing until someone invites them.
