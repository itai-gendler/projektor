---
kind: person
acts: external
relations:
- entity: feedback
  verb: submits
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: apps/api/src/services/feedback.ts#submitFeedback
---

# Feedback submitter

An end user of another product who sends feedback through that product's feedback widget, without any Projektor account.
