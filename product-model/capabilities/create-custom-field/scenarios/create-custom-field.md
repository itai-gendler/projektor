---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent defines a select field with its options
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product adds the custom field definition; issues can hold a value for it from now on
  kind: product
  actor: ai-agent
  entities:
  - {entity: custom-field, effect: creates, facts: [Key, Label, Field type, Options, Project, Internal]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Define a select field

## Trigger

The team wants to track something the built-in fields do not.

## Outcome

Issues can carry the new field.

## Edge cases

- A key the workspace already uses is refused.
