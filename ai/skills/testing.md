# Testing Policy

## Default expectations

- Add tests for core logic and critical flows.
- Please use test driven development.
- Every task should have Unit tests and integration tests to make sure the task is working properly.
- For UI flows, maintain a Playwright smoke suite.

## E2E smoke (minimum)

- App loads
- Login (if applicable)
- One core flow from fetishful_prompt.md
- Logout (if applicable)

## Playwright rules

- Use data-testid selectors
- No sleeps; use expect + auto-waits
- Capture trace/screenshot on failure

## Unit tests

- Please add unit tests for all core logic
- Please add unit tests for all critical flows
- Each test should test a single function at a time and mock all dependencies
- Each test will test different paths for the function
- Unit tests should be in the test folder using the same file structure as the source code
- Each path inside of a test should follow this structure:
  - input: the input to the function
  - expected: the expected output of the function
  - mocks: the mocks for the dependencies of the function with the expected output
  - test logic: the test logic for the function
  - Expect statement

## Integration tests

- Integration tests should be created as you create each endpoint.
- Please add integration tests for every path or endpoint
- Integration tests should be in an "integration" folder, using the same path as the endpoint.
- Integration tests should test the entire flow of the endpointwith nothing mocked.
- External dependencies like DBs, and APIs should be mocked using ephemeral or mock external dependencies.
- Each test should follow this structure:
  - input: the input to the function
  - expected: the expected output of the function
  - Launch mock external dependencies with expected responses
  - test logic: the test logic for the function
  - Expect statement
- Logic to launch external mocks should:
  - Be in a separate folder called "mocks"
  - Receive a list of of expected paths and responses as a parameter
  - Launch a server that responds with the expected response for each path
