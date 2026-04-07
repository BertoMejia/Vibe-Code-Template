# Vibe Code Template

This is a clean operating system for agentic coding.

If you want agents to move fast **without** turning your project into a mess, this is for you.

## What this is

This template gives your agent a clear structure for:

- product requirements
- architecture and ownership
- planning
- implementation
- testing and verification

Instead of letting the agent guess, drift, or create duplicate systems, this template tells it what to read, what is authoritative, and how to execute production-ready work.

## Why you should use it

Most agent workflows fall apart for the same reasons:

- the requirements are vague
- the architecture is undocumented
- the plan lives in chat instead of files
- the agent starts coding too early
- nobody updates the docs after changes

This template fixes that.

It gives you a repeatable system that is simple enough to use quickly and strong enough to support serious production work.

## Why it works

- **[one source of truth]**
  Product requirements live in `docs/PROJECT.md`. Architecture lives in `docs/ARCHITECTURE_INDEX.md`. Execution lives in `docs/PLAN.md`.

- **[clear runtime rules]**
  `.agent/AGENT.md` tells the agent what to load, what governs the work, and what must stay up to date.

- **[planning before coding]**
  The agent has to understand the project and produce a coherent plan before implementation starts.

- **[production-ready execution]**
  `.agent/skills/quality-and-tdd.md` forces quality gates, verification, and disciplined execution.

- **[less chaos, better handoffs]**
  The docs stay current, so the next agent session does not start from scratch.

## What is in the template

### Product and project docs
- `docs/PROJECT.md` → what the product does, what it should include, and what success looks like
- `docs/ARCHITECTURE_INDEX.md` → where things live, who owns what, and where changes belong
- `docs/PLAN.md` → the current implementation plan and active task slices
- `docs/DEVELOPER_PLAYBOOK.md` → how to work with the AI effectively: issue workflow, prompt writing, review, and done criteria
- `docs/design/` → the design reference folder.

### Agent runtime files
- `.agent/AGENT.md` → load order, source of truth, execution policy, and done criteria
- `.agent/INIT_PROMPT.md` → bootstrap prompt for adapting an existing active project to this workflow
- `.agent/architecture-rules/*.md` → service-specific technical rules loaded only when relevant
- `.agent/skills/quality-and-tdd.md` → quality gates, execution loop, and verification standards

## How to use this in a brand new project

1. Copy the template's `.agent/` and `docs/` folders into your new project.
2. Fill in `docs/PROJECT.md` with the product, pages, user flows, requirements, and acceptance criteria.
3. Create or update `docs/ARCHITECTURE_INDEX.md` so it reflects the architecture you actually want.
4. Adjust `.agent/architecture-rules/*.md` only if the project needs different service rules.
5. Start your agent and tell it to read `.agent/AGENT.md` and follow it.
6. Let the agent generate `docs/PLAN.md` from `docs/PROJECT.md`, `docs/ARCHITECTURE_INDEX.md`, and the relevant architecture rules.
7. Execute work through `.agent/skills/quality-and-tdd.md` and keep `docs/PLAN.md` and `docs/ARCHITECTURE_INDEX.md` current as the project evolves.

## How to use this in an existing project

1. Copy the template's `.agent/` and `docs/` folders into the existing project.
2. Paste `.agent/INIT_PROMPT.md` into the agent session for that project.
3. Have the agent read the current docs, config, file structure, and implementation entrypoints.
4. Have the agent create or update `docs/ARCHITECTURE_INDEX.md` from the real codebase.
5. Have the agent fill in as much of `docs/PROJECT.md` as it can from actual evidence in the docs and code.
6. Have the agent report what is still missing from `docs/PROJECT.md` so you can finish the parts that require product decisions.
7. Once the project is understood and documented, move into planning and implementation through `.agent/AGENT.md`.
