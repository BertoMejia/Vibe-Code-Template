# ARCHITECTURE_INDEX.md (Project-specific architecture map)

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
├─ mobile/                      # React Native app when required by the project
│  ├─ src/
│  │  ├─ screens/
│  │  ├─ components/
│  │  ├─ services/
│  │  └─ navigation/
│  └─ test/
├─ shared/                      # Shared types/contracts/utilities (if used)
├─ docs/
│  ├─ PROJECT.md                # User-authored project definition
│  ├─ PLAN.md                   # AI-generated project plan
│  ├─ ARCHITECTURE_INDEX.md     # Project-specific service map
│  └─ design/                   # Mockups/reference design assets
└─ .agent/
   ├─ AGENT.md                  # Runtime operating instructions
   ├─ INIT_PROMPT.md            # Minimal init prompt
   ├─ PROJECT_STATE.md          # Current progress
   ├─ architecture-rules/       # Static service-specific architecture rules
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
- Mobile API access: `mobile/src/services/apiClient`
- Shared contracts and schemas: `shared/`

## Update rule
If folder/module locations change, update this file in the same patch.
