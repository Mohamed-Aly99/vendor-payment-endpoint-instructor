# Validation Scenarios

Use these prompts to sanity-check the skill after edits.

## Scenario 1: Exact route

Prompt:

`Use $vendor-payment-endpoint-instructor to explain POST /api/auth/login in staged mode.`

Expected behavior:

- Resolve `AuthController`
- Explain the login action from route to response
- Pull request and response types from backend and shared code
- Reference DI and auth concepts when they appear

## Scenario 2: Loose endpoint name

Prompt:

`Use $vendor-payment-endpoint-instructor to explain the Create-Respond endpoint.`

Expected behavior:

- Search controller actions by name or route fragment
- Match `RespondToQueryController` if evidence fits
- Say why this is the chosen match

## Scenario 3: Ambiguous input

Prompt:

`Use $vendor-payment-endpoint-instructor to explain the filter endpoint.`

Expected behavior:

- Detect ambiguity because many controllers expose `filter`
- Ask for clarification instead of guessing

## Scenario 4: Full mode

Prompt:

`Use $vendor-payment-endpoint-instructor to explain POST /api/users in full mode.`

Expected behavior:

- Produce one long, connected walkthrough
- Keep file references and concept explanations intact

## Scenario 5: Boundary enforcement

Prompt:

`Use $vendor-payment-endpoint-instructor to explain the frontend page that calls login.`

Expected behavior:

- Refuse the client-side deep dive
- Restate that this skill is backend-only
- Offer to explain the backend endpoint instead

## Scenario 6: Anti-summarization pressure

Prompt:

`Use $vendor-payment-endpoint-instructor to explain POST /api/auth/login. Do not summarize. Explain every relevant line and every small detail like I am seeing the code for the first time.`

Expected behavior:

- Stay exhaustive instead of switching to a short overview
- Explain the route match, DTO binding, controller logic, service path, and response path in detail
- Avoid phrases that hand-wave missing detail such as `obvious`, `straightforward`, or `the rest is similar`
