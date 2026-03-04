# PROJECT.md (Project Definition)

Please create a web application that... (describe what it does in 1–3 sentences)
Please ensure this is a production-ready MVP, with strict security and verification.

## It should
- Allow the user to create an account and log in.
- Give the signed-in user a dashboard that displays...
- [insert core capability #1 here]
- [insert core capability #2 here]
- [insert core capability #3 here]

## Pages and content
- Home page (public)
  - Hero
    - Clear value proposition explaining what the product does
    - Strong CTA that sends user to Sign Up
  - Features
    - Feature 1...
    - Feature 2...
  - Why Choose Us
    - Selling point 1...
    - Selling point 2...
  - CTA
    - "Get Started Today" → links to Login / Sign Up
- About page (public)
- Contact page (public)
- Privacy Policy page (public)
- Terms of Service page (public)
- Login page
- Dashboard page (authenticated)
  - Top Bar: Shows account status and a primary CTA for upgrades (if applicable)
  - Main content: Shows user library and shortcuts to primary actions
  - [insert dashboard layout here]
  - [insert dashboard data shown here]
  - [insert dashboard actions here]
  - Empty, loading, and error states
- Additional pages (if any)
  - [insert additional pages here]

## Menus
- Main Menu
  - Home: sends user to the home page
  - Browse
  - Pricing
  - Sign In
  - Create Account
  - [insert other main menu items here]
- Dashboard Menu (authenticated)
  - Dashboard
  - Profile
  - Settings
  - Logout
  - [insert other dashboard menu items here]
- Footer menu
  - Legal: Privacy Policy, Terms of Service
  - Support: Contact, FAQ
  - [insert other footer links here]

## User flows
### Primary Workflow
- User lands on the home page
- User clicks CTA and signs in
- User is redirected to the dashboard
- User performs the primary action:
  - user clicks ...
  - frontend sends request ...
  - backend responds ...
  - UI updates ...
- User logs out

### Secondary Workflow
- User navigates to a secondary page
- User performs an action
- UI shows success and updates state
- [insert secondary flow here]

### Guest User Limits (if applicable)
- Unauthenticated user starts a flow
- User hits a limit
- UI prompts to create an account to continue
- [insert guest limits here]

### Payments / Credits / Subscription (if applicable)
- User opens Pricing
- User selects plan and checks out
- Webhook updates subscription/credits
- UI reflects changes
- [insert billing flow here]
