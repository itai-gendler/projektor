---
appliesTo:
- type: entity
  id: workspace
  effect: creates
permits:
- actors: [user]
- related: [{verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: ai-agent, fact: Scope, is: Read and write}
- configuredBy: deployment-settings
references:
- kind: code
  role: implementation
  target: apps/api/src/services/workspaces.ts#createWorkspace
- kind: code
  role: implementation
  target: apps/api/src/services/provisioning.ts#ensureUserProvisioned
---

# Any signed-in person creates a workspace

Creating a workspace needs no role: the creator becomes its owner. The deployment settings also create the default workspace at the first admin sign-in.
