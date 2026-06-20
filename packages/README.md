# Bootstrap Packages

`agent-memory-bootstrap` is the project creator. New projects should start from a named package instead of hand-copying files.

## Packages

### `small-node-static-web`

Use for small projects, prototypes, internal tools, and simple dashboards.

Default shape:

- Node + TypeScript backend.
- Plain HTML/CSS/JavaScript frontend.
- Backend serves `frontend/public` directly.
- One command starts the app: `npm run dev`.
- No frontend build system unless the project earns it.

### `medium-large-modular-web`

Use for projects expected to grow into larger products, or for existing apps that already have multiple domains like scanner, charting, backtesting, broker integrations, plugins, or complex settings.

Default shape:

- Node + TypeScript backend.
- Structured frontend with TypeScript-ready modules.
- Shared API/domain contracts.
- Modular monolith boundaries by product capability.
- One command still starts the app: `npm run dev`.
- No microservices by default.

## Selection Rule

Start small unless the project already has clear medium/large signals.

Choose `medium-large-modular-web` when any of these are true:

- several product domains are known at project creation;
- frontend state, routing, charting, or settings will be substantial;
- backend needs durable module boundaries;
- more than one agent will likely work on separate areas;
- the project is expected to become a long-lived product rather than a prototype.

## Invariant

Every package should preserve the agent-ready baseline:

- `AGENTS.md` startup routing;
- memory policy and continuity files;
- transcript mirror scripts;
- Validator/Builder/Editor role contracts when tri-agent governance is enabled;
- router workflow when relay routing is enabled;
- one clear verification command after creation.

## Enforcement

Package selection is an agent contract, not just a folder preference.

For new projects, Validator records the selected package in the initial project directive and `AGENTS.md`. Builder follows that package's boundaries during implementation. Editor reviews for drift from the selected package. If a project needs to move from `small-node-static-web` to `medium-large-modular-web`, Validator must authorize the migration explicitly.
