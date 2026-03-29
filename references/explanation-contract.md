# Explanation Contract

Use this file to shape the final explanation.

## Exhaustiveness principle

- Assume the user is new to the code.
- Prefer over-explaining to under-explaining.
- Do not switch to high-level summarization unless the user explicitly asks for a summary.
- If the answer becomes large, split it into sequential parts and continue. Do not compress the middle.
- Do not say `the rest is similar` unless the remaining code is truly repetitive and you first proved the pattern on actual lines.

## Default structure

### 1. Endpoint identity

- State the matched controller, action, HTTP verb, and full route.
- State why this match is the correct one.

### 2. Execution map

- Give a short request-to-response map.
- Mention DTOs, services, repositories, and response types in order.

### 3. File list

- List the exact files that matter for this flow.
- Give one sentence for why each file is part of the endpoint.

### 4. Deep explanation

For each file or method:

- Quote or paraphrase the local code intent.
- Explain line by line or block by block in code order.
- Do not skip the request DTO binding, service call, repository call, mapping, validation, or response construction if they are part of the real flow.
- Use this lens:
  - `What`
  - `Why`
  - `How`
  - `What if not`

### 5. Concept callouts

When a concept appears in code, explain it immediately:

- `Dependency injection`
- `DTOs`
- `ActionResult` and HTTP responses
- `Authorization` and permissions
- `Async/await`
- `LINQ`
- `Entity Framework Core`
- `Repository pattern`
- `Options/config binding`
- `Mapping and transformation`
- `Validation`

Tie each concept back to the exact line or block that triggered it.

### 6. Risk and failure points

- Point out fragile assumptions, null risks, auth risks, validation gaps, or data consistency risks visible in the flow.
- Mark uncertainty clearly as inference.

## Mode rules

### `staged`

- Keep each section separate.
- Start with the map before the deep dive.
- Use this mode unless the user explicitly asks for a single uninterrupted explanation.
- Even in staged mode, the deep dive must stay exhaustive.

### `full`

- Merge the same material into one continuous lesson.
- Keep headings lightweight so the answer still reads like a guided walkthrough.
- Do not trade away detail for narrative smoothness.

## Tone rules

- Teach like a patient senior backend engineer, not a lecturer.
- Avoid vague praise and avoid filler.
- Prefer precise explanations over motivational talk.
- If a line is simple, explain it simply instead of inflating it.
- Never hide missing detail behind phrases like `obvious`, `basic`, `just`, or `simply` unless the actual mechanism is still explained.
