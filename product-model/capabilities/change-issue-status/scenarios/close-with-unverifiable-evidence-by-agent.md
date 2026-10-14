---
kind: alternative
routes:
  agent: MCP
steps:
- text: The AI agent moves an issue to Done with a completion report whose verification is plain prose
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The verification contains no pull request, CI run, commit link or commit hash
  kind: condition
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: [Completion report]}
  contexts:
    agent:
      place: mcp
- text: The Product closes the issue, flags it as needing audit, posts the report as a comment and releases its lease and file claims
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: changes, from: In review, to: Done, facts: [Completion report, Needs audit, Done at]}
  - {entity: comment, effect: creates, facts: [Body, Author kind, Posted at]}
  - {entity: issue-lease, effect: changes, from: Held, to: Released, facts: [Released at, Release reason]}
  - {entity: file-claim, effect: changes, from: Held, to: Released, facts: [Released at, Release reason]}
  contexts:
    agent:
      place: mcp
references:
- kind: code
  role: implementation
  target: apps/api/src/services/evidence-classification.ts
---

# An agent closes an issue with evidence nothing can check

## Trigger

An agent closes its own work without a human gate.

## Outcome

The issue is done but sits in the audit queue for a person to check.

## Edge cases

- A verification that carries a resolvable link or commit hash closes without the flag.
