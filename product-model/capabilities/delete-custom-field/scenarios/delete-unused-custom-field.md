---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent deletes a custom field definition
  kind: actor
  actor: ai-agent
  entities:
  - {entity: custom-field, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: No issue holds a value for it
  kind: condition
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: [Custom fields]}
  contexts:
    agent:
      place: mcp
- text: The Product deletes the custom field definition
  kind: product
  actor: ai-agent
  entities:
  - {entity: custom-field, effect: removes}
  contexts:
    agent:
      place: mcp
---

# Delete an unused field

## Trigger

A field is no longer tracked.

## Outcome

The field is gone.

## Edge cases

- A field some issue still has a value for is refused as a conflict.
