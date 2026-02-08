# Code Generation Patterns

## Always prefer

- small PR-sized commits
- typed boundaries (DTOs, schemas)
- consistent folder structure per repo rules
- no magic strings for routes/permissions

## UI implementation rule

- Match design/homepage_mockup first
- Use design/branding_guidelines.html for styles and component design.
- Only expand design when the design elements are missing in the design/branding_guidelines.html

## Architecture

- Before writing any code, please review the architecture.md file to find all relevant services, models, routes, controllers, and tests, and make sure that the code is consistent with the architecture.
- After writing any code, please update the architecture.md file as necessary to keep it up to date.
- If the architecture.md file is missing, please create one that describes:
  - The architecture of the application
  - Location and brief explanation of each service
  - The organization and where to find the data models, routes, controllers, etc.
  - The organization and where to find the tests
