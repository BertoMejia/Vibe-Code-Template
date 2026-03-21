# AGENT.md (single source of operating instructions)

You are working in the Vibe Code Template.

## 0) Required load order (always)
1. `docs/PROJECT.md` (project definition and acceptance outcomes)
2. `docs/ARCHITECTURE_INDEX.md` (project-specific architecture map and active services)
3. Load only the relevant static rule files referenced by `docs/ARCHITECTURE_INDEX.md` from `.agent/architecture-rules/`
4. `docs/PLAN.md` (detailed AI-generated project plan)
5. `.agent/PROJECT_STATE.md` (current progress against plan)
6. `.agent/skills/testing.md` (quality gates, TDD flow, verification)

If `docs/PLAN.md` is empty or placeholder, generate it first from `docs/PROJECT.md` + `docs/ARCHITECTURE_INDEX.md` + the relevant static rule files in `.agent/architecture-rules/` before coding.
If required files are missing or stale, stop and request updates before implementation.

## 1) Project document ownership and generation rules
- `docs/PROJECT.md` is the user-authored project definition.
- `docs/ARCHITECTURE_INDEX.md` is project-specific output generated and maintained from `docs/PROJECT.md`.
- `docs/PLAN.md` is project-specific output generated from `docs/PROJECT.md` + `docs/ARCHITECTURE_INDEX.md` + the relevant files in `.agent/architecture-rules/`.
- `.agent/PROJECT_STATE.md` is runtime execution state derived from the current plan and implementation progress.
- `.agent/AGENT.md`, `.agent/skills/testing.md`, and `.agent/architecture-rules/*.md` are static operating files and should not become project-specific.
- Keep procedural instructions in `.agent/`, not in `docs/`.
- Keep `docs/PROJECT.md`, `docs/ARCHITECTURE_INDEX.md`, and `docs/PLAN.md` focused on project content only.
- `docs/PROJECT.md` should describe the product, user flows, pages, and requirements.
- `docs/ARCHITECTURE_INDEX.md` should describe active services, ownership, and repo structure for the current project.
- `docs/PLAN.md` should contain only the current project plan and execution checklist.
- Update `docs/ARCHITECTURE_INDEX.md` when service ownership, folder structure, or active services change.
- Update `docs/PLAN.md` when milestones, task slices, or verification steps change.
- Read project files only when needed for the current task, but always respect the required load order above.

## 2) Operating principles
- One system only: do not create duplicate planning/state systems.
- Keep static agent instructions in `.agent/`; keep project-specific definitions, plans, and architecture files in `docs/`.
- Keep changes minimal, scoped, and reversible.
- Prefer explicit contracts over assumptions.
- Build for production quality: correctness, security, observability, maintainability.

## 3) Plan-before-code (required)
Before implementation, output:
1. Assumptions and blockers (only if needed)
2. Impacted repository tree
3. Data model / schema impact
4. API contract changes (inputs, outputs, errors)
5. Step-by-step implementation checklist mapped to tests

Do not start coding until this plan is coherent and testable.

## 4) TDD-first loop (required)
For each smallest task slice:
1) Update the relevant checklist item in `docs/PLAN.md`
2) Add or update failing test(s) first
3) Implement minimal code to make tests pass
4) Run required verification from `.agent/skills/testing.md`
5) Refactor safely with tests still green
6) Update `.agent/PROJECT_STATE.md`
7) Update `docs/ARCHITECTURE_INDEX.md` if service/module ownership or locations changed

Never mark a task complete unless verification passes.

## 5) Anti-stuck execution rules
- Try up to 3 viable implementation/debug paths before declaring blocked.
- If blocked, report:
  - exact blocker,
  - evidence (error output/failed check),
  - options with tradeoffs,
  - recommended next action.
- Ask for clarification only when it materially changes architecture, scope, security, or paid-service usage.
- Never silently skip requirements.

## 6) Change control and safety
- No architecture or behavior changes outside approved scope.
- No temporary hacks, fake implementations, or hidden TODO debt.
- No dummy data in production paths unless explicitly allowed.
- Ask before introducing paid services, external integrations, secrets, or migrations with irreversible effects.
- Validate input/output boundaries and error handling for every changed endpoint/flow.

## 7) Definition of done
A task is done only when all are true:
- Acceptance criteria are satisfied.
- Tests cover success, failure, and edge cases for changed behavior.
- Lint/type/test checks pass for impacted areas.
- Logging/error messages are actionable.
- Docs/state files are updated (`docs/PLAN.md`, `.agent/PROJECT_STATE.md`, `docs/ARCHITECTURE_INDEX.md`).
- Known risks and follow-ups are explicitly listed.

## 8) Output discipline
At handoff, provide concise evidence:
- What changed (files + behavior)
- Commands run
- Verification results
- Remaining risks/follow-ups (if any)
