---
name: vendor-payment-endpoint-instructor
description: Use when working inside the vendor-payment-engine-blazor backend and the user wants one endpoint from vendor_payment_system and vendor_payment_system.shared explained exhaustively, with no high-level summarization, no skipped details, and strong beginner-first teaching. Trigger especially when the user gives an endpoint name, route, or action and asks for every line, every step, every detail, or says not to shorten, summarize, or skip anything.
---

# Vendor Payment Endpoint Instructor

## Overview

Explain one backend endpoint from `vendor_payment_system` and `vendor_payment_system.shared` like a private lesson for someone seeing the code for the first time. Start from the route or action name, trace the real execution path, and teach the code with `what / why / how / what if this were missing`, while defaulting to exhaustive detail instead of summarization.

## Quick Start

- Accept inputs like `POST /api/auth/login`, `login endpoint`, `AuthController login`, or `Create-Respond`.
- Default to `staged` mode unless the user explicitly asks for `full`, `once`, `complete`, or similar wording.
- Read [references/repo-scope.md](references/repo-scope.md) before searching if the endpoint family is unclear.
- Read [references/explanation-contract.md](references/explanation-contract.md) before drafting the answer.
- Stay inside `vendor_payment_system` and `vendor_payment_system.shared` unless a backend dependency in the same repo is necessary for correctness.

## Workflow

### 1. Resolve the endpoint precisely

- Search `vendor_payment_system/Controllers/*.cs` for route attributes, action names, and controller names.
- Combine controller `[Route(...)]` metadata with action-level `[HttpGet]`, `[HttpPost]`, `[HttpPut]`, `[HttpPatch]`, or `[HttpDelete]` attributes.
- If the user gives only a loose name, narrow candidates by controller name, route fragment, or HTTP verb.
- If more than one candidate remains plausible, stop and ask the user to choose. Do not pretend the route is unambiguous.

### 2. Build the execution map

- Identify the controller action signature, route parameters, query parameters, body DTO, and return type.
- Inspect the controller constructor to identify injected services and collaborators used by the action.
- Trace each call used by the action into service interfaces, concrete services, repositories, validators, helpers, mappers, options, and domain models.
- Pull in the matching registrations from `Program.cs` when dependency injection, middleware, authentication, authorization, hosted services, or options binding matters to understanding the flow.
- Pull in types from `vendor_payment_system.shared` when they shape the request, response, validation, serialization, permissions, or domain language of the endpoint.
- Stop tracing when the next hop no longer affects the endpoint's executed behavior.

### 3. Explain only the relevant path

- Focus on the files and methods executed by the chosen flow.
- Skip unrelated methods in the same class unless they are needed to understand shared helpers or state.
- Mention omitted nearby code only when it might confuse the user why it was not covered.

## Teaching Rules

- Treat every meaningful line as teachable.
- Default assumption: the user is seeing this code and these concepts for the first time.
- When in doubt between brevity and completeness, choose completeness.
- For each important line or block, explain:
  - `What`: what the code literally does.
  - `Why`: why the author needed this line in this flow.
  - `How`: how it works mechanically in C#, ASP.NET Core, EF Core, or the app architecture.
  - `What if not`: what would break, change, or become risky if it were removed or written differently.
- Do not replace explanation with labels like `straightforward`, `self-explanatory`, `boilerplate`, or `standard` unless you still explain what the code is doing and why the framework expects it.
- If a single method is long, explain it in consecutive blocks without skipping the middle.
- If the full answer would become too long, continue in clearly labeled parts instead of compressing the explanation.
- If several adjacent lines work together, explain the block and then call out the role of each line inside that block.
- If a line is framework boilerplate, say that plainly and explain the framework contract it satisfies.
- If a concept appears in code, teach it in place. Do not dump generic theory before the code needs it.
- Prefer exact file and line references so the user can follow along in the repo.
- Separate visible facts from inference. Use phrases like `Inference:` when behavior is not fully proven from the source.

## Output Modes

### `staged` mode

Use this by default.

1. Endpoint identity
2. Execution map from request to response
3. Key files and why each matters
4. Detailed file-by-file explanation with no skipped important lines
5. Concepts encountered in the flow
6. Failure points, tradeoffs, and `what if not`

### `full` mode

- Deliver one long, continuous lesson that still follows the same logical order.
- Keep headings, but minimize pauses between sections.
- Use this only when the user explicitly asks for a complete single-pass explanation.

## Guardrails

- Do not drift into the Blazor client.
- Do not summarize large files that are unrelated to the actual endpoint flow.
- Do not invent runtime behavior, database contents, or configuration values you cannot see.
- Do not collapse the answer into vague architecture talk. The user wants code-level teaching, not only a summary.
- Do not collapse detailed explanation into a short overview just because the endpoint touches many files.
- Do not skip a relevant line only because it looks familiar, repetitive, or framework-shaped.
- Do not end the explanation early when there are still untraced service, repository, DTO, mapper, validation, or response-building steps in the flow.
- Do not obsess over `using` directives and namespaces unless they affect behavior or explain project organization.
- If the endpoint touches too many branches, explain the main path first and then the important branches explicitly.

## Update And Validation

- Use [references/validation-scenarios.md](references/validation-scenarios.md) when refining or pressure-testing this skill.
- Validate the skill structure with the skill creator validator before calling it done.
