# SERVICE_INDEX.md (Where everything lives)

Purpose: architecture map + location index so agents know where to implement changes.

## Canonical repo tree

```text
.
├─ webapp/                      # Next.js app (UI + frontend orchestration only)
│  ├─ app/                      # Routes/pages/layouts
│  ├─ components/               # Reusable UI components
│  ├─ services/                 # apiClient, authClient, loggingClient
│  └─ test/                     # Frontend tests
├─ api/                         # FastAPI backend (business logic source of truth)
│  ├─ routes/
│  │  └─ <feature>/
│  │     ├─ router.py
│  │     ├─ service.py
│  │     ├─ models.py
│  │     └─ constants.py
│  ├─ core/
│  │  ├─ authentication/        # token verification + identity extraction
│  │  ├─ database/              # DB client/access helpers
│  │  ├─ storage/               # object storage helpers
│  │  ├─ logging/               # centralized logging
│  │  ├─ config/                # environment/config loading
│  │  └─ errors/                # shared error handling/schema
│  └─ test/                     # Backend tests
├─ shared/                      # Shared types/contracts/utilities (if used)
├─ docs/
│  ├─ PROJECT.md                # Project definition and outcomes
│  ├─ ARCHITECTURE.md           # Technical architecture/rules
│  └─ design/                   # Mockups/reference design assets
└─ .agent/
   ├─ AGENT.md                  # Runtime operating instructions
   ├─ INIT_PROMPT.md            # Minimal init prompt
   ├─ PLAN.md                   # Detailed project plan
   ├─ PROJECT_STATE.md          # Current progress
   ├─ SERVICE_INDEX.md          # This file
   └─ skills/
      └─ testing.md             # Gates + TDD + verification workflow
```

## Service ownership map
- Frontend API access: `webapp/services/apiClient`
- Frontend auth orchestration: `webapp/services/authClient`
- Frontend logging: `webapp/services/loggingClient`
- Backend auth verification: `api/core/authentication`
- Backend DB layer: `api/core/database`
- Backend storage layer: `api/core/storage`
- Backend logging: `api/core/logging`
- Backend configuration: `api/core/config`
- Backend shared error schema: `api/core/errors`

## Update rule
If folder/module locations change, update this file in the same PR/patch.
