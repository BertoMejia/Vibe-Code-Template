# Vibe Code Template (Unified, Minimal, User-Friendly)

This template gives one clean workflow for agentic coding.

## Folder choice / best practice
- Uses `.agent/` for static agent runtime files.
- Why: hidden, tool-friendly, and aligned with Claude-style naming (`CLAUDE.md` + `.agent` ecosystem conventions).
- Keeps agent mechanics separate from product code and avoids `ai/` naming collisions in app projects.
- Keeps project-specific planning and architecture index files in `docs/`.

## Single unified system

### Product + technical source files
- `docs/PROJECT.md` → project description and acceptance outcomes
- `docs/ARCHITECTURE_INDEX.md` → project-specific architecture map and active services
- `docs/PLAN.md` → detailed AI-generated project plan

### Agent runtime files
- `.agent/AGENT.md` → master instructions and load order
- `.agent/INIT_PROMPT.md` → tiny init prompt users paste directly
- `.agent/PROJECT_STATE.md` → live progress against plan
- `.agent/architecture-rules/*.md` → static service-specific architecture rules loaded only when needed
- `.agent/skills/testing.md` → all gates/TDD/verification guidance

## Default workflow
1. Paste `.agent/INIT_PROMPT.md`
2. Agent reads `.agent/AGENT.md`
3. Agent reads `docs/PROJECT.md` and `docs/ARCHITECTURE_INDEX.md`
4. Agent loads only the relevant `.agent/architecture-rules/*.md` files
5. Planning first, then TDD execution
6. Keep `docs/PLAN.md`, `.agent/PROJECT_STATE.md`, and `docs/ARCHITECTURE_INDEX.md` updated continuously

## Notes
- `docs/design/` is the design reference folder.
- No duplicate planning systems.
- No commit automation implied; review-first workflow supported.
