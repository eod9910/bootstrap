# AGENTS.md Package Selection Block

Add this block near the top of a generated project's `AGENTS.md`, after startup/memory routing and before task-specific contracts.

Replace `<selected-package>` and `<project-coding-paradigm-file>` during project creation.

```markdown
## Role Bootloader

`AGENTS.md` instantiates the role workflow by routing each agent to the role documents it must obey:

- Validator reads `agent-relay/roles/Validator/ROLE.md` before freezing requirements, writing directives, judging Builder/Editor reports, or accepting work.
- Builder reads `agent-relay/roles/Builder/ROLE.md` before implementing any Validator directive.
- Editor reads `agent-relay/roles/Editor/ROLE.md` before reviewing, simplifying, refactoring, or marking an `EDITOR BLOCKER`.
- When one running agent is mediating the roles, it must read all three role documents before routing or simulating role handoffs.
```

```markdown
## Project Coding Paradigm

- This project is governed as `<selected-package>`.
- Read `<project-coding-paradigm-file>` before substantial feature, refactor, frontend, backend, domain, or architecture work.
- Package selection is an agent contract, not just a folder preference.
- Validator directives must name the selected package, affected domain, current files, target boundary, shared-contract permission, verification gates, and STOP conditions.
- Builder must implement inside the named package/domain boundary or report back when the boundary is unclear.
- Editor reviews for drift from the selected package and marks architecture drift as an `EDITOR BLOCKER` when it would create or preserve spaghetti.
```

For a `medium-large-modular-web` project, use:

```markdown
## Role Bootloader

`AGENTS.md` instantiates the role workflow by routing each agent to the role documents it must obey:

- Validator reads `agent-relay/roles/Validator/ROLE.md` before freezing requirements, writing directives, judging Builder/Editor reports, or accepting work.
- Builder reads `agent-relay/roles/Builder/ROLE.md` before implementing any Validator directive.
- Editor reads `agent-relay/roles/Editor/ROLE.md` before reviewing, simplifying, refactoring, or marking an `EDITOR BLOCKER`.
- When one running agent is mediating the roles, it must read all three role documents before routing or simulating role handoffs.
```

```markdown
## Project Coding Paradigm

- This project is governed as `medium-large-modular-web`.
- Read `PROJECT_CODING_PARADIGM.md` before substantial feature, refactor, frontend, backend, domain, or architecture work.
- The target architecture is a modular monolith organized by product capability.
- New substantial work must name the affected product domain and stay inside the approved domain boundary.
- Do not add new global dumping grounds, parallel engines, duplicate caches, duplicate workflows, or shared abstractions without Validator approval.
- Migration is incremental. Do not reshuffle the whole repo just to match the target tree; improve touched areas toward the target boundary only when the directive authorizes it.
- Validator enforces the coding paradigm in directives, Builder implements within the named boundary, and Editor treats architecture drift as an anti-spaghetti concern.
```
