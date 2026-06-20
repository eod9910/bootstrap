# Package: small-node-static-web

Use this package for small apps where speed, readability, and one-command startup matter more than frontend architecture.

## Intended User

This package is for a non-coder-friendly project start: easy to open, easy to run, and easy for agents to inspect.

## Default Stack

- Backend: Node, Express, TypeScript.
- Frontend: plain HTML, CSS, and JavaScript.
- Runtime: backend serves static frontend files.
- Dev command: `npm run dev`.

## Target Shape

```text
<project>/
  AGENTS.md
  TRI_AGENT_CODING_CONTRACT.md
  memory-bank/
  agent-relay/
  tools/

  backend/
    package.json
    tsconfig.json
    src/
      server.ts
      routes/
      services/
      types/
    data/

  frontend/
    public/
      index.html
      app.js
      styles.css

  package.json
  README.md
```

## Rules

- Keep one backend process as the thing the user starts.
- Do not add Vite, React, or frontend TypeScript by default.
- Keep frontend JavaScript modular enough to read, but do not invent a framework.
- Add a frontend build system only when a Validator directive says the UI has outgrown this package.
- Backend APIs should be typed and validated at trust boundaries.

## Upgrade Trigger

Move to `medium-large-modular-web` when the frontend develops complex state, the backend grows several domains, or multiple agents need stable ownership boundaries.
