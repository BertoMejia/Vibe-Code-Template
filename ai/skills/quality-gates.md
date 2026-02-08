# Quality Gates (simple)

Gate 1: Scope & Acceptance

- Task goal is explicit
- Acceptance criteria listed
- Non-goals noted

Gate 2: Contracts & Data

- Routes/APIs typed or documented
- Data model clarified (even if lightweight)
- Env vars updated in .env.example if needed

Gate 3: Implementation

- Minimal change for the task
- No unrelated refactors

Gate 4: Verification
Pick what fits the change and run it:

- unit tests (preferred)
- lint/typecheck
- integration test
- E2E smoke (Playwright) for user flows

Gate 5: Review

- 3-reviewer pass for non-trivial changes:
  correctness, security, maintainability

Stop rule:
If a gate fails, fix it before continuing.
