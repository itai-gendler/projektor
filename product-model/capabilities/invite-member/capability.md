---
availability:
- place: mcp
domain: workspace
references:
- kind: code
  role: implementation
  target: apps/api/src/services/workspaces.ts#inviteMember
---

# Invite member

A workspace owner or admin adds a person to the workspace by email with a role. A person Projektor has not seen yet is recorded so they find the membership when they first sign in.
