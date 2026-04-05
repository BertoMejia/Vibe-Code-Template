# Quality and TDD

Purpose: governs quality gates, execution flow, and verification for code changes.
Use for any implementation, refactor, or bug fix.

## A) Quality gates (must pass in order)

### Gate 1 — Scope clarity
- Objective is explicit.
- Acceptance criteria are testable.
- Non-goals are listed.
- Dependencies/constraints are identified.

### Gate 2 — Contract clarity
- Data model impact is identified.
- API contract impact is identified (inputs, outputs, errors).
- Affected files/modules are mapped via `docs/ARCHITECTURE_INDEX.md`.

### Gate 3 — Test design before implementation
- Tests are written/updated first.
- Failing state is observed when expected.
- Coverage includes happy path, failure path, and key edge cases.

### Gate 4 — Implementation quality
- Minimal implementation satisfies tests.
- No dead code, hidden feature flags, or placeholder logic.
- Error handling and logging are meaningful.
- Keep tests in the correct test location for the project.

### Gate 5 — Verification
Run all checks that apply:
- Unit tests for changed modules
- Integration tests for changed APIs/flows
- Lint and type checks
- E2E smoke for primary UX flow when UI changed
- Functional test
	- Run the project while developing.
	- Open the current page being built/ported.
	- Inspect terminal/browser logs and fix surfaced errors before marking progress complete.
- Build/package check if deployment artifact changed

### Gate 6 — State and docs sync
- `docs/PLAN.md` reflects both checklist status and the current task slice.
- `docs/ARCHITECTURE_INDEX.md` updated if architecture/locations changed.
- Project state file is updated if the repo uses one.
- Any new operational runbook notes are added where relevant.

Stop if any gate fails. Fix it before proceeding.

## B) Execution loop (every task slice)
1. Select the current task slice from `docs/PLAN.md` and keep its checklist/status current.
2. Define expected behavior from acceptance criteria.
3. Write failing test(s).
4. Implement minimal code change.
5. Run targeted checks, then broader relevant checks.
6. Refactor, cleanup, run linting, and fix linting problems only with tests still green.
7. Update `docs/PLAN.md` and any affected architecture/state files.

## C) Bug-fix policy
- Every bug fix must include a regression test that fails before the fix and passes after it.
- Document root cause in project state file if the repo uses one (briefly).

## D) Production-readiness checklist
For changed surfaces, verify as applicable:
- Security: authz/authn, input validation, secret handling, injection-safe queries.
- Reliability: retries/timeouts/idempotency where needed.
- Observability: logs/metrics/traces or at minimum structured logging at failure points.
- Data safety: migration strategy and rollback/forward compatibility.
- Performance: avoid obvious regressions on critical paths.
- Clean code: follow project conventions, no commented-out code, clear naming, no temporary/test files or code.

## E) Verification evidence format (for handoff)
Provide concise evidence:
- Commands run
- Pass/fail summary
- Test coverage notes for changed behavior
- Remaining known risks and follow-ups
