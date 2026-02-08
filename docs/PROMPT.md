Please create a web application that... (describe what it does in 1–3 sentences)
Please ensure this is a production-ready MVP, with strict security and verification.

# It should:
- Allow the user to create an account and log in.
- Give the signed-in user a dashboard that displays...
- [insert core capability #1 here]
- [insert core capability #2 here]
- [insert core capability #3 here]

# Pages and content:
* Home page (public)
  * Hero
    * Clear value proposition explaining what the product does
    * Strong CTA that sends user to Sign Up
  * Features
    * Feature 1...
    * Feature 2...
  * Why Choose Us
    * Selling point 1...
    * Selling point 2...
  * CTA
    * "Get Started Today" → links to Login / Sign Up
* About page (public)
* Contact page (public)
* Privacy Policy page (public)
* Terms of Service page (public)
* Login page
* Dashboard page (authenticated)
  * Top Bar: Shows account status and a primary CTA for upgrades (if applicable)
  * Main content: Shows user library and shortcuts to primary actions
  * [insert dashboard layout here]
  * [insert dashboard data shown here]
  * [insert dashboard actions here]
  * Empty, loading, and error states
* Additional pages (if any)
  * ...
  * [insert additional pages here]

# Menus
* Main Menu
  * Home: sends user to the home page
  * Browse
  * Pricing
  * Sign In
  * Create Account
  * [insert other main menu items here]
* Dashboard Menu (authenticated)
  * Dashboard
  * Profile
  * Settings
  * Logout
  * [insert other dashboard menu items here]
* Footer menu
  * Legal: Privacy Policy, Terms of Service
  * Support: Contact, FAQ
  * [insert other footer links here]

# User flows:
Here is the user flow for **Primary Workflow**:
* User lands on the home page
* User clicks CTA and signs in
* User is redirected to the dashboard
* User performs the primary action:
  * user clicks ...
  * frontend sends request ...
  * backend responds ...
  * UI updates ...
* User logs out

Here is the user flow for **Secondary Workflow**:
* User navigates to a secondary page
* User performs an action
* UI shows success and updates state
* [insert secondary flow here]

Here is the user flow for **Guest User Limits** (if applicable):
* Unauthenticated user starts a flow
* User hits a limit
* UI prompts to create an account to continue
* [insert guest limits here]

Here is the user flow for **Payments / Credits / Subscription** (if applicable):
* User opens Pricing
* User selects plan and checks out
* Webhook updates subscription/credits
* UI reflects changes
* [insert billing flow here]

---

# Please use the following technologies:
* Webapp
  * Next.js (App Router)
  * TypeScript
  * Tailwind CSS
  * Radix UI (unstyled components)
  * NextAuth.js (frontend auth orchestration only)
  * TanStack Query (server state)
  * New Relic (monitoring + error tracking)
* Backend
  * Python
  * FastAPI
  * Supabase Auth (token verification only on backend)
  * Supabase Database
  * Supabase monitoring and error tracking
  * Backblaze B2 Storage (for images/videos)
  * Stripe (payments)
  * Ollama (text generation) [insert model here]
  * ComfyUI (image generation) [insert model/pipeline here]
  * [insert any additional services here]

# Design references:
* Use design/homepage_mockup.html if present
* Use design/homepage_mockup.png if present
* If missing, create a clean, modern layout that matches the home page sections above

# Project goals:
* Production-ready MVP suitable for real users.
* All business logic lives in the backend.
* Frontend is a thin client that renders UI and calls backend APIs.

# Output requirements (IMPORTANT):
* Before writing any code, output in this exact order:
  1. Assumptions and blocking questions (only if required)
  2. Repository tree
  3. Data model (tables/collections + indexes)
  4. API contract (endpoints + request/response models)
  5. Implementation plan (checklist)
  6. Code
  7. Tests
  8. Documentation

# Rules and constraints:
* Always use DRY, fail-fast principles, and security best practices.
* NEVER make architectural or functionality changes without asking.
* NEVER create temporary fixes or workarounds. All solutions must be production-ready.
* Do not create dummy or seed data.
  * If data is required to display the UI, ask me to create it and provide exact instructions or API calls.
* If API keys, OAuth credentials, environment variables, or provider configuration are required, ask before proceeding.
* Keep secrets out of source control. Provide `.env.example` files only.
* Add all secrets, base paths for API calls, etc. to a .env file in the root of each app.

# Repository structure (monorepo):
* /webapp
* /api
* /shared
* /docs

# Testing:
* Frontend tests go in `/webapp/test`
* Backend tests go in `/api/test`

# Frontend rules:
* Use TypeScript everywhere.
* Use Next.js App Router.
* Default to Server Components.
* Only use Client Components when required (forms, interactivity, auth state).
* All data fetching must go through the backend API.
* No direct access to anything other than the backend API.
* Use unstyled Radix UI components only.
* Tailwind is responsible for all styling.
* Use a single layout template that includes:
  * Header
  * Footer
  * Navigation
  * Toasts/alerts
  * Error boundary
* Pages that do not need certain layout elements must disable them via props or configuration.
* For each responsibility, use a single service:
  * API client service
  * Auth service
  * Logging service

# Backend rules:
* Use Python + FastAPI with a strict modular structure.
* API structure for each route:
  * router.py      (routes only)
  * service.py     (business logic)
  * models.py      (Pydantic request/response models)
  * constants.py   (error messages and constants)
* Shared logic goes in `/api/core`:
  * authentication
  * database client
  * storage client
  * logging
  * configuration
  * error handling
* If shared logic requires multiple files, use a folder with:
  * service.py
  * models.py
  * constants.py
* Always check `/core` before writing new logic.

# Authentication and authorization:
* Frontend authenticates user via NextAuth.js.
* Frontend sends provider ID token with every API request:
  * `Authorization: Bearer <token>`
* Backend verifies tokens and derives user identity from token claims.
* Backend enforces all authorization rules.
* Frontend must handle:
  * 401 → force logout
  * 403 → show permission error

# API standards:
* Version all endpoints under `/api/v1`
* Use a consistent error schema:
  * `{ error: { code, message, details } }`
* Backend validates and sanitizes all inputs.
* Rate-limit sensitive endpoints (auth, uploads, destructive actions).

# Storage rules:
* Enforce file size and type restrictions.
* Use signed URLs or controlled upload flows, if applicable.

# Storage layout (if using object storage):
* /images
  * /<entity-type>/<entity-id>/<file>.png
* /videos
  * /<entity-type>/<entity-id>/<file>.mp4
* [insert any special storage hierarchy here]

# Build and deliverables:
* Provide:
  * Full monorepo code
  * `/docs/SETUP.md` (local setup instructions)
  * `/docs/API.md` (all endpoints documented)
  * `/docs/ARCHITECTURE.md` (design decisions)
* Ensure the project runs locally:
  * Frontend via Next.js dev server
  * Backend via uvicorn
* Provide scripts:
  * lint
  * test
  * run
* Include CI-ready commands.
* Provide linting setup with best practices, and adhere to them.

# Edge cases and error handling:
* Loading, empty, and error states for all pages
* Token expiration and automatic re-auth
* Permission errors with actionable messages
* Centralized backend and frontend logging

# Performance requirements:
* Avoid unnecessary re-renders.
* Paginate large datasets.
* Optimize API calls and caching.
* Keep bundle size reasonable.

# Security requirements:
* Never trust the client.
* Backend is the source of truth.
* Log and monitor authentication and authorization failures.
* [insert any special compliance or policy constraints here]

---

# Optional: Seed data (only if explicitly allowed)
For seed data, please do the following:
- Generate the list of metadata objects (slug + description) required for the UI.
- Provide a script that can generate or import assets into storage in a deterministic folder structure.
- [insert seed/data rules here]

Please implement the complete project with the above constraints.
