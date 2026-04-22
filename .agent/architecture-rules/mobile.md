# mobile.md

Load this file only when the project includes a mobile application.

## Technology stack
- React Native
- TypeScript
- Expo or React Native CLI, chosen based on project requirements
- React Navigation
- TanStack Query
- Native secure storage for tokens or session data
- Sentry or equivalent mobile error tracking when required

## Mobile app goals
- Mobile client should be a thin client that consumes the backend API
- Share product behavior and contracts with the webapp where practical
- Keep platform-specific code isolated and explicit

## Mobile app rules
- Use React Native with TypeScript
- Organize app code under `mobile/src`
- Keep screens in `mobile/src/screens`
- Keep reusable UI components in `mobile/src/components`
- Keep API/auth/logging integrations in `mobile/src/services`
- Keep navigation in `mobile/src/navigation`
- Keep screen containers separate from reusable presentational components
- Keep platform-specific code isolated behind explicit files or adapters
- All data fetching goes through the backend API
- No mobile-only business logic that conflicts with backend behavior
- Handle loading, offline, empty, and error states clearly
- Handle token expiration, forced logout, and permission failures consistently
- Keep secure data in platform-appropriate secure storage only
- Design for variable network quality, slower devices, and interrupted app sessions
- Keep navigation flows explicit and predictable
- Respect platform conventions for gestures, back behavior, permissions, and deep links
- Prefer shared contracts from `shared/` when both web and mobile use the same domain models
- Keep native modules to the minimum required for project goals
- Minimize unnecessary re-renders and expensive bridge/native operations
- Optimize list rendering, image loading, and app startup time on critical flows
- Keep accessibility support in place for labels, focus order, touch targets, and screen readers

## Code style
- Follow standard TypeScript/JavaScript naming conventions; match the project's ESLint configuration.
- Document public classes, methods, and utility functions with JSDoc.
- Avoid excessive primitive types; encapsulate related data in composite types.

## Testing
- Mobile tests in `/mobile/test`.
- Each unit test covers a single function; mock all other dependencies.
- E2E tests are limited and cover only primary user flows.

## Deliverables
- Mobile implementation in `/mobile`
- Lint, test, and run scripts for the mobile app
- Clear local run instructions for iOS and Android flows when applicable
