# Quality and TDD

Purpose: governs quality gates, execution flow, and verification for code changes.
Use for any implementation, refactor, or bug fix.

## A. Execution loop (every task slice)

1. Select the current task slice from `docs/PLAN.md`. Confirm the objective is explicit, acceptance criteria are testable, and non-goals are listed. Identify data model and API contract impacts (inputs, outputs, errors). Map affected files/modules via `docs/ARCHITECTURE_INDEX.md`.
2. Write failing test(s). Coverage must include happy path, failure path, and all edge cases. Confirm the failing state before implementing.
3. Write the minimal implementation that satisfies the tests. No dead code, hidden feature flags, or placeholder logic. Error handling and logging must be meaningful. Keep tests in the correct test location.
4. Run unit tests for the changed code.
5. Run integration tests and E2E tests for affected flows.
6. Run linting for the impacted service(s) using the commands in `docs/ARCHITECTURE_INDEX.md`. Fix all lint errors and warnings before proceeding.
7. Run type checks (e.g., `mypy` for Python, `tsc` for TypeScript).
8. Verify documentation: all new and changed public functions, classes, methods, and modules must have proper docstrings or JSDoc comments explaining purpose, parameters, return values, and exceptions/errors.
9. Run E2E smoke tests if any UI components or routes changed.
10. If any check fails, fix and return to step 3.
11. Refactor and clean up. Re-run tests and linting; fix issues only with tests still green.
12. Run a build and watch logs for errors.
13. Run the application and test the current routes.
14. If there are errors, fix them and return to step 3.
15. Update `docs/PLAN.md` and any affected architecture/state files.
16. Mark the task slice complete and move to the next.

Stop if any step cannot be completed cleanly. Fix it before proceeding.

## B. Bug-fix policy
- Every bug fix must include a regression test that fails before the fix and passes after it.
- Document root cause in project state file if the repo uses one (briefly).

## C. Production-readiness checklist
For changed surfaces, verify as applicable:
- Security: authz/authn, input validation, secret handling, injection-safe queries.
- Reliability: retries/timeouts/idempotency where needed.
- Observability: logs/metrics/traces or at minimum structured logging at failure points.
- Data safety: migration strategy and rollback/forward compatibility.
- Performance: avoid obvious regressions on critical paths.
- Clean code: follow project conventions, no commented-out code, clear naming, no temporary/test files or code.

## D. Verification evidence format (for handoff)
Provide concise evidence:
- Commands run
- Pass/fail summary
- Test coverage notes for changed behavior
- Remaining known risks and follow-ups
