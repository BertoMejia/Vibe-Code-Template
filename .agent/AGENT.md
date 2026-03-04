# AGENT.md (single source of operating instructions)

You are working in the Vibe Code Template.

## 0) Required load order (always)
1. `docs/PROJECT.md` (project definition and acceptance outcomes)
2. `docs/ARCHITECTURE.md` (technical architecture + constraints)
3. `.agent/SERVICE_INDEX.md` (where each service/module lives)
4. `.agent/PLAN.md` (detailed project plan)
5. `.agent/PROJECT_STATE.md` (current progress against plan)
6. `.agent/skills/testing.md` (quality gates, TDD flow, verification)

If `.agent/PLAN.md` is empty or placeholder, generate it first from PROJECT + ARCHITECTURE before coding.
If required files are missing or stale, stop and request updates before implementation.

## 1) Operating principles
- One system only: do not create duplicate planning/state systems.
- Keep changes minimal, scoped, and reversible.
- Prefer explicit contracts over assumptions.
- Build for production quality: correctness, security, observability, maintainability.

## 2) Plan-before-code (required)
Before implementation, output:
1. Assumptions and blockers (only if needed)
2. Impacted repository tree
3. Data model / schema impact
4. API contract changes (inputs, outputs, errors)
5. Step-by-step implementation checklist mapped to tests

Do not start coding until this plan is coherent and testable.

## 3) TDD-first loop (required)
For each smallest task slice:
1) Update the relevant checklist item in `.agent/PLAN.md`
2) Add or update failing test(s) first
3) Implement minimal code to make tests pass
4) Run required verification from `.agent/skills/testing.md`
5) Refactor safely with tests still green
6) Update `.agent/PROJECT_STATE.md`
7) Update `.agent/SERVICE_INDEX.md` if modules/locations changed

Never mark a task complete unless verification passes.

## 4) Anti-stuck execution rules
- Try up to 3 viable implementation/debug paths before declaring blocked.
- If blocked, report:
  - exact blocker,
  - evidence (error output/failed check),
  - options with tradeoffs,
  - recommended next action.
- Ask for clarification only when it materially changes architecture, scope, security, or paid-service usage.
- Never silently skip requirements.

## 5) Change control and safety
- No architecture or behavior changes outside approved scope.
- No temporary hacks, fake implementations, or hidden TODO debt.
- No dummy data in production paths unless explicitly allowed.
- Ask before introducing paid services, external integrations, secrets, or migrations with irreversible effects.
- Validate input/output boundaries and error handling for every changed endpoint/flow.

## 6) Definition of done
A task is done only when all are true:
- Acceptance criteria are satisfied.
- Tests cover success, failure, and edge cases for changed behavior.
- Lint/type/test checks pass for impacted areas.
- Logging/error messages are actionable.
- Docs/state files are updated (`PLAN`, `PROJECT_STATE`, `SERVICE_INDEX`).
- Known risks and follow-ups are explicitly listed.

## 7) Output discipline
At handoff, provide concise evidence:
- What changed (files + behavior)
- Commands run
- Verification results
- Remaining risks/follow-ups (if any)
