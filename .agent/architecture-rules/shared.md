# shared.md

Default architecture principles that apply across the repository unless project-specific documents explicitly require a different approach.

## Shared goals
- Keep the system simple, explicit, and maintainable
- Reduce duplication without creating hidden coupling
- Fail fast when assumptions are violated
- Keep responsibilities separated by file, folder, and service boundary

## Shared rules
- Follow DRY: extract repeated logic only when it represents true shared behavior
- Fail fast: validate inputs, surface errors early, and avoid silent fallbacks
- Keep logic in the correct layer and folder for its responsibility
- Keep each component, module, and service in its own file unless there is a clear reason not to
- Prefer small, focused files over large multi-purpose files
- Use explicit interfaces, contracts, and data shapes between layers and services
- Do not mix UI concerns, business logic, and infrastructure concerns in the same module
- Keep service boundaries clear: each service owns its own runtime logic and infrastructure concerns
- Share only truly cross-service contracts, schemas, types, constants, and pure utilities
- Avoid hidden coupling through implicit behavior, global state, or cross-service reach-through
- Keep naming consistent, predictable, and aligned with the folder structure
- Organize code so a reader can quickly find where a feature, component, or service lives

## Structural expectations
- Keep each file and folder focused on a clear responsibility
- Group related logic in a way that improves ownership and discoverability
- Split large files when they start carrying multiple responsibilities
- Add new folders only when they improve clarity, not as placeholders

## Change expectations
- When architecture changes, update the corresponding project docs in the same patch
- When shared contracts change, update every impacted consumer deliberately
- Prefer reversible, localized changes over sweeping rewrites unless the task requires broader refactoring
- Keep rules in this file service-agnostic; put service-specific rules in the corresponding rule file
