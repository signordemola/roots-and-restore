<!-- BEGIN:nextjs-agent-rules -->
# This is NOT the Next.js you know

This version has breaking changes — APIs, conventions, and file structure may all differ from your training data. Read the relevant guide in `node_modules/next/dist/docs/` before writing any code. Heed deprecation notices.
<!-- END:nextjs-agent-rules -->

<!-- playbook:start -->
# Project Instructions for AI Agents

## Core Principles — apply to EVERY change

1. **Single Source of Truth** — one function per business rule, defined once, called from everywhere.
2. **Database as Safety Net** — application logic validates first, DB constraints are the final defence.
3. **Never Trust the Client** — re-validate all inputs server-side; authenticate and authorize all mutations.
4. **Audit Everything** — every state transition, charge, and permission change gets logged. Append-only.
5. **Idempotency by Default** — every external side effect uses a business-derived idempotency key.
6. **Money Is Integer Minor Units** — never floats; the currency travels with every amount; rounding happens once, in one named function.

## Required Reading, in Order

1. `.playbook/rules/`: `code-style.md`, `project-structure.md`, `mistakes.md`, `definition-of-done.md`, `git-workflow.md` (the global rules are already loaded)
2. `CONTEXT.md` at the project root, if it exists — the domain glossary; use its exact terms in all naming
3. `DESIGN.md` at the project root, if it exists — the design lock; read it before any UI work
4. `.playbook/stacks/nextjs/STACK.md` — stack conventions, templates, and check commands
5. `.playbook/playbooks/<domain>/INDEX.md` — for the relevant domain (e.g. `booking`, `core`)

## Workflows

`.playbook/workflows/flow.md` maps the available workflows (installed as slash commands) — consult it when unsure how to proceed.

## Completion Gate

A task is complete ONLY when `.playbook/rules/definition-of-done.md` passes.
<!-- playbook:end -->
