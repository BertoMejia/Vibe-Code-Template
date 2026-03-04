# Vibe Code Template (Unified, Minimal, User-Friendly)

This template gives one clean workflow for agentic coding.

## Folder choice / best practice
- Uses `.agent/` for agent runtime files.
- Why: hidden, tool-friendly, and aligned with Claude-style naming (`CLAUDE.md` + `.agent` ecosystem conventions).
- Keeps agent mechanics separate from product code and avoids `ai/` naming collisions in app projects.

## Single unified system

### Product + technical source files
- `docs/PROJECT.md` → project description and acceptance outcomes
- `docs/ARCHITECTURE.md` → technical stack, rules, constraints

### Agent runtime files
- `.agent/AGENT.md` → master instructions and load order
- `.agent/INIT_PROMPT.md` → tiny init prompt users paste directly
- `.agent/PLAN.md` → detailed AI-generated project plan
- `.agent/PROJECT_STATE.md` → live progress against plan
- `.agent/SERVICE_INDEX.md` → architecture/location tree
- `.agent/skills/testing.md` → all gates/TDD/verification guidance

## Default workflow
1. Paste `.agent/INIT_PROMPT.md`
2. Agent reads `.agent/AGENT.md`
3. Agent follows required load order
4. Planning first, then TDD execution
5. Keep PLAN + PROJECT_STATE + SERVICE_INDEX updated continuously

## Notes
- `docs/design/` is the design reference folder.
- No duplicate planning systems.
- No commit automation implied; review-first workflow supported.
