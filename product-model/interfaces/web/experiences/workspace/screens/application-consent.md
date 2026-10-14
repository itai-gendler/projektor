---
entities:
- entity: connected-application
  shows: [Application, Access]
- entity: workspace
  shows: [Name]
- entity: workspace-membership
  shows: [Role]
entryPoints:
- web: /oauth/authorize
references:
- kind: code
  role: implementation
  target: apps/api/src/routes/oauth.ts
---

# Connect an application

The consent page an application's connector sign-in sends the person to, naming the application, the workspace, the access asked for and the person's own role.
