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
- All data fetching goes through the backend API
- No direct access to anything other than the backend API unless explicitly approved
- Use unstyled Radix UI components only
- Tailwind handles all styling
- Use one layout system with Header, Footer, Navigation, Toasts or alerts, and an Error Boundary
- Pages can disable specific layout elements via config or props
- Use one service per responsibility: API client, Auth, Logging
- Handle loading, empty, and error states for all pages
- Handle token expiration and automatic re-auth UX
- Handle permission errors with actionable messages
- Avoid unnecessary re-renders
- Optimize API calls and caching
- Keep bundle size reasonable

## Testing locations
- Frontend tests in `/webapp/test`

## Deliverables
- Frontend implementation in `/webapp`
- Lint, typecheck, test, and run scripts
- CI-ready frontend commands
