---
scope: The Cloudflare Worker (REST API, MCP server, OAuth consent), the Astro web app and the database schema.
method: Static inspection of source, schema migrations and the project's documentation at the pinned commit.
covered:
- description: Worker services, REST routes, MCP tools, input schemas, authentication, authorization and OAuth consent.
  paths:
  - apps/api/src/services/
  - apps/api/src/routes/
  - apps/api/src/mcp/
  - apps/api/src/schemas/
  - apps/api/src/middleware/
  - apps/api/src/auth/
  - apps/api/src/oauth/
  - apps/api/src/index.ts
- description: Web app pages, islands and layout.
  paths:
  - apps/web/src/pages/
  - apps/web/src/islands/
  - apps/web/src/layouts/
- description: Database schema and migrations.
  paths:
  - packages/db/
- description: Shared environment and request types.
  paths:
  - packages/types/
exclusions:
- description: Documentation site.
  paths:
  - apps/docs/
- description: Unit, integration and end-to-end tests.
  paths:
  - apps/api/src/test/
  - apps/web/e2e/
  - apps/web/src/test/
- description: Build, release, CI, generators and repository tooling.
  paths:
  - scripts/
  - .github/
  - apps/api/scripts/
  - apps/web/scripts/
  - bundle-budget.json
  - turbo.json
  - biome.json
  - lefthook.yml
- description: Design notes and implementation plans kept in the repository.
  paths:
  - docs/
- description: Plugin SDK and plugins, which the running Worker does not load.
  paths:
  - packages/plugin-sdk/
  - plugins/
  - apps/api/src/plugins/
- description: Web styling, shared UI components and client plumbing.
  paths:
  - apps/web/src/styles/
  - apps/web/src/islands/ui/
  - apps/web/src/utils/
  - apps/web/src/lib/
- description: 'Request plumbing: body parsing, error adapters and URL helpers.'
  paths:
  - apps/api/src/http/
  - apps/api/src/lib/urls.ts
  - apps/api/src/examples/
unmapped:
- description: 'Opt-in real-time events, left out: they only push changes the model already describes to open views, when the deployment enables them.'
  paths:
  - apps/api/src/services/realtime.ts
  - apps/api/src/realtime/
  - apps/api/src/routes/realtime.ts
- description: Rate limiting of requests, failed sign-ins and feedback submissions, left out as abuse-protection plumbing.
  paths:
  - apps/api/src/middleware/rate-limit.ts
  - apps/api/src/lib/rate-limiter-do.ts
- description: REST-only endpoints no web or MCP control offers (share link revocation, personal tokens, wiki export, workspace logo upload), left out because the project calls its REST API the web app's private contract.
  paths:
  - apps/api/src/routes/share.ts
  - apps/api/src/routes/auth.ts
  - apps/api/src/services/wiki-export.ts
- description: Wiki link-graph backfill and the daily retention purges of old notifications, sessions and activity, left out as maintenance plumbing.
  paths:
  - apps/api/src/services/wiki-links.ts
  - apps/api/src/services/activity.ts
limitations:
- description: OAuth token issuance and refresh, served by the OAuth library before the Worker's own routes.
  paths:
  - apps/api/src/oauth/provider.ts
---

# Coverage
