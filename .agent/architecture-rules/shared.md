# shared.md

Load this file only when multiple services need shared contracts, schemas, utilities, or domain types.

## Shared goals
- Reduce duplication without creating hidden coupling
- Keep shared code stable, explicit, and framework-light
- Share contracts, not service-specific behavior

## Shared rules
- Put shared code in `/shared`
- Prefer shared types, schemas, DTOs, validation helpers, and pure utilities
- Do not put UI-specific code in `shared/`
- Do not put backend-only infrastructure concerns in `shared/`
- Keep shared modules framework-agnostic where possible
- Changes to shared contracts must trigger updates in every consumer service
- Version shared contracts carefully when breaking changes are unavoidable

## Typical ownership
- Shared request/response contracts
- Shared domain schemas
- Shared constants used across services
- Shared pure utilities

## Deliverables
- Shared code only when the project benefits from it
- Clear consumer ownership noted in `docs/ARCHITECTURE_INDEX.md`
