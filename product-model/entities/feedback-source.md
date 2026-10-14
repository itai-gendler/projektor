---
domain: feedback
relations:
- entity: feedback
  verb: receives
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: apps/api/src/services/feedback-sources.ts#createFeedbackSource
---

# Feedback source

A named collection point in a project, such as an onboarding survey or an in-app rating widget, with its own public submit token so each integration can be paused, rotated or revoked on its own.

## Information kept

- **Name** — what the source collects
- **Description** — notes on the integration
- **Allowed origins** — the browser origins its widget runs on, a courtesy for browsers only
- **Submit token** — the public token a widget submits with, shown once when created or rotated
- **Created at** — when it was created
- **Revoked at** — when it was revoked

## States

### Active

Accepting feedback.

### Paused

Refusing feedback until resumed, with the same token.

### Revoked

Never accepting feedback again; its history is kept.
