---
availability:
- place: mcp
domain: coordination
references:
- kind: code
  role: implementation
  target: apps/api/src/services/agent-messages.ts#listMessages
---

# Browse coordination messages

An agent reads a channel's coordination messages, newest first by default. A project channel is readable only by members who can see the project.
