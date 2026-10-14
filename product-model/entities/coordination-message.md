---
domain: coordination
references:
- kind: code
  role: implementation
  target: apps/api/src/services/agent-messages.ts#postMessage
---

# Coordination message

A message an agent posts to a channel so the fleet can talk: the whole workspace, one project or one issue.

## Information kept

- **Channel** — the workspace, a project or an issue
- **Body** — the message text
- **Posted at** — when it was posted
