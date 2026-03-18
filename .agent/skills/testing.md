# testing.md (single process file)

This is the only process file for quality gates, TDD flow, and verification standards.

## A) Quality gates (must pass in order)

### Gate 1 — Scope clarity
- Objective is explicit.
- Acceptance criteria are testable.
- Non-goals are listed.
- Dependencies/constraints are identified.

### Gate 2 — Contract clarity
- Data model impact is identified.
- API contract impact is identified (inputs, outputs, errors).
- Affected files/modules are mapped via `.agent/SERVICE_INDEX.md`.

### Gate 3 — Test design before implementation
- Tests are written/updated first.
- Failing state is observed when expected.
- Coverage includes happy path, failure path, and key edge cases.

### Gate 4 — Implementation quality
- Minimal implementation satisfies tests.
- No dead code, hidden feature flags, or placeholder logic.
- Error handling and logging are meaningful.

### Gate 5 — Verification
Run what applies, but do run required checks:
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
- `.agent/PROJECT_STATE.md` reflects progress and next step.
- `.agent/PLAN.md` checklist reflects done/pending status.
- `.agent/SERVICE_INDEX.md` updated if architecture/locations changed.
- Any new operational runbook notes are added where relevant.

Stop rule: if any gate fails, fix before proceeding.

## B) Standard TDD loop (every task slice)
1. Select the smallest slice from `.agent/PLAN.md`.
2. Define expected behavior from acceptance criteria.
3. Write failing test(s).
4. Implement minimal code change.
5. Run targeted checks, then broader relevant checks.
6. Refactor only with tests still green.
7. Update state files.

## C) Bug-fix policy
- Every bug fix must include a regression test that fails before the fix and passes after it.
- Document root cause in `.agent/PROJECT_STATE.md` (briefly).

## D) Production-readiness checklist
For changed surfaces, verify as applicable:
- Security: authz/authn, input validation, secret handling, injection-safe queries.
- Reliability: retries/timeouts/idempotency where needed.
- Observability: logs/metrics/traces or at minimum structured logging at failure points.
- Data safety: migration strategy and rollback/forward compatibility.
- Performance: avoid obvious regressions on critical paths.

## E) Verification evidence format (for handoff)
Provide concise evidence:
- Commands run
- Pass/fail summary
- Test coverage notes for changed behavior
- Remaining known risks and follow-ups
