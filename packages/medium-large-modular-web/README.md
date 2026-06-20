# Package: medium-large-modular-web

Use this package for apps that should start simple to run but structured enough to grow.

## Intended User

This package is for long-lived products, larger dashboards, trading/research tools, plugin-based systems, and apps with several known product domains.

## Default Stack

- Backend: Node, Express, TypeScript.
- Frontend: TypeScript-ready modular app served by the backend.
- Shared contracts: API and domain types live outside individual modules.
- Runtime: one command still starts the app.
- Architecture: modular monolith, not microservices.

## Target Shape

```text
<project>/
  AGENTS.md
  TRI_AGENT_CODING_CONTRACT.md
  memory-bank/
  agent-relay/
  tools/

  apps/
    server/
      src/
        app.ts
        routes/
        modules/
          <domain>/
            routes.ts
            service.ts
            types.ts
            validators.ts
        shared/
          config/
          errors/
          logging/
          validation/
    web/
      public/
      src/
        api-client/
        components/
        pages/
        state/
        styles/

  packages/
    contracts/
      api/
      domain/
    shared-utils/

  data/
  package.json
  README.md
```

## Rules

- Keep the app one-command runnable.
- Split by product capability, not by technical layer alone.
- Prefer a modular monolith over microservices.
- Keep shared contracts explicit so frontend/backend drift is visible.
- Do not create parallel engines, caches, workflows, or sources of truth without Validator approval.
- Use TypeScript where contracts, services, and state would otherwise become fragile.

## Example Domains

Pattern Detector-sized projects might start with modules like:

- scanner;
- charting;
- strategies;
- backtests;
- broker;
- universe;
- plugins;
- auth/settings.

## Downgrade Rule

If the project is only a prototype or a tiny internal tool, use `small-node-static-web` instead. Bigger scaffolds carry more ceremony, so they should be earned by real product complexity.
