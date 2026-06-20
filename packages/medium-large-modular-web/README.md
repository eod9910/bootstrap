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
        modules/
          <domain>/
            <domain>.routes.ts
            <domain>.service.ts
            <domain>.types.ts
            <domain>.validators.ts
            <domain>.test.ts
        shared/
          config/
          errors/
          logging/
          http/
          validation/
    web/
      public/
      src/
        pages/
          <domain>/
        components/
        api-client/
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

## Coding Paradigm

This package is organized by product capability. A domain owns the code needed to deliver that capability.

Default backend module shape:

```text
apps/server/src/modules/<domain>/
  <domain>.routes.ts
  <domain>.service.ts
  <domain>.types.ts
  <domain>.validators.ts
  <domain>.test.ts
```

Default frontend domain shape:

```text
apps/web/src/pages/<domain>/
apps/web/src/api-client/
apps/web/src/state/
apps/web/src/components/
```

Use shared folders only for infrastructure or utilities that are genuinely used across domains. Do not create global catch-all `routes/`, `services/`, `utils/`, or `helpers/` folders for domain code.

## Validator Enforcement

Validator owns architecture enforcement for this package.

For every substantial directive, Validator should state:

- selected package: `medium-large-modular-web`;
- affected product domain or new domain name;
- files/modules expected to change;
- whether shared contracts or shared utilities are allowed;
- verification gates;
- STOP conditions for architecture drift.

Validator should reject or revise a plan when it:

- places domain behavior in global technical buckets instead of a domain module;
- creates a parallel engine, cache, workflow, or source of truth;
- introduces a shared abstraction before two real domains need it;
- changes API/domain contracts without naming the affected consumers;
- upgrades architecture without explaining why the current package boundary failed.

## Builder Enforcement

Builder must implement inside the selected package and domain boundary.

Builder should:

- add or change code in the owning domain module first;
- keep routes, service logic, types, validators, and tests together for that domain;
- mirror backend domains in frontend pages/api/state when UI work is involved;
- promote code to `packages/` or `shared/` only when the directive allows it or when at least two domains actually use it;
- report architecture assumptions and any required boundary changes back to Validator.

Builder must stop and report back instead of improvising when:

- the right domain is unclear;
- the work appears to require a new domain;
- the requested change would create duplicate sources of truth;
- a shared package or contract change would affect another domain;
- the smallest correct implementation no longer fits the approved boundary.

## Editor Enforcement

Editor should review for architecture drift as part of the anti-spaghetti pass.

Editor should flag an `EDITOR BLOCKER` when work accepted under this package:

- scatters one domain across unrelated global folders;
- duplicates an existing domain service, contract, cache, or workflow;
- hides product behavior in generic utilities;
- weakens validation, safety, or behavior-preservation evidence while simplifying;
- makes future Validator/Builder ownership unclear.

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
