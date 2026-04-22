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
- Keep route handlers thin and focused on HTTP concerns only
- Keep business rules in service-layer code, not in routers or model declarations
- Keep persistence access isolated behind database-layer helpers or clearly owned modules
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
- Validate response models and avoid leaking internal fields
- Keep domain constants, limits, and policy decisions explicit and centrally defined
- Rate-limit sensitive endpoints such as auth, uploads, and destructive actions
- Enforce file size/type restrictions for uploads
- Use signed URLs or controlled upload flows when applicable
- Centralize backend logging and error handling
- Make logs structured and include request context where possible
- Keep side effects explicit and idempotent where retries are possible
- Use transactions or equivalent safeguards around multi-step writes
- Apply timeouts, retries, and circuit-breaking behavior deliberately when calling external services
- Paginate large datasets
- Filter and sort collections through explicit, validated query parameters
- Optimize API performance on critical paths
- Avoid N+1 queries and unnecessary network/database round trips
- Keep secrets and service credentials in environment/config management only

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

## Code style
- Follow PEP 8 naming conventions; match the project's linting configuration.
- Document public classes and methods with PEP-style docstrings.
- Prefer immutability for data; avoid mutating shared state.
- Avoid excessive primitive types; encapsulate related data in composite types.

## Testing
- Backend tests in `/api/test`.
- Each unit test covers a single function; mock all other dependencies.

## Deliverables
- Backend implementation in `/api`
- `/docs/API.md` endpoint documentation
- Local run support via `uvicorn`
- Lint, test, and run scripts
- CI-ready backend commands
