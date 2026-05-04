# PlanTestShip

**Plan it. Test it. Ship it.**

PlanTestShip is a structured development workflow for AI-assisted coding.

It helps developers and vibe coders use AI agents to move fast without letting the codebase turn into a mess.

Instead of asking an agent to “just build it,” PlanTestShip gives you a repeatable system:

> - Plan the work
> - Write a clear prompt
> - Map the architecture
> - Test the behavior
> - Build the change
> - Review the code
> - Verify manually
> - Ship a focused PR
> - Repeat

AI coding is fast. PlanTestShip makes it disciplined.

---

## Why PlanTestShip exists

AI coding agents can generate code quickly, but speed alone is not enough.

Without structure, AI-assisted development usually breaks down because:

* requirements are vague
* prompts are too broad
* architecture is undocumented
* plans live in chat instead of files
* agents start coding too early
* tests are skipped or written too late
* PRs get too large
* docs go stale
* every new agent session starts from scratch

PlanTestShip fixes that.

It gives both the developer and the AI agent a clear workflow for planning, testing, reviewing, verifying, and shipping production-ready code.

---

## What PlanTestShip does

PlanTestShip gives your project a lightweight operating system for AI-assisted development.

It helps your agent understand:

* what the product should do
* where things belong in the architecture
* what plan it should follow
* what tests it should write
* what quality gates must pass
* what docs must stay updated
* when a task is actually done

It also helps the developer stay efficient by giving them a clear playbook for:

* keeping issues small
* writing better prompts
* working one focused task at a time
* reviewing AI-generated code
* manually verifying changes
* opening clean PRs
* merging quickly

The result is simple:

**You keep the speed of AI coding, but add the discipline of a real development process.**

---

## Who this is for

PlanTestShip is for:

* developers using AI coding agents
* vibe coders who want better structure
* founders building MVPs with AI
* small teams shipping fast
* engineers who want AI speed without AI chaos
* anyone tired of agents creating messy, untested, hard-to-review code

It works especially well for:

* new products
* existing codebases
* full-stack apps
* web apps
* APIs
* mobile apps
* monorepos
* small teams using AI to move faster

---

## The core idea

Most AI coding workflows ask the agent to do too much with too little structure.

PlanTestShip changes the workflow from this:

```text
Prompt → Code → Hope it works
```

To this:

```text
Plan → Test → Build → Review → Verify → Ship
```

That small change makes a big difference.

The agent gets clearer instructions.
The developer gets better output.
The codebase stays easier to understand.
The next task starts with more context, not less.

---

## Why it works

### 1. One source of truth

Product requirements live in `docs/PROJECT.md`.

Architecture and ownership live in `docs/ARCHITECTURE_INDEX.md`.

Execution plans live in `docs/PLAN.md`.

The agent is told what is authoritative, what to read first, and what must stay updated.

---

### 2. Plan before code

Before implementation, the agent must understand the project and produce a clear plan.

That plan should include:

* assumptions and blockers
* impacted files and modules
* data model or schema impact
* API contract changes
* a step-by-step implementation checklist mapped to tests

This keeps the agent from guessing, drifting, or coding too early.

---

### 3. Test-first execution

PlanTestShip includes a quality and TDD workflow that pushes the agent to:

* select a small task slice
* write failing tests
* implement the minimum code needed
* run verification checks
* fix failures
* refactor only after tests pass
* update the plan and architecture docs

The goal is not just to generate code.

The goal is to generate code that can be trusted.

---

### 4. A real developer playbook

The AI agent needs structure, but so does the developer.

PlanTestShip includes a developer playbook that helps you work efficiently with AI:

* work on one issue at a time
* keep one active PR at a time
* keep issues small enough to finish in one focused work session
* write short, specific prompts
* review the AI’s work carefully
* manually verify the app, flow, or endpoint
* keep PRs small and easy to review
* merge quickly once approved

The system does not replace the developer.

It makes the developer more effective.

---

### 5. Better handoffs between sessions

AI coding sessions lose momentum when the context only exists in chat.

PlanTestShip keeps important project state in files, so every new session can quickly understand:

* what the product is
* how the architecture works
* what the current plan is
* what task is active
* what has already been verified
* what still needs to happen

That means less re-explaining and more shipping.

---

## What is included

### Project docs

* `docs/PROJECT.md`
  Defines what the product does, what it should include, user flows, requirements, and acceptance criteria.

* `docs/ARCHITECTURE_INDEX.md`
  Defines where things live, who owns what, and where changes belong.

* `docs/PLAN.md`
  Tracks the current implementation plan, active task slices, and verification checklist.

* `docs/DEVELOPER_PLAYBOOK.md`
  Gives the human developer a practical workflow for using AI effectively, including issue selection, prompt writing, review, manual verification, PR flow, and done criteria.

* `docs/design/`
  A place to store design references, screenshots, flows, mockups, and visual context.

---

### Agent runtime files

* `.agent/AGENT.md`
  Defines the agent load order, source-of-truth rules, execution policy, change control, and definition of done.

* `.agent/INIT_PROMPT.md`
  A bootstrap prompt for adapting an existing active project to the PlanTestShip workflow.

* `.agent/architecture-rules/*.md`
  Service-specific architecture rules loaded only when relevant.

* `.agent/skills/quality-and-tdd.md`
  Defines the quality gates, test-first execution loop, verification standards, and handoff format.

---

## Quick start

### Use PlanTestShip in a new project

1. Copy the `.agent/` and `docs/` folders into your new project.
2. Fill in `docs/PROJECT.md` with the product, pages, user flows, requirements, and acceptance criteria.
3. Create or update `docs/ARCHITECTURE_INDEX.md` so it reflects the architecture you want.
4. Adjust `.agent/architecture-rules/*.md` only if your project needs different service rules.
5. Start your AI coding agent.
6. Tell it to read `.agent/AGENT.md` and follow PlanTestShip.
7. Let the agent generate `docs/PLAN.md` from:

   * `docs/PROJECT.md`
   * `docs/ARCHITECTURE_INDEX.md`
   * relevant architecture rules
8. Execute work through `.agent/skills/quality-and-tdd.md`.
9. Keep `docs/PLAN.md` and `docs/ARCHITECTURE_INDEX.md` current as the project evolves.

---

### Use PlanTestShip in an existing project

1. Copy the `.agent/` and `docs/` folders into the existing project.
2. Paste `.agent/INIT_PROMPT.md` into your agent session.
3. Have the agent read the current docs, config, file structure, and implementation entrypoints.
4. Have the agent create or update `docs/ARCHITECTURE_INDEX.md` from the real codebase.
5. Have the agent fill in as much of `docs/PROJECT.md` as it can from actual evidence.
6. Have the agent report what is still missing from `docs/PROJECT.md`.
7. Finish the product decisions that require human judgment.
8. Move into planning and implementation through `.agent/AGENT.md`.

---

## Recommended developer workflow

PlanTestShip works best when you keep the work small and focused.

### 1. Pick one issue

Choose an issue that:

* has a clear outcome
* can be completed in one focused work session
* does not overlap heavily with someone else’s work
* can become a small, reviewable PR

If the issue is too large, break it down first.

---

### 2. Write a clear prompt

Your prompt should be short, specific, and scoped.

Use this structure:

```text
Read and follow `.agent/AGENT.md`.

Task:
[Say what needs to be built or fixed in 1 to 3 short sentences.]

Focus areas:
- [file, folder, component, endpoint, or service]
- [file, folder, component, endpoint, or service]

Requirements:
- [requirement]
- [requirement]
- [Do not change X, Y, or Z]

Edge cases:
Please consider any other edge cases that might be relevant and add them to the list.
- [edge case]
- [edge case]
```

You do not need to explain the full workflow every time.
PlanTestShip already gives the agent the process.

Your job is to give it a clear task.

---

### 3. Let the agent plan before coding

The agent should read the required docs, inspect the relevant files, identify the impacted areas, and produce a testable plan before implementation starts.

Do not skip this step.

A good plan prevents messy code.

---

### 4. Review the code

Do not blindly trust AI-generated code.

Review for:

* correctness
* clean architecture
* edge cases
* logging
* error handling
* security issues
* unnecessary complexity
* unrelated changes
* consistency with existing patterns

If the output is weak, improve the prompt and run the agent again.

---

### 5. Manually verify the change

Passing tests are not enough.

You should still:

* run the app, page, flow, or endpoint yourself
* inspect the real behavior
* check logs when relevant
* confirm the user experience makes sense
* test important edge cases manually

---

### 6. Ship a focused PR

Open a PR when:

* the issue is solved
* tests pass
* you reviewed the code
* you manually verified the change
* the branch is up to date
* the PR is small and focused

Good target:

* one issue per PR
* under 300 lines changed when possible
* fast review
* fast merge

---

## Example prompt

```text
Read and follow `.agent/AGENT.md`.

Task:
Fix signup so users see a clear message when an email is already in use.

Focus areas:
- `SignupForm.tsx`
- `authController.ts`
- `authService.ts`

Requirements:
- Return a clean backend error for duplicate email
- Show a friendly message in the UI
- Keep the existing signup flow unchanged otherwise
- Do not change the success path for signup

Edge cases:
Please consider any other edge cases that might be relevant and add them to the list.
- Email casing differences
- Unexpected server failure
```

---

## Definition of done

A task is not done just because the agent wrote code.

A task is done when:

* the AI followed the PlanTestShip workflow
* the acceptance criteria are satisfied
* tests cover the changed behavior
* verification checks pass
* the developer reviewed the code
* the change was manually verified
* logging, error handling, architecture, and efficiency are solid
* docs and plan files are updated
* the PR is approved and merged

---

## The promise

PlanTestShip helps you move from chaotic AI coding to structured AI-assisted development.

You still get the speed.

But now the agent has:

* context
* constraints
* a plan
* tests
* quality gates
* documentation discipline

And the developer has:

* a repeatable workflow
* better prompts
* smaller issues
* cleaner reviews
* faster PRs
* more confidence in what ships

---

## Use this if you want to

* stop agents from guessing
* stop plans from getting lost in chat
* stop docs from going stale
* stop PRs from getting too big
* stop AI-generated code from skipping tests
* make every coding session easier to continue
* ship faster without losing control of the codebase

---

## Bottom line

PlanTestShip gives AI the system.
You give AI the task.

Keep the work small.
Make the prompt clear.
Plan before coding.
Test before trusting.
Review before merging.
Ship with confidence.

---

## License

MIT
