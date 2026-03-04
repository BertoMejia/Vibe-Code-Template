# ARCHITECTURE.md (Technical Stack + Constraints)

## Technology stack
### Webapp
- Next.js (App Router)
- TypeScript
- Tailwind CSS
- Radix UI (unstyled components)
- NextAuth.js (frontend auth orchestration only)
- TanStack Query (server state)
- New Relic (monitoring + error tracking)

### Backend
- Python
- FastAPI
- Supabase Auth (token verification only on backend)
- Supabase Database
- Supabase monitoring and error tracking
- Backblaze B2 Storage (for images/videos)
- Stripe (payments)
- Ollama (text generation) [insert model here]
- ComfyUI (image generation) [insert model/pipeline here]
- [insert any additional services here]

## Design references
- Use `docs/design/homepage_mockup.html` if present
- Use `docs/design/homepage_mockup.png` if present
- If missing, create a clean, modern layout matching PROJECT.md sections

## Project goals
- Production-ready MVP suitable for real users
- All business logic lives in the backend
- Frontend is a thin client that renders UI and calls backend APIs

## Required output order (when implementing)
1. Assumptions and blocking questions (only if required)
2. Repository tree
3. Data model (tables/collections + indexes)
4. API contract (endpoints + request/response models)
5. Implementation plan (checklist)
6. Code
7. Tests
8. Documentation

## Rules and constraints
- Always use DRY, fail-fast principles, and security best practices
- NEVER make architectural or functionality changes without asking
- NEVER create temporary fixes or workarounds; solutions must be production-ready
- Do not create dummy or seed data unless explicitly allowed
- If data is required to display UI, ask user to create it and provide exact instructions/API calls
- If API keys, OAuth credentials, environment vars, or provider config are required, ask before proceeding
- Keep secrets out of source control; provide `.env.example` files only
- Add all secrets/base paths/etc. to `.env` in root of each app

## Repository structure (monorepo)
- `/webapp`
- `/api`
- `/shared`
- `/docs`

## Testing locations
- Frontend tests in `/webapp/test`
- Backend tests in `/api/test`

## Frontend rules
- Use TypeScript everywhere
- Use Next.js App Router
- Default to Server Components
- Use Client Components only when required (forms, interactivity, auth state)
- All data fetching goes through backend API
- No direct access to anything other than backend API
- Use unstyled Radix UI components only
- Tailwind handles all styling
- Use a single layout template with Header, Footer, Navigation, Toasts/alerts, Error boundary
- Pages can disable specific layout elements via config/props
- Use one service per responsibility: API client, Auth, Logging

## Backend rules
- Python + FastAPI with strict modular structure
- Per route module:
  - `router.py` (routes only)
  - `service.py` (business logic)
  - `models.py` (Pydantic request/response models)
  - `constants.py` (messages/constants)
- Shared logic in `/api/core`:
  - authentication
  - database client
  - storage client
  - logging
  - configuration
  - error handling
- If shared logic needs multiple files, use folder with `service.py`, `models.py`, `constants.py`
- Always check `/core` before writing new shared logic

## Authentication and authorization
- Frontend authenticates via NextAuth.js
- Frontend sends provider ID token on every API request:
  - `Authorization: Bearer <token>`
- Backend verifies tokens and derives identity from claims
- Backend enforces all authorization rules
- Frontend handles:
  - 401 → force logout
  - 403 → permission error

## API standards
- Version endpoints under `/api/v1`
- Consistent error schema:
  - `{ error: { code, message, details } }`
- Backend validates and sanitizes all input
- Rate-limit sensitive endpoints (auth, uploads, destructive actions)

## Storage rules
- Enforce file size/type restrictions
- Use signed URLs or controlled upload flows when applicable

## Storage layout (if using object storage)
- `/images/<entity-type>/<entity-id>/<file>.png`
- `/videos/<entity-type>/<entity-id>/<file>.mp4`
- [insert special hierarchy here]

## Build and deliverables
- Full monorepo code
- `/docs/SETUP.md` local setup instructions
- `/docs/API.md` endpoint documentation
- `/docs/ARCHITECTURE.md` design decisions
- Local run support:
  - Frontend via Next.js dev server
  - Backend via uvicorn
- Scripts: `lint`, `test`, `run`
- Include CI-ready commands
- Include linting setup and comply with it

## Edge cases and error handling
- Loading, empty, and error states for all pages
- Token expiration + automatic re-auth
- Permission errors with actionable messages
- Centralized backend and frontend logging

## Performance requirements
- Avoid unnecessary re-renders
- Paginate large datasets
- Optimize API calls and caching
- Keep bundle size reasonable

## Security requirements
- Never trust the client
- Backend is source of truth
- Log and monitor auth/authz failures
- [insert special compliance/policy constraints here]

## Optional seed data (only if explicitly allowed)
If seed data is explicitly allowed:
- Generate metadata objects (slug + description) required for UI
- Provide script to generate/import assets into deterministic storage paths
- [insert seed/data rules here]
