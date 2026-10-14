---
availability:
- place: mcp
domain: coordination
references:
- kind: code
  role: implementation
  target: apps/api/src/services/agents.ts#finishWork
---

# Finish work

In one call an agent optionally moves its issue on, under the same completion report rules as any status change, then releases everything its session holds and ends the session.
