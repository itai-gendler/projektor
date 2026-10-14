---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent invites an email address with a role
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product records the person if Projektor has not seen them yet
  kind: product
  actor: ai-agent
  entities:
  - {entity: user, effect: creates, facts: [Email, Name, Public viewer]}
  contexts:
    agent:
      place: mcp
- text: The Product gives them a workspace membership with the role, clearing any earlier removal
  kind: product
  actor: ai-agent
  entities:
  - {entity: workspace-membership, effect: creates, facts: [Role, Joined at]}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Invite a person by email

## Trigger

Someone needs to join the workspace.

## Outcome

The person is a member with the role and sees projects once a group grants them.

## Edge cases

- Inviting someone who is already a member is refused as a conflict.
