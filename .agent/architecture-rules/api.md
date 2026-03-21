# api.md

Load this file only when the project includes an API or backend service.

## Technology stack
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

## API goals
- Production-ready MVP suitable for real users
- Backend is the source of truth for business logic
- Validate and authorize every request boundary

## Backend rules
- Python + FastAPI with strict modular structure
- Per route module:
  - `router.py` for routes only
  - `service.py` for business logic
  - `models.py` for Pydantic request/response models
  - `constants.py` for messages/constants
- Shared logic in `/api/core`:
  - authentication
  - database client
  - storage client
  - logging
  - configuration
  - error handling
- If shared logic needs multiple files, use a folder with `service.py`, `models.py`, `constants.py`
- Always check `/api/core` before writing new shared logic
- Version endpoints under `/api/v1`
- Use a consistent error schema: `{ error: { code, message, details } }`
- Validate and sanitize all input
- Rate-limit sensitive endpoints such as auth, uploads, and destructive actions
- Enforce file size/type restrictions for uploads
- Use signed URLs or controlled upload flows when applicable
- Centralize backend logging and error handling
- Paginate large datasets
- Optimize API performance on critical paths

## Authentication and authorization
- Frontend sends `Authorization: Bearer <token>` on every API request
- Backend verifies tokens and derives identity from claims
- Backend enforces all authorization rules
- Never trust the client
- Log and monitor auth/authz failures

## Storage layout
- `/images/<entity-type>/<entity-id>/<file>.png`
- `/videos/<entity-type>/<entity-id>/<file>.mp4`
- [insert special hierarchy here]

## Testing locations
- Backend tests in `/api/test`

## Deliverables
- Backend implementation in `/api`
- `/docs/API.md` endpoint documentation
- Local run support via `uvicorn`
- Lint, test, and run scripts
- CI-ready backend commands
