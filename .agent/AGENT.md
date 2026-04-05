# Development Rules

## 0) Required load order (always)
1. `docs/PROJECT.md` (project definition and acceptance outcomes)
2. `docs/ARCHITECTURE_INDEX.md` (project-specific architecture map)
3. `.agent/architecture-rules/shared.md` (shared architecture rules that always apply)
4. Load only the service-specific static rule files needed for the current task from `.agent/architecture-rules/`
   - Load `webapp.md` only when working on the webapp
   - Load `api.md` only when working on the API
   - Load `mobile.md` only when working on the mobile app
5. `docs/PLAN.md` (detailed AI-generated project plan, including the current task slice)
6. `.agent/skills/quality-and-tdd.md` (quality gates, execution loop, and verification)

 If `docs/PLAN.md` is empty or placeholder, generate it first from `docs/PROJECT.md` + `docs/ARCHITECTURE_INDEX.md` + `shared.md` + the relevant service-specific static rule files in `.agent/architecture-rules/` before coding.
 If required files are missing or stale, stop and request updates before implementation.

## 1) Source of truth
- `docs/PROJECT.md` defines product requirements and acceptance criteria.
- `docs/ARCHITECTURE_INDEX.md` defines ownership, boundaries, and where to implement changes.
- `docs/PLAN.md` defines the current plan, active task slice, and verification checklist.
- `.agent/architecture-rules/*.md` define default technical rules for affected services.
- If project docs conflict with `.agent/architecture-rules/*.md`, project docs win.
- Keep reusable operating rules in `.agent/` and project-specific content in `docs/`.
- Update `docs/ARCHITECTURE_INDEX.md` when ownership or locations change.
- Update `docs/PLAN.md` when scope, task slices, or verification steps change.

## 2) Operating principles
- One system only: do not create duplicate planning, architecture, or tracking systems.
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

## 4) Execution policy (required)
For every implementation, refactor, or bug-fix task slice, follow `.agent/skills/quality-and-tdd.md`.
Use `docs/PLAN.md` to select the current task slice and keep its checklist/status current.
Update `docs/ARCHITECTURE_INDEX.md` whenever service/module ownership or locations change.

Never mark a task complete unless all required verification passes.

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
- Docs/state files are updated (`docs/PLAN.md`, `docs/ARCHITECTURE_INDEX.md`).
- Known risks and follow-ups are explicitly listed.

## 8) Output discipline
At handoff, provide concise evidence:
- What changed (files + behavior)
- Commands run
- Verification results
- Remaining risks/follow-ups (if any)
