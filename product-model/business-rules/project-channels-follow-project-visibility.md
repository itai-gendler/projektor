---
appliesTo:
- type: capability
  id: browse-coordination-messages
- type: entity
  id: coordination-message
  facts: [Channel]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/agent-messages.ts#listMessages
---

# A project's coordination channel is readable only by those who can see the project

Messages on a project's or an issue's channel are listed only for members who can see that project.
