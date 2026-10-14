---
appliesTo:
- type: entity
  id: workspace-membership
  effect: creates
permits:
- related: [{verb: admits, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: admits, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
  - {entity: ai-agent, fact: Scope, is: Read and write}
- related: [{verb: admits, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: admits, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
  - {entity: ai-agent, fact: Scope, is: Read and write}
- configuredBy: deployment-settings
references:
- kind: code
  role: implementation
  target: apps/api/src/services/workspaces.ts#inviteMember
- kind: code
  role: implementation
  target: apps/api/src/services/provisioning.ts#ensureUserProvisioned
---

# Owners and admins invite members; otherwise only the deployment settings add them

A workspace membership is created when a workspace owner or admin invites someone, or at sign-in as the deployment settings say: admin emails own every workspace, a mapped email domain joins its workspace with the mapped role, and an auto-join role joins the default workspace. The anonymous public viewer joins the default workspace as a viewer.
