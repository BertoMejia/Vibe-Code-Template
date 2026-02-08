# Architecture and Requirements

## Product summary
- Example: This app provides a guided workflow to create, manage, and share user-generated content.
- Example: The MVP is production-ready and designed for real users.
- [insert summary here]
- [insert primary user value here]

## Roles and permissions
- Example: Guest can browse public content and begin a flow.
- Example: Authenticated user can create, save, and manage private content.
- [insert roles here]
- [insert permissions matrix here]

## Pages and navigation
- Example: Public pages include Home, Pricing, About, Contact, Legal.
- Example: Authenticated pages include Dashboard, Library, Create, Settings.
- [insert full route list here]
- [insert menu structure here]

## Core domain model
- Example: Users own entities; entities have metadata and media assets.
- Example: Every entity enforces ownership and authorization server-side.
- [insert entities + fields here]
- [insert indexes/constraints here]

## System architecture
- Example: Monorepo with /webapp (Next.js) and /api (FastAPI).
- Example: Frontend calls backend APIs only; no direct DB/storage access.
- [insert module map here]
- [insert service boundaries here]

## API boundaries
- Example: All APIs versioned under /api/v1 with consistent error schema.
- Example: Request/response models are explicit and typed.
- [insert endpoint groups here]
- [insert error schema and auth headers here]

## Auth model
- Example: Frontend uses NextAuth for session orchestration.
- Example: Backend verifies tokens and enforces authorization.
- [insert provider details here]
- [insert authz rules here]

## Storage model
- Example: Object storage stores media; database stores metadata and references.
- Example: Uploads are controlled with server-issued signed URLs.
- [insert storage paths here]
- [insert file constraints here]

## Observability
- Example: Centralized logs on frontend + backend with request correlation IDs.
- Example: Monitor auth failures and payment/webhook events.
- [insert monitoring tools here]
- [insert alerting strategy here]

## Testing strategy
- Example: Unit tests for services and utility functions.
- Example: Integration tests for endpoints and E2E smoke for primary flow.
- [insert test commands here]
- [insert CI verification requirements here]
