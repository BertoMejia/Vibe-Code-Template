# Portable Agent Template (Loki-lite)

This repo template is designed so you can switch between IDEs (Windsurf, VS Code, Antigravity, Zed, Claude Code, Gemini CLI, Codex CLI) without rewriting your prompt.

## Core files
- docs/PROMPT.md: The master build prompt (your format)
- docs/ARCHITECTURE.md: Architecture + requirements (keep updated)
- ai/PROJECT_STATE.md: Current phase, goal, and next tasks
- ai/skills/: Quality gates, testing, troubleshooting, and artifacts

## How to start a new project
1) Edit docs/PROMPT.md:
   - Replace all [insert ... here] placeholders with your project details.
2) Edit docs/ARCHITECTURE.md:
   - Fill in roles, routes, domain model, API boundaries, and testing strategy.
3) Edit ai/PROJECT_STATE.md:
   - Set Phase 1 goal and next 3–7 tasks.
4) Add design references to /design if you have them.

## IDE usage

### Windsurf
- Open repo in Windsurf.
- `.windsurfrules` is applied automatically.
- Start by asking: “Read docs/PROMPT.md and docs/ARCHITECTURE.md. Output the required planning sections only.”

### VS Code (Copilot)
- Copilot uses `.github/copilot-instructions.md`.
- In Copilot chat, start with:
  “Read docs/PROMPT.md and docs/ARCHITECTURE.md. Produce items 1–5 from Output requirements. Stop.”

### Antigravity
Antigravity does not reliably auto-load repo rules, so do this:
1) First message of each session:
   “Read docs/PROMPT.md, docs/ARCHITECTURE.md, and ai/skills/00-index.md. Follow the gates and output format.”
2) Run Phase 1 (planning output only).
3) Implement in small slices, verifying each slice.

### Zed
- Zed applies `.rules`.
- Start prompt:
  “Follow the repo rules. Read docs/PROMPT.md and docs/ARCHITECTURE.md. Produce planning output only.”

### Claude Code
- Claude Code automatically reads CLAUDE.md.
- Start in terminal:
  “Read docs/PROMPT.md. Produce items 1–5 only. Stop for confirmation before writing code.”

### Gemini CLI
- Gemini CLI uses GEMINI.md.
- Start command:
  “Read docs/PROMPT.md and docs/ARCHITECTURE.md. Produce items 1–5 only and update docs/ARCHITECTURE.md if missing fields.”

### Codex CLI / other terminal agents
- Always start by explicitly pointing at the files:
  “Read docs/PROMPT.md and docs/ARCHITECTURE.md. Follow ai/skills/quality-gates.md. Do planning only first.”
