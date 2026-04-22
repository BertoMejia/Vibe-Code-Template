# webapp.md

Load this file only when the project includes a web application.

## Technology stack
- Next.js (App Router)
- TypeScript
- Tailwind CSS
- Radix UI (unstyled components)
- NextAuth.js (frontend auth orchestration only)
- TanStack Query (server state)
- New Relic (monitoring + error tracking)

## Design references
- Use `docs/design/homepage_mockup.html` if present
- Use `docs/design/homepage_mockup.png` if present
- If missing, create a clean, modern layout matching `docs/PROJECT.md` sections

## Webapp goals
- Production-ready MVP suitable for real users
- Thin client that renders UI and calls backend APIs
- All business logic stays in the backend API

## Webapp rules
- Use TypeScript everywhere
- Use Next.js App Router
- Default to Server Components
- Use Client Components only when required (forms, interactivity, auth state)
- Keep pages, route segments, and components in clearly owned files
- Put reusable UI components in `components/`
- Put constants in `constants/`
- Put helpers and utility functions in `helpers/`
- Put hooks in `hooks/`
- Put service integrations in `services/`
- Keep reusable UI components separated from page-specific compositions
- Keep frontend orchestration in services/hooks, not inside presentational components
- All data fetching goes through the backend API
- No direct access to anything other than the backend API unless explicitly approved
- Use unstyled Radix UI components only
- Tailwind handles all styling
- Use one layout system with Header, Footer, Navigation, Toasts or alerts, and an Error Boundary
- Pages can disable specific layout elements via config or props
- Use one service per responsibility: API client, Auth, Logging
- Keep form state, validation display, and submission flows explicit
- Prefer server-side rendering or streaming when it improves UX and fits the page needs
- Use route-level loading and error boundaries where appropriate
- Handle loading, empty, and error states for all pages
- Handle token expiration and automatic re-auth UX
- Handle permission errors with actionable messages
- Keep accessibility first-class: semantic markup, keyboard navigation, focus states, labels, and contrast
- Keep design and interaction patterns consistent across pages and features
- Avoid duplicating client state that can be derived from server state or props
- Avoid unnecessary re-renders
- Optimize API calls and caching
- Debounce or throttle expensive client interactions when appropriate
- Sanitize and validate any user-controlled data at the UI boundary before submission where useful for UX
- Keep bundle size reasonable
- Lazy-load heavy client-only features when possible
- Do not place business rules in components or client-only utilities when the API should own them

## Code style
- Follow standard TypeScript/JavaScript naming conventions; match the project's ESLint configuration.
- Document public classes, methods, and utility functions with JSDoc.
- Avoid excessive primitive types; encapsulate related data in composite types.

## Testing
- Frontend tests in `/webapp/test`.
- Each unit test covers a single function; mock all other dependencies.
- E2E tests are limited and cover only primary user flows.

## Deliverables
- Frontend implementation in `/webapp`
- Lint, typecheck, test, and run scripts
- CI-ready frontend commands
