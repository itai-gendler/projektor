---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent changes a select field's label and options
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product saves the custom field definition
  kind: product
  actor: ai-agent
  entities:
  - {entity: custom-field, effect: changes, facts: [Label, Options]}
  contexts:
    agent:
      place: mcp
---

# Change a field's options

## Trigger

A field's choices change.

## Outcome

The field offers the new options.
